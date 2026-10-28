## Review setup
- **Input scope** Full manuscript text (preprint, medRxiv)
- **Assessment boundary** Scientific content, methodology, and claims as presented in the provided text; no external data or code verification performed
- **Shared manuscript claim summary** The authors generated multi-omic QTL data (eQTLs, caQTLs) from CD4+ T cells of 362 individuals, integrated these with ChromBPNet sequence-based predictions, and used this framework to interpret regulatory architectures at immune-related GWAS loci.
- **Visible evidence base** Main text (Abstract, Introduction, Results, Discussion, Methods), figure callouts (Figures 1–6, S1–S11), supplementary table callouts (Tables S1–S6), data availability statements
- **Missing materials affecting confidence** Figures and supplementary tables not provided; no code or data repositories accessed; no line numbers; no supplementary methods details beyond main text

## Reviewer
- **Overall assessment** This manuscript presents a substantial multi-omic resource and a systematic integration of empirical QTL mapping with sequence-based deep learning predictions. The study addresses an important question: how well do predictive models complement empirical QTL mapping for interpreting noncoding variation? The cohort size (362 individuals) is reasonable for eQTL discovery, and the inclusion of both expression and chromatin accessibility QTLs adds value. However, several key claims regarding concordance, mediation, and GWAS interpretation are presented with limited quantitative detail in the text provided. The manuscript would benefit from clearer reporting of effect sizes, confidence intervals, and validation metrics. The novelty is moderate, building on established methods (ChromBPNet, CellRegMap, coloc) applied to a new dataset. The interdisciplinary relevance is clear, spanning genomics, immunology, and computational biology.

- **Who would be interested in the results, and why** Researchers in functional genomics, regulatory genomics, and immunogenetics would be interested. The multi-omic QTL resource in CD4+ T cells is a useful community asset. Those working on variant prioritization and interpretation of GWAS loci, particularly in autoimmune diseases, would find the integration of empirical and predictive approaches relevant. Methodologists developing or applying deep learning models for regulatory genomics would also be interested in the concordance analyses.

- **Major strengths**
  1. Generation of a multi-omic QTL resource (eQTLs, caQTLs) in a well-powered cohort of CD4+ T cells from 362 individuals, with data availability statements.
  2. Systematic integration of three complementary approaches: empirical QTL mapping, single-cell dynamic eQTL mapping, and sequence-based deep learning predictions.
  3. Application of causal mediation analysis to infer directionality between chromatin accessibility and gene expression, which is a valuable analytical contribution.
  4. The study provides a realistic assessment of the limitations of sequence-based models, noting that only a small fraction of empirical molQTLs are captured by ChromBPNet predictions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "predicted variant effects correlated with molQTLs" and that concordant effects were validated by allele-specific accessibility measurements.
