## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and figure captions
- **Assessment boundary** Scientific content, methodological rigor, claims and their support, technical soundness, and presentation quality
- **Shared manuscript claim summary** The authors present PyProBound, a reimplementation of the ProBound framework, for building DNA binding affinity models from allele-agnostic in vivo data (ChIP-seq, ChIP-exo, CUT&Tag) without read mapping or peak calling. They introduce a beta-binomial likelihood function for benchmarking sequence-to-affinity models against allele-specific ChIP-seq counts, and demonstrate that models trained with explicit fragmentation bias modeling outperform those trained without, and that de novo motif discovery can be performed directly from allele-specific counts.
- **Visible evidence base** Main text figures 1-5, supplementary figures S1-S7 (referenced but not fully visible), methods section, statistical details for beta-binomial model and bootstrapping
- **Missing materials affecting confidence** Supplementary figures S1-S7 are referenced but not provided in the submitted material; raw data and code availability are not described in the visible text; details on hyperparameter selection for PyProBound beyond the lambda values are limited; the exact number of variants used in the beta-binomial likelihood analysis beyond the counts for CTCF, EBF1, and PU.1 is not fully specified

## Reviewer
- **Overall assessment** This manuscript addresses an important problem in regulatory genomics: how to quantitatively benchmark and build DNA binding affinity models that can predict the functional impact of non-coding variants. The authors propose a principled likelihood-based framework for aggregating allele-specific evidence across the genome, which is a meaningful advance over per-variant significance testing. The PyProBound software is a useful contribution, and the demonstration that fragmentation bias modeling improves model quality is valuable. However, several technical aspects require clarification and additional validation before the claims are fully established. The comparison between models is largely based on a single metric (the beta-binomial likelihood), and the practical utility of the proposed approach for variant effect prediction at the individual level remains unclear. The manuscript is well written and the methods are described in sufficient detail for reproduction, but the evidence for some claims, particularly regarding the superiority of in vivo-derived models and the generalizability of the approach, is not fully convincing.

- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and statistical genetics would be interested. Specifically, those working on transcription factor binding specificity, variant effect prediction, and the interpretation of non-coding GWAS variants would benefit from the benchmarking framework and the PyProBound software. The work is also relevant to experimentalists generating ChIP-seq, ChIP-exo, or CUT&Tag data who wish to derive quantitative binding models from their data without peak calling.

- **Major strengths**
  1. The beta-binomial likelihood framework for aggregating allele-specific evidence across the genome is a principled and statistically sound approach that avoids the limitations of per-variant significance testing.
  2. The PyProBound software is a flexible, open-source reimplementation that addresses a real need for handling variable-length paired-end sequencing data.
  3. The explicit modeling of fragmentation bias in ChIP-seq analysis is an important technical contribution that improves model quality.
  4. The demonstration of de novo motif discovery from allele-specific counts is novel and potentially impactful.
  5. The use of multiple independent datasets (AlleleDB, ENCODE, SRA) and multiple TFs (CTCF, EBF1, PU.1) strengthens the generalizability of the findings.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "models derived from in vivo data in an allele-agnostic manner generally perform better than those derived from in vitro binding data" based on the beta-binomial likelihood metric.
