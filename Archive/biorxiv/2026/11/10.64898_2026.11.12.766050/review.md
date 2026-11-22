## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific claims, methodology, and evidence as presented in the supplied text; no external data or supplementary materials were available for verification
- **Shared manuscript claim summary** The authors train a clade-specific genomic foundation model (GPN architecture) on 455 apicomplexan genome assemblies via masked nucleotide reconstruction, and demonstrate that fine-tuning this model improves prediction of regulatory genomic signals (TF binding, chromatin accessibility, histone modifications, chromatin states) in P. falciparum, particularly in low-data settings, compared to models trained from scratch or pretrained on human genomes.
- **Visible evidence base** Main text figures referenced (Figs 1-7), supplemental figures referenced (Supp Figs 1-5), methods text
- **Missing materials affecting confidence** Actual figure panels and numerical results (AUPRC values, error bars, statistical test outputs) are not visible in the provided text; supplementary figures and tables are referenced but not supplied; exact hyperparameter values and model selection details are partially described but not fully specified

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important question in genomic deep learning: whether self-supervised pretraining provides tangible benefits in small, data-sparse genomes. The authors present a well-motivated study design, comparing clade-specific pretraining against from-scratch training and cross-domain pretraining, and they identify a clear regime (low-data tasks) where pretraining helps. The finding that truncated foundation models retain most of the pretraining benefit is practically useful. However, the manuscript as provided has several significant gaps in evidence presentation and methodological rigor that prevent full evaluation of the claims. The central claims are plausible and potentially important, but the current evidence base is insufficient to fully establish them.

- **Who would be interested in the results, and why** Researchers developing or applying foundation models in genomics, particularly those working on non-model organisms or pathogens with limited functional genomics data. The paper also speaks to the broader debate on the practical value of genomic foundation models, which is of interest to the machine learning for genomics community. Additionally, the malaria and apicomplexan research community would benefit from improved regulatory element prediction tools.

- **Major strengths** The study addresses a well-defined, practically important question with a clear experimental design. The comparison across multiple downstream tasks and data regimes is thorough. The inclusion of a phylogenetically matched negative control (shuffled genomes) and a cross-domain pretrained model (DNABERT) strengthens the interpretation. The truncation analysis provides actionable guidance for practitioners. The writing is clear and the motivation is well articulated.

- **Major Concerns** 
  - R1-M1: The central quantitative results are not visible in the provided text. All AUPRC values, effect sizes, and statistical comparisons are described narratively but the actual figure panels are not available. This makes it impossible to assess the magnitude and reliability of the reported improvements.
  - R1-M2: The claim that "most of the benefit" of pretraining is captured by the first eight layers is based on a limited set of six tasks and three seeds. The variability across seeds is reported as standard deviation but the actual values are not visible. The claim of "practical" sufficiency of truncated models needs stronger statistical support.
  - R1-M3: The comparison with DNABERT is potentially confounded by architecture differences (CNN vs transformer) and tokenization differences, in addition to pretraining data differences. The authors acknowledge this indirectly but do not fully address whether the poor DNABERT transfer is due to phylogenetic distance or architectural/tokenization mismatch.
  - R1-M4: The choice of AUPRC as the sole evaluation metric is reasonable for imbalanced binding tasks, but the authors do not report precision-recall curves or calibration metrics. For practical use, calibration of predicted probabilities matters.
  - R1-M5: The manuscript does not report any analysis of what sequence features the model actually learned. The claim that pretraining "front-loads regulatory sequence structure" is inferred from downstream performance but not directly demonstrated through model inspection.

- **Minor Comments**
  - R1-m1: The abstract states "most of the benefit concentrated on datasets with relatively little labeled data (fewer than 3,000 training examples)" but the threshold of 3,000 appears to be derived post hoc from the data. The authors should justify this threshold or present the relationship continuously.
  - R1-m2: The description of the "Whole Genome 455A 2M steps" training data augmentation (random shifting every 200,000 steps) is unusual and not fully justified. The rationale for this schedule should be explained.
  - R1-m3: The methods state that "15% of each 512 bp sequence (~77 bp) was masked at random" for reconstruction. This is a high masking rate; the authors should comment on whether this was optimized or chosen based on prior work.
  - R1-m4: The exclusion of the "quiescent" chromatin state from prediction is mentioned but the rationale is not fully explained. If quiescent is the most common state, excluding it may inflate apparent performance.
  - R1-m5: The manuscript does not report computational cost or training time for the 2-million-step model, which is relevant for practitioners considering this approach.

- **Technical failings that need to be addressed before the case is established** R1-M1 (missing quantitative evidence), R1-M2 (insufficient statistical support for truncation claims), R1-M3 (confounded cross-model comparison)

- **Assessment against Nature-style criteria** 
  - Originality: The work is not conceptually novel (foundation model pretraining is established), but the application to apicomplexan genomes and the systematic evaluation of when pretraining helps in small genomes is a valuable contribution. The truncation analysis adds a practical dimension.
  - Scientific importance: The question of whether pretraining helps in data-sparse settings is important for the field. The answer has implications for how resources are allocated in genomic deep learning. The specific application to malaria is of biomedical relevance.
  - Interdisciplinary readership: The paper bridges machine learning and parasitology. The writing is accessible to both communities, though the ML audience may want more architectural detail and the biology audience may want more biological validation.
  - Technical soundness: The experimental design is sound in principle, but the missing quantitative evidence and potential confounds in the cross-model comparison prevent full assessment.
  - Readability for nonspecialists: The manuscript is well written and the key concepts are explained clearly. The figures, if they match the narrative descriptions, would aid comprehension.

- **Recommendation posture** Supportive if technical concerns are resolved. The core question is important, the study design is appropriate, and the findings are potentially valuable. However, the current evidence base, as presented, is insufficient to fully establish the claims. The authors must provide the actual quantitative results and address the confounds in the cross-model comparison.

## Risk / unsupported claims
- The claim that pretraining provides "most of the benefit" in low-data settings cannot be verified without the actual AUPRC values and statistical comparisons.
- The claim that truncated models (8 layers) are "practically" sufficient is not fully supported by the visible evidence.
- The claim that DNABERT's poor transfer is due to phylogenetic distance is not fully established; architectural and tokenization differences are confounds.
- The claim that reconstruction confidence can serve as "an annotation-free prior for locating candidate regulatory elements" is suggestive but not directly validated (e.g., no experimental validation of novel predictions).
- The claim that "clade-specific pretraining can capture repetitive features and other distinctive sequence composition" in heterochromatic regions is inferred from downstream performance but not directly demonstrated.
- The statement that "the benefit we observe is not a generic property of large pretrained models but depends on the phylogenetic proximity" is only supported by a single cross-domain comparison (DNABERT).