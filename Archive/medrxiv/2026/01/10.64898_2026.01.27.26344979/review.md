## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure legends as provided.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims relative to presented evidence, and clarity of presentation. No assessment of editorial fit or journal-specific policy.
- **Shared manuscript claim summary** The authors present a multi-omic resource of CD4+ T cells from 362 genotyped individuals, integrating single-cell RNA-seq eQTLs, bulk ATAC-seq caQTLs, and ChromBPNet deep learning predictions to characterize regulatory variants and interpret immune-related GWAS loci.
- **Visible evidence base** Abstract, full introduction, results sections (Cohort Characteristics; Molecular QTLs; T cell state dynamics; ChromBPNet integration; TF motif disruption; GWAS colocalization), discussion, methods, data availability statements, and figure legends referenced in text.
- **Missing materials affecting confidence** Figures and supplementary tables are referenced but not provided. Key numerical results (e.g., total QTL counts, replication statistics, enrichment effect sizes) are described qualitatively. No supplementary figures or tables were available for inspection.

## Reviewer
- **Overall assessment** This manuscript presents a substantial data resource and a systematic integration of empirical QTL mapping with sequence-based deep learning predictions in CD4+ T cells. The study addresses an important question: how well do predictive models complement empirical molQTL discovery for interpreting GWAS variants? The authors report several notable findings, including the modest overlap between ChromBPNet predictions and empirical molQTLs, the enrichment of ChromBPNet variants at colocalized eQTL-caQTL loci, and the identification of context-dependent eQTLs. However, the manuscript as provided has significant gaps in quantitative reporting, and several central claims cannot be fully evaluated without the missing figures and tables. The statistical frameworks for key analyses (e.g., mediation, enrichment, colocalization) are described but not accompanied by sufficient detail on model validation, sensitivity analyses, or robustness checks. The claim that molQTLs explain 33% of immune-related GWAS loci is potentially impactful but requires careful comparison with existing resources to establish novelty. Overall, the work is promising and likely of interest to the functional genomics and statistical genetics communities, but the current evidence base is insufficient to fully support all conclusions.

- **Who would be interested in the results, and why** Statistical geneticists and functional genomics researchers interested in regulatory variant prioritization, particularly those working on immune-mediated diseases. The integration of single-cell eQTLs with chromatin accessibility QTLs and deep learning predictions addresses a methodological gap that many groups are actively working on. The resource itself (QTL summary statistics, fine-mapping, ChromBPNet models) will be of value to the broader community studying CD4+ T cell regulation. Researchers developing or applying variant effect prediction tools will also find the concordance analyses informative.

- **Major strengths**
  1. The study generates a multi-omic resource in a relevant primary cell type (CD4+ T cells) with substantial sample size (n=362), enabling well-powered QTL discovery.
  2. The integration of three orthogonal approaches (eQTLs, caQTLs, ChromBPNet) is conceptually strong and addresses a real gap in the field.
  3. The inclusion of dynamic eQTLs via CellRegMap adds a layer of context-dependency that is often missing from static QTL maps.
  4. The authors are transparent about limitations, including power constraints for rare cell states and the conservative peak calling.
  5. The mediation analysis framework to infer directionality between chromatin and expression is a thoughtful addition.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "molQTLs, primarily those affecting chromatin, indicated potential molecular drivers for 33% of immune-related GWAS loci."
