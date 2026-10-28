## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, conclusion, data availability, funding, acknowledgments)
- **Assessment boundary** Scientific and technical evaluation of the MOKA pipeline as described, including statistical methodology, validation approach, and reported results
- **Shared manuscript claim summary** The authors present MOKA, a Snakemake-based pipeline for SNP-set kernel association testing that integrates multiomics functional weights. They claim improved statistical power, population structure correction via spectral decomposition, and demonstrate application to schizophrenia GWAS with 89 Bonferroni-significant genes and 15.7% DisGeNET validation.
- **Visible evidence base** Methods section (design, configuration, kernel testing, spectral transformation, post-GWAS analyses), Results section (association results, validation, spectral transformation comparison, GO and KEGG enrichment), Figures 1-4 referenced, Tables 1-2 referenced
- **Missing materials affecting confidence** Figures and tables not provided; no supplementary materials; no code repository contents; no detailed simulation or benchmark methodology; no information on the schizophrenia GWAS cohort size, quality control, or imputation; no comparison of computational performance metrics

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful pipeline that automates a previously published statistical framework (data-bridged kernel association tests). The software engineering aspects appear sound, and the integration of Snakemake for reproducibility is commendable. However, the scientific validation is weak. The reported results are difficult to interpret without the actual figures and tables, the comparison to existing methods is incomplete, and the statistical properties of the proposed approach are not rigorously evaluated. The spectral decomposition correction is presented as a solution to population structure, but the reported lambda GC values remain substantially inflated, raising questions about the adequacy of the correction. The manuscript would benefit from a more thorough benchmarking against existing tools and a clearer demonstration of the claimed improvements in power and calibration.

- **Who would be interested in the results, and why** Statistical geneticists and bioinformaticians developing or using gene-based association testing methods would be the primary audience. Researchers working on integrating functional annotations into GWAS, particularly those using Snakemake workflows, would find the pipeline relevant. The schizophrenia application may interest psychiatric genetics researchers, though the biological findings are not the main contribution.

