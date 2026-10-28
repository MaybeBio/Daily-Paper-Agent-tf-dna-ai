## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text. No supplementary figures or data files were available for direct inspection.
- **Shared manuscript claim summary** The authors use optogenetic control of the yeast transcription factor Msn2 to investigate how promoter decoding of TF nuclear localization dynamics is modulated by changes in TF DNA-binding affinity. They report that promoters exhibit differential sensitivity to Msn2 localization dynamics, that altering Msn2 affinity has promoter-dependent effects on gene expression, and that TF degradation triggered by nuclear localization may act as a timer limiting expression of low-sensitivity genes.
- **Visible evidence base** Main text figures referenced (Figures 1–7), supplementary figures referenced (Figures S1–S14), methods section, and figure legends as described in the text. No raw data, code, or supplementary files were provided for independent verification.
- **Missing materials affecting confidence** Supplementary figures and tables, raw time-lapse imaging data, model parameter distributions, code for image analysis and model fitting, and details of statistical tests. These are essential for full evaluation of the quantitative claims.

## Reviewer
- **Overall assessment** This manuscript addresses an important question in gene regulation: how TF DNA-binding affinity and localization dynamics jointly influence promoter interpretation. The use of an optogenetic system to decouple TF localization from upstream signaling is a strong methodological advance. The results are largely consistent with prior work on Msn2 and extend it by systematically varying affinity. However, several technical and interpretive issues need clarification, particularly regarding model parameterization, the specificity of the affinity mutants, and the generalizability of the conclusions. The manuscript is well written and will interest researchers in gene regulation, systems biology, and optogenetics.
- **Who would be interested in the results, and why** Researchers studying transcription factor dynamics, promoter architecture, and gene expression noise. The optogenetic approach will appeal to those developing tools for dynamic control of gene expression. The findings on promoter-dependent decoding and the potential role of TF degradation as a timer are relevant to understanding stress responses and cell fate decisions.
- **Major strengths** 1) The optogenetic system provides direct, time-varying control of Msn2 nuclear localization without perturbing upstream signaling, a clear improvement over chemical inhibition. 2) The combination of experiments with a three-state promoter model allows quantitative interpretation of promoter decoding behavior. 3) The use of Msn2 affinity mutants is a logical approach to test model predictions. 4) The observation that TF degradation may act as a timer for low-sensitivity genes is novel and interesting.
- **Major Concerns** 1) The model parameterization and identifiability are not fully described, and the use of pooled data across experiments may obscure important variability. 2) The specificity of the Msn2 affinity mutants is not fully validated; off-target effects or changes in protein stability could confound results. 3) The claim that promoter-dependent effects are primarily due to affinity is not fully supported, as other factors (e.g., chromatin state, cofactor recruitment) may vary between promoters. 4) The degradation kinetics are inferred from population-level data, and the proposed timer mechanism is not directly tested. 5) The generalizability of the findings to other TFs and promoters is speculative.
- **Minor Comments** 1) The manuscript would benefit from a clearer description of the model equations and parameter ranges. 2) The statistical analysis of differences between Msn2 mutants could be more rigorous. 3) The discussion of noise and information transmission could be expanded. 4) Some figure references are unclear (e.g., Figure S5C is mentioned but not described in detail).
- **Technical failings that need to be addressed before the case is established** 1) Model identifiability and parameter uncertainty analysis. 2) Validation of Msn2 mutant affinity and specificity. 3) Direct measurement of Msn2 degradation kinetics. 4) Statistical comparison of promoter responses across conditions.
- **Assessment against Nature-style criteria**  
  - *Originality*: High. The combination of optogenetics, affinity mutants, and quantitative modeling is novel.  
  - *Scientific importance*: High. The work addresses fundamental questions about how TF dynamics and affinity are integrated at promoters.  
  - *Interdisciplinary readership*: Moderate. The topic is of interest to molecular biologists, systems biologists, and bioengineers, but may be too specialized for a general audience.  
  - *Technical soundness*: Moderate. The experimental approach is sound, but the modeling and statistical analyses need more rigor.  
  - *Readability for nonspecialists*: Good. The manuscript is clearly written, though some sections assume familiarity with optogenetics and modeling.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are interesting and potentially important, but the current evidence does not fully establish the mechanistic claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the three-state promoter model accurately captures the decoding behavior of Msn2 target genes and that parameter estimates (e.g., K, n, k1, d1) are reliable.
