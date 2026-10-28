## Review setup

- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and suitability for a high-impact general audience
- **Shared manuscript claim summary** The authors present TFClassPredict, a DNABERT-based multi-class classification framework that assigns DNA sequences to 23 DBD-classes defined by the TFClass hierarchy. They claim that this approach outperforms PWM-based methods and benchmarked deep learning architectures for TFBS classification, improves downstream applications including PWM-based pipelines and 3D genome interaction prediction, enables genome-wide DBD-class annotation, and recapitulates known lineage-specifying TF programs from immune cell ATAC-seq data.
- **Visible evidence base** Results sections 2.1-2.5, Figures 1-6 (referenced), Supplementary Tables A1-A5, Supplementary Figures A1-A6 (referenced), Methods sections 4.1-4.11
- **Missing materials affecting confidence** Actual figure images and supplementary tables/figures were not provided; exact hyperparameter values for DNABERT fine-tuning beyond k-mer size; details of the HOMER motif-to-DBD-class mapping completeness; code repository contents not reviewed; exact statistical test details for some comparisons

## Reviewer

- **Overall assessment** This manuscript addresses a genuine and important problem in regulatory genomics: the assignment of TFBSs to their cognate transcription factors at the DBD-class level. The authors identify a real limitation of current approaches, namely the binary bound-versus-unbound formulation that ignores competitive binding among TFs sharing DNA-binding domains. The conceptual framing of DBD-class as a biologically meaningful resolution level is well argued and supported by prior literature on DBD-DNA co-evolution. The methodological contribution, particularly the multi-class formulation and the use of high-confidence direct binding data from UniBind, is sound in principle. However, the manuscript as presented has several issues that prevent full confidence in the claims. The comparison against PWM-based methods, while showing improved performance, does not adequately address the inherent advantage of a supervised deep learning model trained on the same data distribution. The genome-wide annotation and downstream application sections are interesting but rely on correlational evidence that is interpreted somewhat strongly. The writing is generally clear but the manuscript would benefit from more precise statistical reporting and a more critical discussion of limitations, particularly regarding the interpretability of what the model actually learns.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on TFBS prediction, regulatory genomics, and cis-regulatory code inference would be the primary audience. Researchers developing deep learning methods for genomics would find the architectural comparison and the multi-class formulation of interest. Experimental biologists studying gene regulation, particularly those using ATAC-seq or ChIP-seq data for regulatory interpretation, would find the genome-wide annotation tracks and the application to immune cell differentiation useful. The work could also appeal to researchers interested in protein-DNA recognition and the evolutionary constraints shaping binding site preferences.