- **Major strengths**
  1. Addresses a genuine gap: no existing Snakemake pipeline specifically for kernel-based association tests with functional weight integration
  2. Modular design with clear configuration options and Docker support enhances reproducibility and accessibility
  3. Incorporates multiple post-GWAS analysis steps (GO, KEGG, DisGeNET validation) in a unified framework
  4. Provides a test dataset for users to verify installation and execution
  5. The spectral decomposition approach for population structure correction in set-based tests is a reasonable extension of existing methodology

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** "MOKA supports population structure correction via spectral decomposition" and "Applying MOKA's spectral correction (MOKA-Ph-COR) further lowered λGC to ≈ 4.3"
- **Evidence pointer** Methods section "Data transformation to control population structure"; Results section "Spectral transformation controls genomic inflation factor"; Table 2 (not provided)
- **Concern** The spectral decomposition correction is claimed to control population structure, yet the reported lambda GC values after correction (2.5 to 4.6) remain substantially above the well-calibrated threshold of 1.0 to 1.2. The authors acknowledge this ("additional adjustment for population structure may still be beneficial") but do not explain why the correction is insufficient or whether this residual inflation affects the validity of the reported associations. The manuscript does not provide a theoretical justification for why the spectral transformation should adequately control for population structure in the context of weighted kernel tests, nor does it compare the performance of this correction against established methods such as principal component adjustment or linear mixed models in the set-test framework.
- **Why it matters** If the correction does not adequately control for population structure, the reported significant associations may include false positives. The core methodological contribution of the pipeline is undermined if the statistical calibration is not demonstrated to be reliable.
- **Resolution test** Provide a simulation study with known population structure showing that the spectral correction controls type I error at the nominal level across a range of scenarios. Report lambda GC values close to 1.0 in well-calibrated settings. Alternatively, demonstrate that the residual inflation does not affect the ranking or interpretation of results through sensitivity analyses.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation and benchmarking
- **Claim pointer** "MOKA provides a robust, scalable, and extensible framework" and the comparison of validation proportions (15.7% for MOKA vs 13.3% for SKAT and 12.0% for REGENIE)
- **Evidence pointer** Results section "External database validation"; Table 2 (not provided)
- **Concern** The validation approach using DisGeNET overlap is presented as evidence of improved performance, but the comparison is not adequately controlled. The three methods (MOKA, SKAT, REGENIE) are applied to the same dataset, but the number of significant genes differs substantially (2,245 for MOKA, 2,530 for SKAT, 958 for REGENIE). The validation proportion is sensitive to the significance threshold and the total number of genes tested. A higher validation proportion could simply reflect a more conservative test (fewer genes called) rather than better biological relevance. The manuscript does not report precision-recall curves, enrichment of known schizophrenia genes, or other more robust validation metrics. Additionally, the comparison to REGENIE is confounded by the fact that REGENIE uses a different statistical framework (whole-genome regression) and may have different power characteristics.
- **Why it matters** The claim of improved validation is central to the manuscript's argument for the utility of MOKA. If the comparison is not fair or the metric is not appropriate, the conclusion that MOKA improves biological relevance is not supported.
- **Resolution test** Provide a more rigorous benchmarking framework: (1) use a gold-standard set of validated schizophrenia genes rather than a database with known ascertainment biases; (2) report power and type I error in simulations with known causal variants; (3) match the number of significant genes across methods or use continuous metrics such as area under the precision-recall curve; (4) include a null simulation to demonstrate that the validation proportion is not inflated by the testing procedure itself.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and completeness
- **Claim pointer** "MOKA is a fully automated analysis workflow" and "It is open-source and available at https://github.com/davidenoma/moka"
- **Evidence pointer** Methods section "Design of MOKA"; Data availability section
- **Concern** The manuscript describes the pipeline but does not provide sufficient detail for independent evaluation or reproduction. Key elements are missing: (1) the exact kernel function used is not fully specified (the equations are incomplete in the text); (2) the method for computing P-values from the mixture of chi-squared distributions is not described; (3) the parameters for the VAE-derived weights are not given; (4) the schizophrenia GWAS dataset characteristics (sample size, number of SNPs, quality control steps) are not reported; (5) the computational runtime and resource requirements are not quantified. While the code is available on GitHub, the manuscript should stand alone as a scientific description.
- **Why it matters** Reproducibility is a stated goal of the pipeline, but the manuscript does not provide enough information for a reader to understand or reproduce the results without extensive reverse-engineering of the code. This limits the scientific value of the contribution.
- **Resolution test** Provide complete mathematical specifications of the kernel and test statistic, describe the P-value computation method, report dataset characteristics, and include a detailed example run with expected outputs and runtime. Consider adding a supplementary methods document.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** "The top-associated gene, TMEM17, encodes a transmembrane protein involved in ciliogenesis and neural signaling, and has previously been implicated in schizophrenia"
- **Evidence pointer** Results section "Association results"; Figure 2 (not provided)
- **Concern** The biological interpretation of the top hit is minimal and does not add to the manuscript's contribution. The citation to Bigdeli et al. 2021 is not contextualized, and no discussion of whether the gene-level association is driven by specific variants, whether the functional weights contributed to the detection, or whether the finding replicates in independent datasets is provided. The manuscript would benefit from a more careful interpretation of the biological results, including potential limitations of the gene-based approach.
- **Why it matters** The schizophrenia application is presented as a use case, but the biological findings are not developed sufficiently to be informative. This weakens the demonstration of the pipeline's utility.
- **Resolution test** Provide additional biological context for the top findings, including replication attempts, examination of the specific variants contributing to the signal, and discussion of whether the functional weights improved biological interpretability compared to unweighted analysis.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Kernel-based association testing with multiomics weights"
- **Evidence pointer** Methods section, equations (incomplete in text)
- **Issue** The equations for the weighted kernel and test statistic are incomplete or incorrectly formatted in the manuscript text. The kernel definition and the test statistic formula are not fully specified.
- **Required correction** Provide complete, correctly formatted equations for the kernel function, the test statistic, and the null distribution.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "External database validation"
- **Evidence pointer** Results section; Table 2 (not provided)
- **Issue** The manuscript states "The validation proportion was calculated as the fraction of false discovery rate (FDR)-significant genes at P- < 0.05" but the notation "P-" is unclear and the threshold description is confusing. It is not clear whether the FDR is applied to the gene-level P-values or to a different set of tests.
- **Required correction** Clarify the validation proportion calculation, including the exact threshold and multiple testing correction method used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results section "Spectral transformation controls genomic inflation factor"
- **Evidence pointer** Results section; Table 2 (not provided)
- **Issue** The manuscript reports lambda GC values for different methods and datasets but does not provide confidence intervals or a clear description of how lambda GC was computed for each method. The range of values across datasets (2.5 to 4.6 for MOKA-ED-COR) is wide, and the interpretation is not consistent.
- **Required correction** Provide a clear description of lambda GC computation for each method and dataset, and include confidence intervals or a statistical test for whether lambda GC differs from 1.0.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Introduction section
- **Evidence pointer** Introduction, first paragraph
- **Issue** The introduction is brief and does not adequately contextualize the contribution. The distinction between MOKA and the previously published data-bridged architecture is not clearly articulated, and the specific advantages of the pipeline over existing tools are not enumerated.
- **Required correction** Expand the introduction to clearly state the novelty of MOKA relative to prior work, including a comparison table of existing pipelines and their limitations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section "Configuration, data and software requirements"
- **Evidence pointer** Methods section; Table 1 (not provided)
- **Issue** The description of the configuration file and parameters is incomplete. The manuscript mentions "Table 1" but does not describe the key parameters that users need to set, such as the kernel type, the weighting scheme, or the significance threshold.
- **Required correction** Provide a more detailed description of the configuration options and their default values, either in the text or in a supplementary table.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Validation
- **Affected element** Results section "Gene ontology analysis" and "KEGG pathway enrichment"
- **Evidence pointer** Results section; Figures 3 and 4 (not provided)
- **Issue** The GO and KEGG enrichment results are reported with P-values but no effect sizes, gene counts, or multiple testing correction details. The biological relevance of the top terms is not discussed.
- **Required correction** Report the number of genes in each enriched term, the multiple testing correction method, and provide a brief interpretation of the biological relevance of the top terms.

## Risk / unsupported claims
1. "MOKA provides a robust, scalable, and extensible framework" - The claim of scalability is not supported by any benchmark data on runtime, memory usage, or performance on large datasets.
2. "improving statistical power in GWAS" - No power analysis or simulation study is presented to support this claim.
3. "MOKA with spectral correction yields well-calibrated, biologically informed association tests" - The reported lambda GC values (2.5 to 4.6) do not support the claim of well-calibrated tests.
4. "The validation proportion was calculated as the fraction of false discovery rate (FDR)-significant genes at P- < 0.05" - The methodology for validation is unclear and the comparison across methods is not adequately controlled.
5. "TMEM17... has previously been implicated in schizophrenia" - The citation is provided but the context and strength of the prior evidence are not discussed.
6. The claim that MOKA "enhances variant prioritization and aggregation" is not directly tested; no comparison of variant prioritization between weighted and unweighted approaches is presented.
7. The statement "MOKA addresses these challenges by providing a robust, flexible, and user-friendly framework" is an assertion without supporting evidence from user studies or comparative analysis.