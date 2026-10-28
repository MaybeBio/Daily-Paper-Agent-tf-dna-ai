## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and supplementary file descriptions
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and presentation quality as presented in the provided manuscript
- **Shared manuscript claim summary** The authors present a computational framework that integrates multi-omics data (ChIP-seq, PPI, co-expression, Hi-C) via PANDA gene regulatory networks to predict gene expression in GM12878 and K562 cell lines, demonstrating improved prediction over cis-only models and utility in weighting rare variants for SKAT analysis
- **Visible evidence base** Main text figures (Figs. 1-7), tables (Table 1), and referenced supplementary files (Additional files 1-7) as described
- **Missing materials affecting confidence** Supplementary files (Additional files 1-7) not provided; detailed statistical outputs, full results tables, and additional validation details (e.g., HepG2 results) not accessible

## Reviewer
- **Overall assessment** This manuscript describes a useful integrative framework for modeling transcriptional regulation using gene regulatory networks derived from multiple omics data types. The core idea of incorporating trans-acting regulatory information via PANDA GRNs into predictive models of gene expression is sound and represents a meaningful extension over cis-only approaches. The authors demonstrate improved prediction performance and provide a practical application to rare variant analysis. However, several methodological details require clarification, and the evidence for some claims is incomplete or not fully accessible from the provided materials. The work is likely of interest to computational biologists and researchers studying gene regulation, but the current presentation does not fully establish the robustness and generalizability of the approach.

- **Who would be interested in the results, and why** Computational biologists, bioinformaticians, and researchers studying transcriptional regulation, gene regulatory networks, and integrative omics analysis. The framework's ability to combine diverse data types and its application to variant prioritization would also interest geneticists working on rare variant interpretation and functional genomics.

- **Major strengths** 
  1. The integration of trans-acting regulatory mechanisms (via PANDA GRNs) into gene expression prediction is a novel and valuable contribution, addressing a known limitation of cis-only models.
  2. The systematic comparison of different TFBS identification methods (positional, FIMO, TEPIC) and the inclusion of Hi-C data to capture chromatin interactions is thorough.
  3. The demonstration of practical utility through rare variant weighting in SKAT analysis provides a compelling application.
  4. The framework is flexible and extensible, allowing incorporation of additional data types.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that GRN-based models incorporating trans-acting mechanisms significantly outperform cis-only models (TEPIC) is central to the paper's contribution.
