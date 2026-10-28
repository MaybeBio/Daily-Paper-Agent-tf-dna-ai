## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) as provided
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and suitability for a high-impact interdisciplinary journal
- **Shared manuscript claim summary** The authors present PTFSpot, a transformer-DenseNet deep co-learning framework that jointly learns from transcription factor (TF) sequences, 3D structures, and their binding regions to predict TF binding regions (TFBRs) across plant species with high accuracy, including for unseen TFs and species, outperforming existing tools by >30% and achieving >90% accuracy in cross-species settings.
- **Visible evidence base** Descriptions of datasets A–F, performance metrics (accuracy, sensitivity, specificity, MCC, F1, AUC), benchmarking comparisons against nine tools, structural analyses (RMSD, binding affinity via docking), and a case study on MYB88–PIN7/zmPIN1c with expression correlation.
- **Missing materials affecting confidence** Actual performance tables and figures (Fig. 4, 6) are referenced but not shown; supplementary tables and figures are not provided; no detailed hyperparameter values, model architecture diagrams, or training curves; no statistical significance tests for most benchmarking comparisons; no details on negative dataset construction for cross-species sets; no code or data availability verification.

## Reviewer
- **Overall assessment** The manuscript addresses a significant and timely problem in plant regulatory genomics: the lack of universal, cross-species TFBR prediction tools. The core idea of co-learning TF structure and binding region covariability is conceptually novel and potentially impactful. However, the evidence presented in the text is insufficient to fully substantiate the strong claims of "impeccable universality" and "revolutionary" performance. Key methodological details are missing, and the benchmarking results are described qualitatively without the actual data being visible in the provided material. The case study is compelling but limited. The work has promise, but the current manuscript does not provide enough verifiable evidence to establish the case.
- **Who would be interested in the results, and why** Plant molecular biologists, regulatory genomics researchers, computational biologists developing deep learning methods for genomics, and researchers studying TF–DNA interactions across species. The potential to annotate TFBRs in non-model plant species without species-specific training data would be of broad interest.
- **Major strengths**
  - Conceptually novel approach: co-learning TF structure and binding region covariability is a fresh idea that addresses a real limitation of existing tools.
  - Addresses a critical gap: cross-species TFBR prediction in plants is underdeveloped, and the motivation is well articulated.
  - Comprehensive benchmarking design: multiple datasets, multiple tools, cross-species validation, and a biological case study.
  - Clear writing and logical structure; the principles behind the method are explained well.
- **Major Concerns**
  - **R1-M1** (Severity: Major, Blocking: Yes, Axis: Evidence sufficiency) The central claim of >30% performance lead and >90% accuracy across unseen species and TFs is not verifiable from the provided material. The referenced figures (Fig. 4, 6) and supplementary tables are not included, so the actual performance data cannot be assessed. The text describes results but does not provide the numbers in a way that allows independent evaluation.
  - **R1-M2** (Severity: Major, Blocking: Yes, Axis: Methodological completeness) The negative dataset construction is described only briefly. For a deep learning method, the choice of negatives is critical. The claim that negatives include "unbound region's motifs and flanking region information" is interesting, but the exact procedure, especially for cross-species datasets, is not detailed. Without this, the validity of the learned discrimination is unclear.
  - **R1-M3** (Severity: Major, Blocking: Yes, Axis: Statistical rigor) No statistical significance tests are reported for the performance differences between PTFSpot and the compared tools. The claim of "outperformed by >30%" needs confidence intervals or significance testing, especially given the variability expected in deep learning models.
  - **R1-M4** (Severity: Major, Blocking: No, Axis: Generalizability of evidence) The cross-species validation uses only six TFs from maize and rice for the comparative benchmarking, and 117 TFs for the full dataset. The claim of "impeccable universality" is based on a limited taxonomic sampling (two monocots). Testing on more diverse plant lineages (e.g., eudicots beyond Arabidopsis, mosses, or algae) would strengthen the claim.
  - **R1-M5** (Severity: Major, Blocking: No, Axis: Biological validation depth) The MYB88–zmPIN1c case study is interesting, but the correlation analysis (r = 0.97) is based on only nine conditions. This is a weak basis for inferring regulation. Experimental validation (e.g., ChIP-qPCR, reporter assays) would be needed to substantiate the biological relevance.
- **Minor Comments**
  - **R1-m1** (Severity: Minor, Axis: Clarity) The term "impeccable universality" in the title is hyperbolic and not supported by the evidence presented. A more measured title would be appropriate.
  - **R1-m2** (Severity: Minor, Axis: Reproducibility) The hyperparameter optimization is mentioned but no details are given (e.g., search space, final values). For reproducibility, these should be provided.
  - **R1-m3** (Severity: Minor, Axis: Completeness) The authors state that "all details on data retrieval are illustrated in Fig. 2," but the figure is not provided. The text should summarize the key data sources and filtering steps.
  - **R1-m4** (Severity: Minor, Axis: Interpretation) The statement that "learning this way even on A. thaliana data alone... would turn to be a boon" is speculative. The manuscript should clarify whether the universal model was trained only on Arabidopsis data or on a mix, and what the implications are.
  - **R1-m5** (Severity: Minor, Axis: Accessibility) The authors mention a webserver and GitHub repository, but no URLs are verified in the provided material. The availability statement should be confirmed.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Provide actual performance data (tables/figures) with confidence intervals.
  - R1-M2: Detail negative dataset construction, especially for cross-species sets.
  - R1-M3: Add statistical tests for all benchmarking comparisons.
  - R1-M4: Expand cross-species validation to more diverse plant lineages.
  - R1-M5: Strengthen biological validation or temper claims.
- **Assessment against Nature-style criteria**
  - Originality: High. The co-learning of TF structure and binding region covariability is a novel contribution.
  - Scientific importance: High. Cross-species TFBR prediction is a major bottleneck in plant genomics.
  - Interdisciplinary readership: Moderate. The work bridges deep learning and plant biology, but the presentation is heavily computational; the biological implications could be more accessible.
  - Technical soundness: Currently not fully assessable. The architecture is plausible, but missing details on data, training, and evaluation prevent a full assessment.
  - Readability for nonspecialists: Moderate. The introduction and principles are clear, but the methods section assumes familiarity with deep learning and genomics terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the problem is important, but the current evidence is insufficient to support the strong claims. The authors should provide the missing data, add statistical rigor, and temper the language to match the evidence.

## Risk / unsupported claims
- The claim of ">30% lead" over existing tools is unsupported without actual performance tables.
- The claim of ">90% accuracy for never-encountered species and TFs" is unsupported without the cross-species results being shown.
- The claim of "impeccable universality" is not established from the provided evidence.
- The claim that PTFSpot "may even bypass the need of costly experiments like DAP-seq" is speculative and not directly tested.
- The biological relevance of the MYB88–zmPIN1c interaction is weakly supported (correlation only, n = 9).