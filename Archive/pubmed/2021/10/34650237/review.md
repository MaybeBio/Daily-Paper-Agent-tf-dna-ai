## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, methods, and figure legends where available
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and presentation quality; not copyediting or formatting
- **Shared manuscript claim summary** The authors present a multiomic profiling of chromatin and expression dynamics during epidermal differentiation, identify 40,103 dynamic cis-regulatory elements (CREs) associated with 3,609 dynamically expressed genes, and apply an interpretable deep-learning framework to model the cis-regulatory logic of chromatin accessibility. They identify cooperative DNA sequence rules in dynamic CREs, validate temporal dynamics and cooperative logic using massively parallel reporter assays (MPRAs), and show enrichment of human skin disease-associated variants in these combinatorial motif rules.
- **Visible evidence base** Abstract, full results section with figure references, discussion, methods summary, data availability statement
- **Missing materials affecting confidence** Full figure panels and supplementary figures not visible; detailed methods for deep learning architecture, MPRA library design, and statistical tests only partially described; no access to supplementary tables or extended data figures

## Reviewer
- **Overall assessment** This manuscript presents a substantial and ambitious integration of multiomic profiling, deep learning, and experimental validation to decipher the combinatorial cis-regulatory code underlying epidermal differentiation. The work is technically sophisticated and the combination of computational prediction with MPRA validation is commendable. However, several concerns regarding the interpretability of the deep learning model, the specificity of the validation, and the strength of the disease association claims need to be addressed before the case is fully established.
- **Who would be interested in the results, and why** Researchers in gene regulation, chromatin biology, skin biology, and computational biology would find this work of high interest. The framework for interpreting combinatorial cis-regulatory logic is generalizable beyond epidermal differentiation and could inform studies of other differentiation systems and disease-associated noncoding variation.
- **Major strengths** 1) The dense longitudinal multiomic dataset spanning 13 timepoints is a valuable resource. 2) The transfer learning approach leveraging 431 cell types improves model performance and stability. 3) The interpretability framework goes beyond motif discovery to infer quantitative combinatorial rules. 4) The MPRA validation of predicted temporal dynamics and cooperative interactions is a strong experimental confirmation. 5) The integration with disease-associated variation provides translational relevance.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of model interpretation
  - **Claim pointer** The authors claim that the model-derived contribution scores identify "predictive motif instances" that reflect functional TF binding sites, and that these are "critical to obtain improved estimators of the cis-regulatory activity of TFs."
  - **Evidence pointer** Results section "Model interpretation shows combinatorial regulatory logic", Figure 3c-h, Extended Data Figure 3e-h
  - **Concern** The contribution scores are derived from a gradient-based attribution method applied to a deep learning model. The authors state they "developed methods to stabilize and normalize the scores" and "developed stringent null models to identify statistically significant contribution scores," but the details of these methods are only in Supplementary Methods, which is not visible. The validation of contribution scores against ChIP-seq data (Figure 3g) shows higher occupancy at predictive motif instances, but the effect sizes and statistical significance of these comparisons are not reported in the visible text. Furthermore, the comparison to "inactive motif instances with low contribution scores" is potentially circular if the threshold for "active" is derived from the same model.
  - **Why it matters** The entire downstream analysis of combinatorial motif logic, including the identification of cooperative interactions and the disease association analysis, depends on the reliability of these contribution scores. If the attribution method is unstable or biased, all subsequent conclusions could be compromised.
  - **Resolution test** Provide full details of the contribution score stabilization and null model procedures in the main text or clearly reference specific supplementary sections. Report effect sizes and confidence intervals for the ChIP-seq enrichment comparisons. Demonstrate that the contribution scores are robust across different random seeds and model initializations. Show that the predictive motif instances identified by the model are not simply recapitulating sequence conservation or motif strength alone.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Validity of MPRA validation
  - **Claim pointer** The authors claim that MPRA experiments "validated temporal dynamics and cis-regulatory logic involving cooperative TF interactions" and that 55 of 80 heterotypic motif pairs (68%) were validated for temporal dynamics.
  - **Evidence pointer** Results section "Regulatory activity in the combinatorial motif lexicon", Figure 5, Extended Data Figure 8
  - **Concern** The MPRA design uses 19 randomly selected genomic sequences per motif pair. The criteria for "temporal validation" require concordance between MPRA reporter activity and chromatin accessibility dynamics, but the correlation values and statistical thresholds are not reported in the visible text. The comparison between MPRA activity and ATAC-seq signal shows low absolute correlation (Pearson ρ = 0.097 for observed, 0.088 for predicted), which the authors attribute to "fundamental differences between the MPRA-derived intrinsic measures of regulatory potential and endogenous chromatin state." However, this low correlation raises questions about whether the MPRA is truly measuring the same regulatory logic as the chromatin accessibility model. The use of a linear model with the final layer of the CNN to fit MPRA data (ρ = 0.344) suggests that a transformation is needed, but the nature of this transformation and its biological interpretation are unclear.
  - **Why it matters** The MPRA validation is the key experimental evidence supporting the computational predictions. If the validation criteria are lenient or the correlation between MPRA and chromatin state is weak, the claim that the combinatorial motif lexicon is "validated" is overstated.
  - **Resolution test** Report the full distribution of correlation values for the 55 validated pairs, including confidence intervals. Provide the specific statistical tests and thresholds used to define "concordant effect." Discuss the biological interpretation of the low absolute correlation between MPRA and chromatin state and justify why the relative dynamics, rather than absolute levels, are the appropriate comparison. Show that the MPRA results are reproducible across biological replicates.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Strength of disease association claims
  - **Claim pointer** The authors state that "variants linked to human polygenic skin disease were enriched in these time-dependent combinatorial motif rules" and that this "indicates that disruption of cooperative TF interactions that regulate epidermal differentiation may mediate disease risk."
  - **Evidence pointer** Results section "Disease-associated genetic variation in the motif lexicon", Extended Data Figure 10
  - **Concern** The disease association analysis uses LD score regression with curated UK Biobank phenotypes. The specific phenotypes included, the number of variants analyzed, and the effect sizes and significance thresholds are not reported in the visible text. The claim that specific motif pairs are enriched for disease heritability (e.g., late-stage differentiation rules for acne) is based on correlations that could be confounded by linkage disequilibrium structure, gene density, or other genomic features. The authors do not appear to have performed conditional analyses to test whether the enrichment is independent of other known annotations.
  - **Why it matters** The disease association analysis is presented as a key translational implication of the work. Overstated claims could mislead the field about the clinical relevance of specific motif combinations.
  - **Resolution test** Provide a full description of the phenotypes, variant sets, and LD score regression parameters. Report effect sizes, standard errors, and p-values for all enrichments. Perform conditional analyses controlling for baseline annotations, chromatin state, and other regulatory features. Discuss potential confounding factors and limitations of the analysis.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Figure 1b
  - **Evidence pointer** Results section "Multimodal regulatory dynamics in epidermal differentiation"
  - **Issue** The text references "Fig. 1b" for the experimental design but does not describe what is shown in the figure. The sampling scheme (13 timepoints over 6 days) is described in the Methods but the figure legend is not visible.
  - **Required correction** Ensure the figure legend clearly describes the experimental timeline, including the timepoints sampled and the assays performed at each timepoint.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Clustering analyses
  - **Evidence pointer** Results section "Multimodal regulatory dynamics in epidermal differentiation", Figure 2b-c
  - **Issue** The number of clusters (15 for CREs, 11 for transcripts) is stated but the clustering method parameters and the criteria for choosing the number of clusters are not described in the visible text.
  - **Required correction** Provide details on the clustering algorithm parameters and the model selection criteria, or reference the specific supplementary methods section.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation of repressive motifs
  - **Affected element** Extended Data Figure 4
  - **Evidence pointer** Results section "Deep learning shows a dynamic DNA motif lexicon"
  - **Issue** The authors identify CEBPA and KLF4 as having both activating and repressing roles, but the criteria for classifying a motif as "repressive" based on negative contribution scores are not clearly defined.
  - **Required correction** Define the threshold for negative contribution scores that constitutes a repressive effect and discuss how this relates to known mechanisms of transcriptional repression.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Generalizability
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section
  - **Issue** The authors state the framework is "generalizable" but do not discuss potential limitations when applying it to other differentiation systems with different chromatin dynamics or TF repertoires.
  - **Required correction** Add a brief discussion of the assumptions and potential limitations of the framework when applied to other biological contexts.