- **Evidence pointer** Methods section, Figure 2D, Figure S6B
- **Concern** The model is fit to pooled data from multiple experiments, but the identifiability of parameters is not assessed. The authors do not report confidence intervals or posterior distributions for parameter estimates, and it is unclear whether the model can distinguish between different parameter combinations. Additionally, the choice of parameter ranges for Latin hypercube sampling is not justified.
- **Why it matters** If the model parameters are not identifiable, the conclusions about promoter sensitivity and the predicted effects of affinity changes may be unreliable. The model is central to the paper's claims, so this is a critical issue.
- **Resolution test** Provide a formal identifiability analysis (e.g., profile likelihood or MCMC sampling) and report parameter uncertainties. Show that the model can be distinguished from simpler alternatives.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the Msn2(A)* and Msn2(T)* mutants have high and low DNA-binding affinity, respectively, and that this is the primary cause of the observed differences in promoter expression.
- **Evidence pointer** Results section, Figure S8A, Figure S6B
- **Concern** The affinity of the Msn2 mutants is not directly measured. The authors rely on previous reports for the mutations, but do not confirm that the mutants behave as expected in their system. Off-target effects, such as changes in protein stability, nuclear import/export rates, or interactions with cofactors, could also affect promoter expression and confound the interpretation.
- **Why it matters** The central conclusion that affinity modulates promoter decoding depends on the assumption that the mutants differ only in DNA-binding affinity. If this is not validated, the results could be explained by other factors.
- **Resolution test** Directly measure DNA-binding affinity (e.g., by ChIP-seq or in vitro binding assays) and confirm that the mutants do not differ in other properties (e.g., protein levels, localization dynamics).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors suggest that TF degradation triggered by nuclear localization acts as a timer that limits expression of low-sensitivity genes, and that this may be a general mechanism for regulating gene expression.
- **Evidence pointer** Results section, Figure 2E–F, Figure S7
- **Concern** The degradation is inferred from the decay of the nuclear localization signal, but the authors do not directly measure Msn2 protein levels or degradation rates. The proposed timer mechanism is not tested experimentally, and it is unclear whether the observed plateau in expression is due to degradation or to other factors (e.g., promoter saturation, feedback regulation).
- **Why it matters** The timer hypothesis is a novel and potentially important claim, but it is not well supported by the current data. Without direct evidence, the claim remains speculative.
- **Resolution test** Measure Msn2 protein levels over time (e.g., by Western blot or fluorescence recovery after photobleaching) and test whether blocking degradation (e.g., by proteasome inhibition) affects the expression plateau.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the effects of changing Msn2 affinity on promoter decoding are highly promoter-dependent, and that this is due to differences in promoter sensitivity (K, n) and kinetic parameters (k1, d1, etc.).
- **Evidence pointer** Results section, Figure 3, Figure 4, Figure 5
- **Concern** The comparison between promoters is based on model fits, but the authors do not account for potential differences in mRNA stability, translation efficiency, or reporter protein maturation between promoters. These factors could affect the measured expression and confound the interpretation of promoter-dependent effects.
- **Why it matters** If the observed differences are due to post-transcriptional effects rather than promoter decoding, the conclusions about promoter architecture and affinity would be incorrect.
- **Resolution test** Control for mRNA and protein stability (e.g., by using reporters with identical 5' and 3' UTRs) or measure mRNA levels directly.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section
- **Evidence pointer** Methods section, "Light sweep experiments"
- **Issue** The description of the light sweep experiments is dense and could be clearer. For example, the exact timing of light pulses and the number of replicates per condition are not fully specified.
- **Required correction** Provide a more detailed protocol, including a timeline of light delivery and imaging, and specify the number of biological and technical replicates.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section, Figure 4
- **Evidence pointer** Figure 4A–C
- **Issue** The statistical comparison of expression levels between Msn2 mutants is not described. It is unclear whether the observed differences are statistically significant.
- **Required correction** Add statistical tests (e.g., ANOVA or mixed-effects models) and report p-values or confidence intervals for the comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section, "Strain construction"
- **Evidence pointer** Methods section, "Strain construction"
- **Issue** The methods for strain construction are described, but the exact plasmid maps and primer sequences are not provided. This makes it difficult to reproduce the work.
- **Required correction** Include plasmid maps, primer sequences, and a table of strains used in the study.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of the potential role of TF degradation as a timer is interesting but speculative. The authors do not discuss alternative explanations, such as feedback regulation or promoter desensitization.
- **Required correction** Acknowledge alternative mechanisms and suggest experiments to distinguish between them.

## Risk / unsupported claims
- The claim that Msn2 degradation acts as a timer for low-sensitivity gene expression is not directly supported by the data; it is inferred from population-level localization dynamics.
- The claim that the effects of affinity changes are primarily due to DNA-binding affinity is not fully validated, as the mutants are not characterized for other potential differences.
- The generalizability of the findings to other TFs and promoters is speculative and not tested.
- The model predictions about promoter sensitivity and kinetic parameters are not validated with independent experiments (e.g., perturbations of specific parameters).