- **Evidence pointer** Figure 4, Results section "Taking DNA fragmentation bias into account when analyzing ChIP-seq data yields superior sequence-to-affinity models"
- **Concern** The comparison between in vivo-derived and in vitro-derived models is based on a single metric (beta-binomial likelihood) applied to the same test dataset. However, the in vivo-derived models are trained on data from the same cell type or condition as the test data, while the in vitro models are not. This creates a potential confounding factor: the in vivo models may perform better simply because they are trained on data from the same biological context, not because they are intrinsically better at capturing binding affinity. The authors do not control for this by, for example, testing cross-cell-type generalization or using held-out chromosomes for training and testing.
- **Why it matters** The claim of superiority of in vivo-derived models is central to the paper's message. If the comparison is confounded by training-test overlap in biological context, the conclusion may not hold in other settings where in vitro models are the only option.
- **Resolution test** The authors should either (a) train in vivo models on one cell type and test on another, (b) use cross-validation with held-out chromosomes, or (c) explicitly discuss and control for the training-test context overlap. Without such controls, the claim should be tempered.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "PyProBound can leverage our threshold-free ASB likelihood function to perform de novo motif discovery using allele-specific ChIP-seq counts" and show agreement with existing models (Figure 5).
- **Evidence pointer** Figure 5, Results section "De novo motif discovery from allele-specific ChIP-seq counts"
- **Concern** The de novo motif discovery is demonstrated for CTCF and EBF1 with good agreement, but for PU.1 the agreement is inferior (R2 = 0.739), and the authors attribute this to "additional specificity at one end of the binding mode." This discrepancy is not fully explored. The authors do not provide a statistical test for whether the observed agreement is significantly better than what would be expected by chance, nor do they compare against a null distribution of random motifs. Additionally, the number of variants used for PU.1 (387) is smaller than for CTCF (2231), which may limit statistical power, but this is not discussed.
- **Why it matters** The claim that the method can recover known binding specificity from allele-specific data is a key novelty. If the method fails for some TFs or if the agreement is not statistically validated, the generalizability of the approach is questionable.
- **Resolution test** The authors should provide a null distribution for the R2 values (e.g., by permuting the allele labels or using random motifs) and report p-values for the observed agreement. They should also discuss the PU.1 discrepancy in more detail, including whether it reflects a true biological difference or a methodological limitation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors introduce PyProBound as a "flexible and modular" reimplementation of ProBound, but the manuscript does not describe the software architecture, dependencies, or usage in sufficient detail for others to adopt it.
- **Evidence pointer** Methods section "In vivo binding data analysis with PyProBound"
- **Concern** The methods describe the mathematical model and the loss function, but do not provide information on how to install, configure, or run PyProBound. There is no mention of a repository URL, documentation, or example usage. The original ProBound is referenced, but the differences in implementation and the new features of PyProBound are not clearly enumerated.
- **Why it matters** A central contribution of the paper is the software itself. Without clear instructions and availability, other researchers cannot reproduce the results or apply the method to their own data, which limits the impact of the work.
- **Resolution test** The authors should provide a link to a public repository, include installation instructions, and describe the key API functions and parameters. A brief usage example or tutorial would also be helpful.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors use bootstrapping to assess the significance of differences in log-likelihood between models (Figure 3, Figure 4), but the details of the bootstrap procedure are not fully described.
- **Evidence pointer** Methods section "Bootstrapping of log-likelihood", Figure 3, Figure 4
- **Concern** The authors state that variants were resampled 1000 times with replacement, but do not specify whether the resampling was done at the level of individual variants or at the level of genomic loci. They also do not report confidence intervals for the differences in log-likelihood between models, only p-values from a Wilcoxon test. The Wilcoxon test is non-parametric and may not be the most appropriate choice for comparing bootstrap distributions, which are typically approximately normal.
- **Why it matters** The statistical comparison between models is a key part of the paper. If the bootstrap procedure is not correctly specified or the statistical test is inappropriate, the conclusions about model superiority may not be reliable.
- **Resolution test** The authors should describe the bootstrap resampling scheme in detail, report confidence intervals for the log-likelihood differences, and justify the choice of statistical test. They should also consider using a paired bootstrap test that accounts for the correlation between models evaluated on the same variants.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The figure legend is brief and does not fully explain the schematic. In particular, the meaning of the "cumulative binding affinity" and how it is computed from the sliding window is not clear from the figure alone.
- **Required correction** Expand the figure legend to explain the computation of cumulative binding affinity and the sliding window approach.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Prediction of CTCF allele-specific binding events using sequence-to-affinity models"
- **Evidence pointer** Figure 2
- **Issue** The authors report concordance rates for the direction of allelic preference but do not provide confidence intervals or a statistical test for whether the concordance is significantly different from 50% for the stratified subsets (e.g., in Figure 2C-E).
- **Required correction** Add confidence intervals or a statistical test for the concordance rates in the stratified analyses.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Beta-binomial model of genome-wide allelic effects on the binding affinity"
- **Evidence pointer** Methods
- **Issue** The parameter C is described as "background binding due to indirect effects or binding of other TFs," but it is not clear how this parameter is estimated or whether it is constrained to be non-negative. The interpretation of C in the context of the beta-binomial model could be clarified.
- **Required correction** Clarify the estimation procedure for C and its interpretation, and specify any constraints on its value.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of the PU.1 discrepancy is brief and does not fully address the implications for the method's generalizability.
- **Required correction** Expand the discussion of the PU.1 result, including potential biological or methodological explanations and how this might affect the interpretation of the method's performance.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "In vivo binding data used for de novo motif discovery using ProBound"
- **Evidence pointer** Methods
- **Issue** The accession numbers for the ChIP-exo and CUT&Tag data are provided, but the specific processing steps (e.g., adapter trimming, quality filtering parameters) are not fully described for these datasets.
- **Required correction** Provide a complete description of the data processing pipeline for all datasets used.

## Risk / unsupported claims
- The claim that in vivo-derived models "generally perform better" than in vitro-derived models is not fully supported due to potential confounding between training and test biological contexts (R1-M1).
- The claim that de novo motif discovery from allele-specific counts is successful is not statistically validated against a null distribution (R1-M2).
- The claim that PyProBound is a "flexible and modular" framework is not verifiable from the manuscript alone, as no software availability or usage details are provided (R1-M3).
- The claim that the beta-binomial likelihood framework "can be broadly useful for benchmarking sequence-based predictors" is plausible but not demonstrated beyond the three TFs analyzed.
- The statement that "our results underscore both the usefulness of resources such as AlleleDB and the extensibility of (Py)ProBound" is a reasonable summary but the extensibility claim is not fully demonstrated.