## Technical failings that need to be addressed before the case is established
- R1-M1: The interpretability of the deep learning model contribution scores requires full methodological transparency and robustness testing.
- R1-M2: The MPRA validation criteria and the relationship between MPRA activity and chromatin state need to be more rigorously established.
- R1-M3: The disease association analysis requires more detailed reporting and conditional analyses to support the claims.

## Risk / unsupported claims
- The claim that the model identifies "cooperative DNA sequence rules" that are "validated" by MPRA is partially supported but requires stronger statistical evidence.
- The claim that disease-associated variants are enriched in specific combinatorial motif rules is suggestive but not fully established from the visible evidence.
- The claim that the framework "represents a general approach for deciphering the organizational principles of the cis-regulatory code" is reasonable but not directly demonstrated beyond the epidermal differentiation context.
- The statement that "the intrinsic regulatory potential and chromatin state of CRE sequences are both determined by the same underlying cis-regulatory motif syntax" is a strong claim that requires more direct evidence than the correlative analyses presented.

## Assessment against Nature-style criteria
- **Originality** High. The integration of dense multiomic profiling with interpretable deep learning to derive combinatorial cis-regulatory rules is novel. The focus on dynamic, time-resolved regulatory logic rather than static motif enrichment distinguishes this work from prior studies.
- **Scientific importance** High. Understanding how combinations of TF motifs encode dynamic regulatory activity is a fundamental question in gene regulation. The resource and framework presented here could have broad impact on studies of differentiation and development.
- **Interdisciplinary readership** Moderate to high. The work bridges genomics, computational biology, and skin biology. The deep learning interpretability framework may appeal to computational biologists, while the skin disease associations may attract clinical researchers. However, the technical complexity may limit accessibility to a broader biological audience.
- **Technical soundness** Moderate. The multiomic data generation appears rigorous, and the transfer learning approach is well motivated. However, the interpretability of the deep learning model and the validation of combinatorial interactions require more detailed methodological reporting and robustness testing to fully establish technical soundness.
- **Readability for nonspecialists** Moderate. The abstract and introduction are accessible, but the results section is dense and assumes familiarity with deep learning interpretability methods and epigenomic assays. The authors should consider adding more context for nonspecialist readers.

## Recommendation posture
Supportive if technical concerns are resolved. The manuscript presents a valuable resource and a novel analytical framework with strong potential impact. However, the interpretability of the deep learning model, the rigor of the MPRA validation, and the strength of the disease association claims need to be substantially strengthened before the case is fully established. I recommend major revision with the specific concerns above addressed.