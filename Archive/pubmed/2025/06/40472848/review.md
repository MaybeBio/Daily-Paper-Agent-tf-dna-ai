## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, supplementary figure legends, and discussion sections as provided)
- **Assessment boundary** Scientific validity, technical soundness, and significance of the iterative deep learning enhancer design approach; claims are evaluated against the evidence presented in the provided text
- **Shared manuscript claim summary** The authors present an iterative deep learning framework for designing synthetic human enhancers with cell type-specific activity. They train models on published MPRA and chromatin accessibility data, design and experimentally validate enhancer libraries in HepG2 and K562 cells, retrain on their own data, and demonstrate improved specificity across design rounds. They characterize sequence grammar features, validate causal motifs via perturbation experiments, and show that enhancers as short as 50 bp retain specificity.
- **Visible evidence base** Results sections describing R1-MPRA, R1-DHS, and R2 libraries; experimental validation in two cell lines; motif analysis; ablation studies; scMPRA; simulation analyses; methods sections for model training, design algorithms, and statistical analyses
- **Missing materials affecting confidence** Full figures and supplementary tables (referenced but not provided); exact numerical values for many reported statistics; complete details of model architectures and hyperparameters; raw data and code availability statements; details of scMPRA quality control metrics

## Reviewer
- **Overall assessment** This manuscript presents a compelling and technically rigorous approach to a significant problem in synthetic biology: the design of cell-type-specific enhancers. The iterative design-build-test cycle, with retraining on small, high-quality datasets, is a notable advance over single-round design approaches. The combination of MPRA and DTA-based training data, multiple design algorithms, and extensive downstream characterization (motif analysis, ablations, scMPRA) provides a comprehensive picture. The demonstration that 50 bp enhancers retain specificity is particularly interesting. However, several technical concerns need to be addressed to fully establish the claims, particularly regarding the statistical robustness of some comparisons, the generalizability of the findings, and the interpretation of the scMPRA correlation analyses.

- **Who would be interested in the results, and why** Researchers in synthetic biology, gene therapy, and regulatory genomics would find this work highly relevant. The practical demonstration of iterative deep learning design with small datasets is directly applicable to efforts in cell-type-specific gene expression control. The detailed characterization of sequence grammar and motif interactions contributes to fundamental understanding of enhancer biology. The scMPRA approach for linking enhancer activity to TF expression at single-cell resolution is a methodological contribution of broad interest.

- **Major strengths**
  1. The iterative design strategy, with retraining on small, high-quality datasets, is a practical and potentially generalizable advance.
  2. The use of both MPRA and chromatin accessibility data as training sources, and the comparison of multiple design algorithms, strengthens the conclusions.
  3. The extensive validation and characterization, including motif analysis, ablation experiments, and scMPRA, provides mechanistic insight beyond simple demonstration of function.
  4. The demonstration of functional enhancers as short as 50 bp has practical implications for therapeutic vector design.
  5. The analysis of motif grammar evolution across design rounds is insightful and well-supported.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that iterative retraining results in "dramatic performance improvements" in enhancer specificity across design rounds.