- **Evidence pointer** Figure 2, Additional file 3: Tables S3A-S3I
- **Concern** The performance comparison between GRN-based models and TEPIC-only models is presented as the key evidence for the benefit of including trans-acting information. However, the manuscript does not clearly describe the exact model configurations being compared. Specifically, it is unclear whether the TEPIC-only model uses the same set of TFs and TGs as the GRN-based models, and whether the comparison is fair in terms of feature space and regularization. The reported improvements, while statistically significant, are modest (e.g., median PCC 0.42 vs. 0.30 for GM12878), and the practical significance of these differences is not discussed. Additionally, the manuscript does not report confidence intervals or effect sizes beyond p-values, making it difficult to assess the magnitude and reliability of the improvement.
- **Why it matters** The central claim of the paper rests on this comparison. If the comparison is not properly controlled or the improvement is not robust, the main contribution of the work is weakened.
- **Resolution test** Provide a detailed description of the model configurations compared, including the number of features, the TF/TG sets, and the cross-validation procedure. Report confidence intervals for the performance metrics and discuss the practical significance of the observed improvements. Consider additional analyses such as permutation tests or comparisons on independent datasets to strengthen the claim.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that Hi-C data integration improves prediction performance, particularly through the "Hi-C UP" weighting scheme.
- **Evidence pointer** Figure 5, Additional file 7: Figure S4
- **Concern** The Hi-C weighting scheme is a key innovation, but the manuscript does not adequately explain the rationale for the "Hi-C UP" approach versus the "Hi-C DP" approach. The observation that promoter TFBS showed no evidence of within-promoter contacts (59% for GM12878 and 90% for K562) is surprising and raises questions about the quality or resolution of the Hi-C data used. The manuscript does not discuss potential reasons for this observation (e.g., data sparsity, resolution limits, or biological explanations). Furthermore, the improvement from Hi-C UP weighting is presented as significant, but the magnitude of improvement and its consistency across cell lines and TFBS identification methods are not fully detailed.
- **Why it matters** The Hi-C integration is presented as a major advance, but the methodological choices and their biological justification are not fully transparent. Without a clear explanation of why the UP weighting is appropriate and how robust the improvement is, the validity of this component is uncertain.
- **Resolution test** Provide a more detailed explanation of the Hi-C data processing, including quality control metrics and resolution. Discuss the biological rationale for the UP weighting scheme and address the unexpected lack of promoter contacts. Report the performance improvements with confidence intervals and assess consistency across different settings.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that the framework's utility is demonstrated through improved rare variant identification in SKAT analysis.
- **Evidence pointer** Figure 6, Additional file 6: Tables S6A-S6C
- **Concern** The SKAT analysis is presented as a demonstration of utility, but the manuscript does not provide sufficient detail on the statistical methodology or the interpretation of results. The comparison between merge score-based and z-score-based SKAT models is described, but the criteria for "improved" identification are not clearly defined. The replication rate of 32% for merge score-based models versus 21% for z-score-based models is reported, but the statistical significance of this difference is not assessed. Additionally, the manuscript does not discuss potential confounding factors, such as linkage disequilibrium or gene size, that could affect the results.
- **Why it matters** The application to rare variant analysis is a key selling point of the framework. If the improvement is not rigorously demonstrated, the practical value of the approach is less compelling.
- **Resolution test** Provide a more detailed description of the SKAT analysis, including the null model, covariates, and significance thresholds. Assess the statistical significance of the difference in replication rates. Discuss potential confounders and consider sensitivity analyses to ensure the robustness of the findings.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The overall framework is described as a general and flexible approach for integrating multi-omics data.
- **Evidence pointer** Methods section, Figure 1
- **Concern** The manuscript does not provide sufficient detail on the software implementation, parameter choices, or computational resources required to reproduce the results. For example, the PANDA algorithm's parameters, the ENET regularization parameters (beyond alpha=0.5), and the specific versions of software tools are not fully specified. The manuscript states that "all the published algorithms and datasets used in this study have been described in supplementary data," but the supplementary materials are not provided for review. This limits the ability to assess the reproducibility of the work.
- **Why it matters** Reproducibility is a core requirement for computational biology research. Without clear implementation details, other researchers cannot build upon or validate the framework.
- **Resolution test** Provide a detailed description of the computational environment, software versions, parameter settings, and data processing pipelines. Consider making the code and processed data publicly available to facilitate reproducibility.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2
- **Evidence pointer** Figure 2
- **Issue** The figure labels and legend are not fully described in the text. The significance markers (asterisks) are mentioned but the exact p-value thresholds for each marker are not defined in the figure legend.
- **Required correction** Add a clear description of the significance markers and their corresponding p-value thresholds in the figure legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section
- **Evidence pointer** Results section, "Accounting for trans acting mechanisms" subsection
- **Issue** The manuscript mentions that results from all analyses are provided in Additional file 3: Tables S3A-S3I, but these tables are not available for review. This makes it difficult to fully evaluate the claims.
- **Required correction** Ensure that all supplementary tables are made available to reviewers and readers, and consider including key summary statistics in the main text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of the biological interpretation of TF effect estimates is somewhat brief. The authors mention that the approach can characterize TF roles, but do not discuss potential limitations of using linear effect estimates from regularized regression for this purpose.
- **Required correction** Expand the discussion to address the limitations and potential biases of the effect estimates, and how they should be interpreted in a biological context.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Methods section
- **Evidence pointer** Methods section, "Generating Hi-C weightings"
- **Issue** The description of the Hi-C weighting scheme is dense and could be clearer. The distinction between "Hi-C DP" and "Hi-C UP" is not immediately obvious from the text.
- **Required correction** Rewrite this section to provide a clearer step-by-step explanation of the weighting scheme, possibly with a small illustrative example.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Validation
- **Affected element** Results section, HepG2 analysis
- **Evidence pointer** Results section, "Accounting for trans acting mechanisms" subsection
- **Issue** The HepG2 analysis is mentioned as additional validation, but the results are only described in Additional file 1, which is not provided. The main text does not include any quantitative results for this validation.
- **Required correction** Include a brief summary of the HepG2 results in the main text, or at least provide the key quantitative findings.

## Risk / unsupported claims
- The claim that GRN-based models "significantly outperform" cis-only models is supported by the reported p-values, but the practical significance and robustness of the improvement are not fully established without confidence intervals and effect sizes.
- The claim that Hi-C UP weighting improves prediction is not fully supported without a detailed explanation of the methodology and robustness checks.
- The claim that the framework enriches rare variant identification in SKAT analysis is not fully supported without a more rigorous statistical comparison and discussion of potential confounders.
- The generalizability of the framework to other cell types and conditions is not established, as only two cell lines (plus HepG2, not fully described) are tested.
- The biological interpretation of TF effect estimates as reflecting activation or repression is plausible but not directly validated experimentally.
- The manuscript's claim of providing "a framework for integrating multiple data types into a single model" is supported, but the practical utility and scalability to larger datasets are not discussed.