- **Evidence pointer** Results section "Integrating function-to sequence models with caQTLs to prioritize putative causal variants modulating chromatin accessibility in CD4+ T cells"; Figure 4E; Figure S8A–B
- **Concern** The correlation between ChromBPNet log(aFC) and empirical caQTL beta is reported as R2=0.451 for variants significant in both methods. However, the text does not specify the number of variants in this intersection, the confidence interval for the correlation, or whether this correlation is driven by a subset of loci. The allele-specific validation using phASERpop is mentioned but no quantitative results (e.g., correlation coefficients, number of heterozygous sites tested, significance thresholds) are provided in the text. Without these details, the strength of the concordance claim cannot be fully evaluated.
- **Why it matters** The concordance between predictive and empirical methods is a central claim of the paper. If the correlation is weak or based on a small number of variants, the conclusion that these methods are complementary would be weakened. The allele-specific validation is presented as supporting evidence, but without numbers, it is not possible to assess its robustness.
- **Resolution test** Provide the number of variants in the concordance analysis, the Pearson correlation coefficient with 95% confidence interval, and a scatter plot or equivalent visualization. For the phASERpop validation, report the number of heterozygous sites, the correlation between allelic imbalance and predicted effects, and the significance of the enrichment.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "MolQTLs, primarily those affecting chromatin, indicated potential molecular drivers for 33% of immune-related GWAS loci, with the deep learning approach providing insights into 4.7% of GWAS loci."
- **Evidence pointer** Results section "Shared genetic signals between molQTLs and autoimmune diseases and traits"; Figure 6A; Tables S4–S6
- **Concern** The 33% and 4.7% figures are presented as headline results, but the text does not explain how these percentages were calculated. Specifically, it is unclear whether the denominator is the total number of GWAS loci tested, the number of GWAS loci with at least one variant in the analyzed regions, or something else. The text also does not state how many GWAS loci were analyzed in total, how many were colocalized with eQTLs versus caQTLs, or how the "insights" from ChromBPNet were defined (e.g., overlap with GWAS credible sets, predicted regulatory impact). Without this context, the reader cannot interpret the significance of these proportions.
- **Why it matters** The proportion of GWAS loci explained by molQTLs is a key metric for the utility of the resource. If the denominator is inflated (e.g., including loci with no tested variants), the 33% figure would be an underestimate. Conversely, if the definition of "insight" from ChromBPNet is too lenient, the 4.7% figure could be misleading. This affects the overall conclusion about the value of integrating predictive models.
- **Resolution test** Clearly define the denominator for each percentage. Report the total number of GWAS loci tested, the number with at least one tested variant, and the number colocalized with eQTLs, caQTLs, or both. For ChromBPNet, specify the criteria for "providing insights" (e.g., overlap with GWAS credible sets, predicted regulatory impact score threshold) and report the number of loci meeting those criteria.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that they trained ChromBPNet models on "pooled chromatin accessibility profiles (125,944 peaks, 120k mean reads/individual) from 8 individuals."
- **Evidence pointer** Methods section "ChromBPNet model for pan CD4+ T cells"; Figure S7A–C
- **Concern** The choice of 8 individuals for training is not justified. The text does not explain why this subset was chosen, whether it is representative of the full cohort, or whether model performance was evaluated on held-out individuals. The median Pearson r=0.752 is reported, but it is unclear whether this is on training or validation data. The manuscript would benefit from a description of model selection, hyperparameter tuning, and evaluation strategy.
- **Why it matters** ChromBPNet predictions are used throughout the manuscript for variant prioritization and TF motif disruption analysis. If the model is overfit to the training individuals or not generalizable, the downstream conclusions could be affected. The reproducibility of the model training is also important for others who may want to apply the same approach.
- **Resolution test** Provide details on how the 8 training individuals were selected, whether model performance was assessed on held-out data, and report evaluation metrics (e.g., Pearson r, AUROC) on validation and test sets. If possible, show that model performance is stable across different training subsets.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors report "210 cis-eQTLs whose effect sizes vary significantly in CD4+ T pseudocells along transcriptional trajectories" from CellRegMap analysis.
- **Evidence pointer** Results section "T cell state dynamics modulate genetic effects across immune cellular programs"; Figure 2A–B
- **Concern** The text does not describe the multiple testing correction applied to the CellRegMap results. Given that 6,939 eQTLs were tested across multiple factors and pseudocell resolutions, the number of tests is large. The FDR threshold is stated as 0.05, but the method for FDR estimation is not described. Additionally, the choice of Leiden resolution 3.4 over other resolutions is not justified beyond "variance explained and factor independence," which is vague.
- **Why it matters** The dynamic eQTL results are used to support claims about context-dependent regulation. If the FDR control is not properly described, the reader cannot assess the reliability of the 210 dynamic eQTLs. The choice of pseudocell resolution could also affect the results, and the lack of sensitivity analysis is a concern.
- **Resolution test** Describe the FDR estimation procedure for CellRegMap results, including the number of tests and the method used. Provide a sensitivity analysis showing that the number of dynamic eQTLs is robust across different pseudocell resolutions or explain why one resolution was chosen.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "gene-to-chromatin mediation mapped to more chromatin targets than chromatin-to-gene mapped to gene targets, as expected given the larger number of peaks tested (71,348) relative to genes (26,681)."
- **Evidence pointer** Results section "Causal mediation analysis reveals distinct regulatory architectures associated with molQTLs"; Figure 3B–C
- **Concern** The interpretation of the mediation analysis results is presented as if the difference in target counts is solely due to the number of peaks versus genes tested. However, the mediation analysis was only performed on colocalized triplets (18,309), and the number of significant mediation events depends on statistical power, effect sizes, and the specific tests used. The text does not report the number of significant mediation events for each direction, the FDR thresholds, or the overlap between the two models. The claim that the difference is "as expected" is an oversimplification.
- **Why it matters** The mediation analysis is a key analytical contribution, and the interpretation of the results informs the discussion of regulatory architecture. If the difference in target counts is not properly contextualized, the reader may draw incorrect conclusions about the relative importance of chromatin-to-gene versus gene-to-chromatin regulation.
- **Resolution test** Report the number of significant mediation events for each direction, the FDR thresholds used, and the overlap between the two models. Provide a more nuanced interpretation that accounts for statistical power and effect sizes, not just the number of features tested.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, "only a small fraction of empirically detected molQTLs were discovered by predictive models"
- **Issue** The phrase "discovered by predictive models" is ambiguous. It is unclear whether this means the predictive models identified the same variants as significant, or whether the models predicted a functional effect for these variants.
- **Required correction** Rephrase to clarify the comparison, e.g., "only a small fraction of empirically detected molQTLs were also predicted to have significant effects by ChromBPNet."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Cohort description"
- **Evidence pointer** Methods section "Cohort description"
- **Issue** The text states that the cohort includes "healthy, self-identified Ashkenazi Jewish individuals" but does not specify how "healthy" was defined or whether any exclusion criteria were applied beyond the stated age ranges.
- **Required correction** Provide a brief description of health criteria or state that no specific health exclusions were applied beyond the recruitment criteria.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results, "Molecular QTLs explain distinct regulatory contexts"
- **Evidence pointer** Results section "Molecular QTLs explain distinct regulatory contexts across gene expression and chromatin accessibility"; Figure 1B
- **Issue** The text reports 10,424 eQTLs and 68,294 caQTLs at 5% FDR but does not state the number of independent loci or genes tested, nor the effective number of tests. This makes it difficult to assess the FDR calibration.
- **Required correction** Report the number of genes and peaks tested, and if possible, the effective number of independent tests used for FDR estimation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Integrating function-to sequence models"
- **Evidence pointer** Results section "Integrating function-to sequence models with caQTLs to prioritize putative causal variants modulating chromatin accessibility in CD4+ T cells"; Figure 4C
- **Issue** The text describes "seven distinct interception groups" but does not list them or explain the naming convention clearly.
- **Required correction** Provide a brief description of the seven groups or refer to a supplementary table that lists them.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "QTL colocalization with GWAS traits"
- **Evidence pointer** Methods section "QTL colocalization with GWAS traits"
- **Issue** The text states that colocalization was performed with "88 independent GWAS" but does not specify the sources of these GWAS or the criteria for independence.
- **Required correction** List the GWAS sources or provide a supplementary table with references and sample sizes.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion, "Despite our single-cell data and dynamic eQTL mapping, our power to detect eQTLs in rare cell states or transient cellular subpopulations is limited"
- **Issue** The discussion of limitations is brief and does not address potential confounding factors such as cell type composition, batch effects, or the impact of pseudocell construction on power.
- **Required correction** Expand the limitations paragraph to address these potential confounders and their likely impact on the results.

## Risk / unsupported claims
- The claim that ChromBPNet provides "insights into 4.7% of GWAS loci" is not fully supported without a clear definition of "insights" and the denominator used.
- The statement that "gene-to-chromatin mediation mapped to more chromatin targets than chromatin-to-gene mapped to gene targets, as expected given the larger number of peaks tested" is an interpretation that is not fully supported by the data presented.
- The concordance between ChromBPNet predictions and empirical caQTL effects is reported with R2=0.451, but the number of variants and confidence intervals are not provided, making the strength of this correlation difficult to assess.
- The claim that "predicted variant effects correlated with molQTLs" is presented without specifying which molQTLs (eQTLs, caQTLs, or both) and without reporting the correlation coefficient for each comparison.
- The statement that "only a small fraction of empirically detected molQTLs were discovered by predictive models" is ambiguous and not quantified in the abstract or results.
- The choice of 8 individuals for ChromBPNet training is not justified, and the generalizability of the model is not demonstrated.
- The FDR estimation for CellRegMap results is not described, making the 210 dynamic eQTLs difficult to evaluate.
- The mediation analysis results are summarized without reporting the number of significant events for each direction or the FDR thresholds used.