- **Evidence pointer** Results section "Iterative retraining and design results in improved enhancer specificity and precision"; Figure 1F
- **Concern** The comparison of best-performing enhancers across libraries (R0, R1, R2) is based on the maximum observed specificity in each library. This is highly sensitive to library size and sampling. The bootstrap analysis (Figure 1F) partially addresses this, but the reported percentages (e.g., 92.6% for HepG2 at n=5) need confidence intervals. More importantly, the claim of "dramatic" improvement should be supported by a formal statistical comparison of the full distributions of specificities, not just the extremes. The authors should report effect sizes and confidence intervals for the differences in median specificity between libraries.
- **Why it matters** The central claim of the paper is that iterative design improves performance. If this is not rigorously established, the main contribution is weakened. The current analysis may overstate the improvement due to selection bias in taking the maximum.
- **Resolution test** Provide confidence intervals for the bootstrap estimates in Figure 1F. Additionally, perform a formal comparison of the full specificity distributions (e.g., Kolmogorov-Smirnov test or a mixed-effects model) between R1 and R2 libraries, reporting effect sizes. If the improvement is only in the tails of the distribution, this should be stated explicitly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "enhancer activity is correlated with transcription factor expression at the single cell level" based on scMPRA data.
- **Evidence pointer** Results section "A scMPRA enables characterization of enhancer activity at the single cell level"; Figure 5C, 5G, 5H
- **Concern** The correlation analysis between enhancer activity and TF expression across single cells is potentially confounded by several factors. First, the analysis uses pseudobulk binning of cells by TF expression, which can inflate correlations. Second, the correlation between a specific enhancer's activity and the expression of a TF whose motif is present does not establish causality, as many TFs are co-expressed. Third, the authors note that TF mRNA levels may not reflect protein activity (e.g., TP53 is non-functional in K562). The analysis should control for these confounders, for example by using a permutation-based null model that accounts for the number of motifs in each enhancer, or by regressing out the effects of other TFs.
- **Why it matters** The scMPRA correlation is presented as evidence for the causal role of specific TFs in driving enhancer activity. If this correlation is confounded, the mechanistic interpretation is weakened.
- **Resolution test** Perform a permutation analysis where TF expression labels are shuffled across cells to establish a null distribution of correlations. Additionally, perform a multiple regression analysis including expression levels of multiple TFs to assess the independent contribution of each TF. Report the results of these analyses.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors suggest that their approach "may be more readily adapted to selecting enhancers for specific cell types in vivo."
- **Evidence pointer** Discussion section; Results section "Iterative retraining and design results in improved enhancer specificity and precision"
- **Concern** The demonstration is limited to two cell lines (HepG2 and K562) and uses plasmid-based reporters. The authors do not test whether the designed enhancers function in the context of chromatin, in primary cells, or in vivo. The claim of adaptability to in vivo settings is speculative without such validation. The authors should either provide preliminary data in a more complex system or temper the claim.
- **Why it matters** The practical utility of the approach for therapeutic applications depends on its performance in more physiologically relevant contexts. Overstating the potential without evidence could mislead the field.
- **Resolution test** Provide a clear statement that in vivo validation is a necessary next step and not yet demonstrated. If possible, include preliminary data from a small number of enhancers tested in a different cell type or in a chromatin context (e.g., lentiviral integration).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1C
- **Evidence pointer** Results section "Deep learning predictors enable design of cell type-specific enhancers from MPRA data"
- **Issue** The description of Figure 1C is brief. It is unclear whether the plot shows individual data points, distributions, or summary statistics. The text mentions "median log2FCH2K" but does not describe the spread or variability.
- **Required correction** Expand the figure legend to clearly describe what is plotted (e.g., box plots, scatter plots), the number of replicates, and the statistical test used for any comparisons.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "R1-MPRA model training"
- **Evidence pointer** Methods section
- **Issue** The model architecture is described, but the exact hyperparameters (e.g., learning rate schedule, dropout rate, number of training epochs) are not fully specified. The grid search approach is mentioned, but the search space is not defined.
- **Required correction** Provide a table or detailed text listing all hyperparameters and the grid search ranges. This is essential for reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section "Comparing sublibraries of synthetic enhancers suggests optimal design practices"
- **Evidence pointer** Results section
- **Issue** The comparison of design methods (DENs, Fast SeqProp, Simulated Annealing) reports p-values for some comparisons but not others. The text states "no significant differences were observed" without reporting the test or the p-value.
- **Required correction** Report the statistical test used and the p-values for all comparisons, including non-significant ones. If multiple comparisons were made, state whether any correction was applied.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section "Designed sequences evolve a more compact TFBS motif grammar"
- **Evidence pointer** Results section; Figure 2A
- **Issue** The claim that "motif density increased significantly over successive design rounds" is made, but the text does not specify whether this is a comparison of means, medians, or distributions. The relationship between motif density and specificity is described as "positively associated," but the strength of this association is not quantified.
- **Required correction** Report the statistical test used for the density comparison and the correlation coefficient (e.g., Spearman's rho) for the association with specificity.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Shorter enhancers display high specificity"
- **Evidence pointer** Results section; Figure 4
- **Issue** The text states that 25 bp enhancers show a significant decrease in specificity, but it is not clear whether this is a decrease relative to 50 bp, 72 bp, or 145 bp enhancers. The text also does not report the number of enhancers tested at each length.
- **Required correction** Clarify the comparison groups and report the sample sizes for each length. Also, report the effect size of the decrease.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Batch correction across design rounds"
- **Evidence pointer** Methods section
- **Issue** The batch correction procedure is described, but the rationale for using weighted linear regression is not explained. It is also unclear how the weights (SER12+SER22) were calculated.
- **Required correction** Provide a brief justification for the method and define the weights.

## Risk / unsupported claims
- The claim that the approach is "readily adapted" to in vivo settings is not supported by the data presented, which is limited to two cell lines and plasmid-based reporters.
- The claim that scMPRA correlations demonstrate a causal relationship between TF expression and enhancer activity is not fully supported, as the analysis does not control for confounding factors.
- The claim of "dramatic" improvement from iterative retraining is based on comparisons of extreme values (best enhancers) and may overstate the effect.
- The statement that "enhancers as short as 50bp can maintain specificity" is supported, but the claim that this is due to "condensed sequence grammar" is an interpretation that is not directly tested.
- The generalizability of the findings to other cell types, particularly those without strong master regulators like TP53 in HepG2, is not established.