- **Evidence pointer** Results section "Shared genetic signals between molQTLs and autoimmune diseases and traits"; Figure 6A; Table S5
- **Concern** The 33% figure is a headline result, but the manuscript does not provide the denominator (total number of GWAS loci tested), the criteria for "potential molecular drivers," or how this proportion compares to what would be expected by chance or from existing resources (e.g., eQTLGen, DICE, Fairfax et al.). Without these details, the reader cannot assess whether 33% represents a meaningful enrichment or simply reflects the proportion of loci with any regulatory variant in linkage disequilibrium. The comparison to existing CD4+ T cell QTL resources is essential to establish novelty.
- **Why it matters** This claim is central to the manuscript's stated goal of interpreting immune-related GWAS loci. If the 33% figure is not rigorously benchmarked against existing resources, the incremental value of this dataset is unclear.
- **Resolution test** Provide the total number of GWAS credible sets tested, the proportion expected by chance (e.g., via permutation or comparison to matched null loci), and a direct comparison to the proportion of loci explained by existing CD4+ T cell eQTL/caQTL resources. If the 33% is not significantly higher than existing resources, the claim should be reframed.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "predicted variant effects correlated with molQTLs, only a small fraction of empirically detected molQTLs were discovered by predictive models."
- **Evidence pointer** Results section "Integrating function-to-sequence models with caQTLs"; Figure 4C; Figure 4E
- **Concern** The manuscript reports a correlation between ChromBPNet log(aFC) and caQTL beta (R2 = 0.451 for variants significant in both methods), but the overlap analysis is difficult to interpret without knowing the total number of variants tested, the threshold for "discovery" in each method, and how the comparison was restricted to comparable variant sets. The statement that "only a small fraction" of molQTLs were discovered by ChromBPNet is presented without a precise fraction. Furthermore, the comparison of R2 values across different variant subsets (e.g., method-specific vs. shared) is not statistically framed; no confidence intervals or tests for difference in correlation are provided.
- **Why it matters** The concordance between predictive models and empirical QTLs is a key methodological contribution. If the overlap is as low as implied, this has implications for the field's reliance on deep learning predictions for variant prioritization. The claim needs to be quantified precisely and contextualized with appropriate statistical comparisons.
- **Resolution test** Report the exact number and proportion of empirical molQTLs (eQTL and caQTL separately) that contain at least one ChromBPNet-significant variant. Provide confidence intervals for the correlation coefficients and a formal test comparing correlations between variant subsets. Clarify whether the low overlap is driven by differences in statistical power, variant annotation, or genuine model limitations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors describe training ChromBPNet models on pooled ATAC-seq data from 8 individuals and using these models to score 159,908 SNPs.
- **Evidence pointer** Methods section "ChromBPNet variant scoring"; Figure S7
- **Concern** The choice of 8 individuals for model training is a critical methodological decision that is not justified. ChromBPNet is a deep learning model that typically requires large amounts of data for stable training. The manuscript does not report model performance metrics (e.g., AUPRC, calibration) on held-out chromosomes or individuals, nor does it describe how the model was validated. The pooling of individuals for training also raises questions about whether the model captures population-level variation or is biased toward the training individuals' genetic backgrounds.
- **Why it matters** The reliability of all downstream ChromBPNet-based claims depends on the quality of the trained model. If the model is poorly calibrated or overfit, the variant prioritization and TF motif disruption predictions are unreliable.
- **Resolution test** Report standard ChromBPNet performance metrics (e.g., AUPRC on held-out chromosomes, correlation between predicted and observed accessibility) and justify the choice of 8 training individuals. If model performance is inadequate, the authors should either train on more individuals or temper claims based on model predictions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors identify 210 dynamic eQTLs whose effect sizes vary along CD4+ T cell transcriptional trajectories.
- **Evidence pointer** Results section "T cell state dynamics modulate genetic effects"; Figure 2
- **Concern** The dynamic eQTL analysis using CellRegMap is described, but the manuscript does not report how the number of significant interactions was controlled for multiple testing across the large number of SNP-by-factor tests. The choice of MOFA factors as continuous states is reasonable, but the stability of these factors across pseudocell resolutions is not assessed. The authors mention testing across multiple Leiden resolutions but do not report how results were aggregated or whether the 210 dynamic eQTLs were consistent across resolutions.
- **Why it matters** Dynamic eQTLs are a relatively novel and potentially fragile class of findings. Without clear multiple testing control and stability assessment, the 210 dynamic eQTLs may include false positives driven by technical variation.
- **Resolution test** Report the multiple testing correction procedure (e.g., permutation-based FDR) and the number of dynamic eQTLs identified at each Leiden resolution. Assess overlap across resolutions and report whether the 210 dynamic eQTLs are robust to the choice of pseudocell parameters.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability
- **Claim pointer** The authors state that "gene-to-chromatin mediation mapped to more chromatin targets than chromatin-to-gene mapped to gene targets" and interpret this as evidence for distinct regulatory architectures.
- **Evidence pointer** Results section "Causal inference analysis"; Figure 3E-F
- **Concern** The mediation analysis using Findr is described, but the interpretation of the two directional models is underdeveloped. The finding that gene-to-chromatin mediation maps to more targets is attributed to "regulatory architecture," but alternative explanations (e.g., differences in statistical power between eQTL and caQTL discovery, differences in the number of tests performed) are not fully explored. The authors note that gene-to-chromatin loci are more frequently associated with C1/C2 caQTL variants, but the biological interpretation of this pattern is not clearly articulated.
- **Why it matters** The mediation analysis is a central component of the manuscript's claim to reveal "regulatory architectures." If the interpretation is not well-supported, the mechanistic conclusions are weakened.
- **Resolution test** Provide a more detailed discussion of alternative explanations for the observed asymmetry, including power considerations. Consider sensitivity analyses that match the number of tests or variants between the two models. Clarify the biological meaning of gene-to-chromatin mediation in the context of steady-state accessibility measurements.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, sentence 4
- **Issue** The abstract states "only a small fraction of empirically detected molQTLs were discovered by predictive models" without a specific number. This is a key quantitative claim that should be stated precisely in the abstract.
- **Required correction** Include the specific fraction (e.g., "X% of empirical molQTLs") in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Cohort description"
- **Evidence pointer** Methods section "Cohort description"
- **Issue** The age range is reported as 20-41 and 66-100 for young and old groups, respectively, but the median age is only given for the combined cohort. The manuscript does not report sex distribution or other key demographic variables.
- **Required correction** Report age and sex distributions separately for young and old groups.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "cis-eQTL mapping"
- **Evidence pointer** Methods section "cis-eQTL mapping"
- **Issue** The pseudobulk aggregation approach using Seurat's AverageExpression is described, but the number of cells per individual and the minimum cell count threshold are not reported.
- **Required correction** Report the distribution of cells per individual and any filtering thresholds applied.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Cohort Characteristics"
- **Evidence pointer** Results section "Cohort Characteristics"
- **Issue** The kinship cutoff is reported as 0.884, which is unusually high for a kinship coefficient (typically 0.0884 for third-degree relatives). This may be a typographical error.
- **Required correction** Verify the kinship cutoff value and correct if erroneous.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretability
- **Affected element** Results, "Shared genetic signals between molQTLs and autoimmune diseases and traits"
- **Evidence pointer** Results section "Shared genetic signals between molQTLs and autoimmune diseases and traits"
- **Issue** The manuscript reports colocalization with 88 independent GWAS for immune diseases and blood traits, but the list of traits and the sources of GWAS summary statistics are not provided in the main text.
- **Required correction** Provide a supplementary table listing all GWAS traits and data sources.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Allele specific quantification"
- **Evidence pointer** Methods section "Allele specific quantification"
- **Issue** The phASER analysis is described, but the number of heterozygous sites passing filters and the distribution of allelic counts are not reported.
- **Required correction** Report the number of sites analyzed and any quality filters applied.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Integrating function-to-sequence models with caQTLs"
- **Evidence pointer** Results section "Integrating function-to-sequence models with caQTLs"
- **Issue** The term "ChromBPNet variants" is used to refer to variants with significant predicted effects, but the threshold for significance (empirical p < 0.05) is only mentioned in the methods. This should be stated in the results for clarity.
- **Required correction** Define "ChromBPNet variants" in the results section with the significance threshold.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "ChromBPNet variant scoring"
- **Evidence pointer** Methods section "ChromBPNet variant scoring"
- **Issue** The manuscript states that variants were filtered to those within the ChromBPNet peak set, but the number of variants excluded by this filter is not reported.
- **Required correction** Report the number of variants before and after filtering.

## Risk / unsupported claims
- The claim that molQTLs explain 33% of immune-related GWAS loci is not benchmarked against existing resources and lacks a clear denominator; the proportion may not be significantly different from what is already known.
- The statement that "only a small fraction" of empirical molQTLs were discovered by ChromBPNet is not quantified, making it impossible to assess the practical utility of the deep learning approach.
- The biological interpretation of gene-to-chromatin vs. chromatin-to-gene mediation asymmetry is presented as "regulatory architecture" without ruling out statistical power differences.
- The GIMAP4 example (Figure 5B) is presented as an illustrative case, but the direction mismatch between ChromBPNet predictions and caQTL data is acknowledged without a resolved mechanism; the hypothesis regarding IRF2 competition is speculative and not directly tested.
- The claim that dynamic eQTLs reveal "regulatory architectures" is based on 210 loci, but the stability of these findings across pseudocell parameters is not demonstrated.
- The manuscript states that ChromBPNet variants are enriched at lower minor allele frequencies, but no statistical test or effect size is provided for this claim.
- The statement that "over half of the ChromBPNet variants were also supported by molQTL data" (Discussion) is not directly supported by the results section as written, which reports overlap in terms of loci rather than variants.