- **Major strengths** The authors identify a genuinely underappreciated problem in TFBS prediction, namely the ambiguity arising from shared DBDs among TFs. The multi-class formulation at the DBD-class level is a sensible and biologically motivated abstraction. The use of UniBind's high-confidence direct binding data is appropriate and addresses a known limitation of training on potentially noisy ChIP-seq peaks. The systematic evaluation against multiple baseline architectures, including both k-mer and one-hot encoded neural networks, provides a useful benchmark. The demonstration that TFClassPredict can serve as a post-hoc filter for PWM-based predictions is practically valuable. The genome-wide annotation and the application to immune cell ATAC-seq data demonstrate potential utility beyond simple classification benchmarks.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that TFClassPredict outperforms PWM-based approaches and benchmarked deep learning architectures is central to the paper's contribution.
- **Evidence pointer** Section 2.2, Figure 3a, 3b, Supplementary Table A2
- **Concern** The comparison against PWM-based methods (HOMER, FIMO) is potentially unfair. The PWM methods are evaluated in a zero-shot manner, using pre-existing motif databases, while TFClassPredict is trained on the same UniBind data used for evaluation. This is not an apples-to-apples comparison. A more appropriate baseline would be a PWM model trained on the same training set, or at least a discussion of this inherent advantage. Additionally, the comparison against other deep learning architectures (DanQ, simple neural networks) is presented but the details of the hyperparameter search for these baselines are not fully described. It is unclear whether these baselines were given the same level of hyperparameter optimization as the DNABERT model.
- **Why it matters** The central claim of superiority over existing methods is the primary justification for the tool's existence. If the comparison is biased, the conclusion is weakened. The reader cannot assess whether the improvement comes from the DBD-class formulation, the transformer architecture, or simply from the advantage of supervised training on the target data.
- **Resolution test** Provide a comparison against PWM models trained on the same training data, or clearly state and justify the zero-shot evaluation protocol. Provide full hyperparameter search details for all baseline models, including the number of configurations tried and the selection criteria. If possible, include a comparison where all models are trained and evaluated under identical data conditions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The claim that TFClassPredict "recapitulates known lineage-specifying TF programs from immune cell ATAC-seq data" is presented as a key biological validation.
- **Evidence pointer** Section 2.5, Figure 6, Supplementary Figure A6, Supplementary Table A5
- **Concern** The analysis of immune cell ATAC-seq data is correlational. The authors compute TFClassPredict binding potentials in differentially accessible regions and compare them across cell types. The observation that known lineage-specifying TFs show enriched binding potentials in the expected cell types is consistent with the model's utility, but it does not constitute a validation of the model's predictions in a strict sense. The analysis does not include any experimental validation, such as ChIP-seq or perturbation data, to confirm that the predicted binding potentials correspond to actual TF occupancy. Furthermore, the statistical framework for comparing binding potentials across cell types is not fully described. The use of t-tests on TFBPD values assumes independence that may not hold for nearby genomic regions.
- **Why it matters** The biological application section is intended to demonstrate real-world utility. If the evidence is only correlational and the statistical framework is not robust, the claim of recapitulating known programs is overstated. The reader cannot distinguish between a model that genuinely captures regulatory biology and one that simply reflects the underlying sequence composition of cell-type-specific open chromatin regions.
- **Resolution test** Provide a more rigorous statistical framework that accounts for spatial correlation between genomic regions. Consider validating a subset of predictions experimentally or against independent ChIP-seq data for the relevant TFs in the relevant cell types. Alternatively, temper the language to clearly state that these are predicted binding potentials that are consistent with known biology, not validated occupancy.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that TFClassPredict "naturally resolves the ambiguity arising from shared DBD architectures" is a strong statement about the model's behavior.
- **Evidence pointer** Section 2.2, Figure 3e, Supplementary Figure A2
- **Concern** The manuscript demonstrates that the model can classify sequences at the DBD-class level with reasonable accuracy, and that misclassifications tend to fall within the same superclass. However, this does not necessarily mean the model has "resolved" the ambiguity in a mechanistic sense. The model may simply be learning a distributed representation that correlates with DBD-class labels without explicitly modeling the shared DBD structure. The analysis of misclassification patterns is interesting but is presented descriptively rather than as a rigorous test of whether the model has learned DBD-specific features. The authors do not provide an analysis of which sequence features or attention patterns the model uses to make its decisions.
- **Why it matters** The claim of "resolving ambiguity" implies a specific mechanistic interpretation of the model's behavior. If the model is simply learning statistical regularities that happen to correlate with DBD-classes, the claim is overstated. Understanding what the model learns is important for assessing its generalizability to new TFs or new DBD-classes.
- **Resolution test** Provide an interpretability analysis, such as attention visualization or feature attribution, to show that the model has learned DBD-relevant sequence features. Alternatively, temper the language to say that the model "effectively handles" the ambiguity at the classification level rather than "resolving" it mechanistically.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The claim that this represents "the first systematic genome-wide annotation of all human ENCODE-defined promoters by DBD-class binding potential" is a strong novelty claim.
- **Evidence pointer** Section 2.4, Figure 5, Supplementary Table A4
- **Concern** The novelty claim is difficult to verify without a more thorough literature review. There are existing resources that annotate regulatory elements by TF family or DBD class, such as the original TFClass resource itself, and various efforts to map TF binding preferences across families. The authors do not discuss how their genome-wide annotation compares to or differs from these existing resources. The claim of "first" requires a more careful and comprehensive comparison to prior work.
- **Why it matters** The novelty of the genome-wide annotation is a key part of the paper's contribution. If similar annotations exist, the claim is weakened. The reader needs to understand what is genuinely new here versus what is an incremental extension of existing resources.
- **Resolution test** Provide a more thorough comparison to existing genome-wide regulatory annotations, particularly those that use TF family or DBD-level classifications. Clearly state what is new about this annotation relative to existing resources.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract is dense and uses field-specific jargon without sufficient context for a general reader. The phrase "cis-regulatory code" and the distinction between "bound-versus-unbound" and "multi-class" classification may not be immediately clear to non-specialists.
- **Required correction** Consider adding one sentence of context explaining why TFBS-to-TF assignment is challenging and why the DBD-class level is a meaningful resolution.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 2.2, Figure 3
- **Evidence pointer** Figure 3a, 3b, Supplementary Table A2
- **Issue** The performance metrics are reported as accuracy and macro F1, but confidence intervals or variance estimates are not provided. It is unclear whether the differences between models are statistically significant.
- **Required correction** Report confidence intervals or perform statistical significance testing for the differences between models.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section 4.5
- **Evidence pointer** Section 4.5, "DNABERT was fine-tuned"
- **Issue** The fine-tuning procedure is described at a high level but lacks specific details on learning rate schedule, batch size, number of epochs (beyond the early stopping criterion), and computational resources used. This limits reproducibility.
- **Required correction** Provide full hyperparameter details in the methods or as a supplementary table.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Data availability section
- **Issue** The statement says data and models are available on Zenodo and code on GitLab, but the specific accession numbers or DOIs are not provided in the manuscript text.
- **Required correction** Include the specific DOIs and repository URLs in the data availability section.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 2.4, Figure 5c
- **Evidence pointer** Figure 5c, Supplementary Figure A4
- **Issue** The t-SNE embedding and clustering of promoters is presented as evidence of functional organization, but the choice of perplexity and clustering algorithm is described as being selected by silhouette score. The robustness of the clustering to these choices is not discussed.
- **Required correction** Briefly discuss the stability of the clustering across different parameter choices, or acknowledge this as a limitation.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion section
- **Evidence pointer** Discussion, limitations paragraph
- **Issue** The limitations section is thoughtful but does not discuss the potential for circularity in the evaluation. The model is trained on UniBind data, which is derived from ChIP-seq experiments, and then evaluated on held-out UniBind data. The relationship between the training data distribution and the intended application domain (e.g., predicting binding in open chromatin regions from ATAC-seq) is not fully explored.
- **Required correction** Add a sentence acknowledging the potential domain shift between ChIP-seq-derived training data and ATAC-seq-derived application data.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1a-c
- **Issue** The graphical abstract is described but not visible in the provided text. The description suggests it is comprehensive, but the reader cannot assess its clarity.
- **Required correction** Ensure the figure is self-explanatory and accessible to a broad audience.

## Risk / unsupported claims

- The claim of "first systematic genome-wide annotation of all human ENCODE-defined promoters by DBD-class binding potential" is not verifiable from the provided text without a more thorough comparison to existing resources.
- The claim that TFClassPredict "naturally resolves the ambiguity arising from shared DBD architectures" implies a mechanistic understanding that is not demonstrated.
- The claim that TFClassPredict "recapitulates known lineage-specifying TF programs" is based on correlational evidence and is stronger than what the analysis supports.
- The performance comparison against PWM methods is potentially biased by the training protocol and should be interpreted with caution.
- The statement that TFClassPredict achieves "robust classification performance, even for underrepresented DBD-classes" is not fully supported by the data presented, as the performance for the most challenging class (2.9) is described as diminished.