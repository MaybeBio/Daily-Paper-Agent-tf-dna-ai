## Review setup
- **Input scope** Full manuscript text, including abstract, main text, figures (descriptions only), and supplementary file descriptions.
- **Assessment boundary** Scientific content, methodological rigor, statistical validity, and interpretation of results as presented. No assessment of formatting, language style, or editorial fit.
- **Shared manuscript claim summary** The authors present an in-silico analysis of HPV E1 protein conservation and E1-E2 interface thermodynamics, claiming that predicted binding energy differences correlate with clinical risk groups (high-risk vs low-risk HPV types), with high-risk types exhibiting weaker E1-E2 interfaces. They further claim this distinction is specific to the E1-E2 interface, not the E1-E1 hexamer, and propose this as a framework for understanding oncogenic potential.
- **Visible evidence base** Main text with 7 figures (described), 2 tables, and 8 supplementary files (described but not provided in full).
- **Missing materials affecting confidence** Supplementary files 1-8 (detailed data, statistical outputs, alignment confidence profiles, per-residue decompositions) were not provided. Raw sequence data, AlphaFold3 model coordinates, and FoldX input/output files were not accessible. Figure images were not viewable, only descriptions.

## Reviewer
- **Overall assessment** This manuscript presents a computationally intensive analysis of HPV E1 conservation and E1-E2 interface thermodynamics, with a potentially interesting observation that predicted binding energies differ between high-risk and low-risk HPV types. The work is timely given the clinical importance of HPV and the growing use of AI-based structural prediction. However, the study has several critical limitations that prevent the conclusions from being fully established. The sample size is small (n=24), the statistical approach is relatively simple for the complexity of the data, and the biological interpretation relies on speculative mechanistic links that are not directly tested. The most significant concern is the potential circularity or confounding in the risk classification, and the lack of experimental validation for any of the predicted thermodynamic differences. The manuscript would benefit from a more nuanced discussion of the limitations of in-silico binding energy predictions and a clearer articulation of what new biological insight is provided beyond the known sequence conservation of E1.

- **Who would be interested in the results, and why** Researchers in the HPV field, particularly those studying viral replication mechanisms and the E1-E2 interaction as a therapeutic target. Computational biologists interested in applying AlphaFold3 and FoldX to protein-protein interaction analysis. Clinically-oriented researchers interested in molecular correlates of HPV oncogenic risk. The work may also be of interest to those developing broad-spectrum antiviral strategies targeting conserved viral enzymes.

- **Major strengths** 
  1. The study addresses an important clinical question (molecular correlates of HPV oncogenic risk) using modern computational tools.
  2. The multi-scale approach (phylogenetics, conservation analysis, structural modeling, thermodynamics) is comprehensive and well-structured.
  3. The authors include important control analyses (E1-E1 hexamer comparison, pH sensitivity, multiple cross-validation schemes) that strengthen the specificity claims.
  4. The acknowledgment of limitations (e.g., computational scores vs. experimental measurements) in the discussion is appropriate.
  5. The identification of specific residues (e.g., E1 Tyr585, Arg589, Lys476) driving the thermodynamic differences provides testable hypotheses.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity and sample size
- **Claim pointer** The authors claim a significant correlation between E1-E2 binding energy and clinical risk group (P < 0.001, AUC = 0.875) based on 24 genotypes.
- **Evidence pointer** Results section "E1-E2 binding energy correlates with clinical risk profiles", Figure 7, Table 1
- **Concern** The analysis is based on only 24 genotypes (12 high-risk, 12 low-risk). This small sample size raises concerns about the stability and generalizability of the logistic regression model. With n=24, the model has limited statistical power, and the confidence intervals for the AUC (0.69-1.00) are extremely wide, indicating substantial uncertainty. The authors do not report any power analysis or justification for the sample size. Additionally, the 24 genotypes are not independent observations in a strict sense, as they share evolutionary history, which could inflate the apparent significance of the association.
- **Why it matters** The central claim of the paper, that E1-E2 binding energy correlates with clinical risk, rests entirely on this small dataset. If the result is not robust to the inclusion of additional genotypes or to phylogenetic correction, the main conclusion would be substantially weakened. The wide confidence intervals suggest the effect size is not well-estimated.
- **Resolution test** The authors should provide a power analysis justifying the sample size, perform phylogenetic independent contrasts or a mixed-effects model accounting for evolutionary relatedness, and demonstrate that the result holds when excluding individual genotypes (e.g., jackknife or bootstrap sensitivity analysis). Reporting the AUC with a tighter confidence interval and providing calibration plots would also strengthen the claim.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validity of thermodynamic predictions
- **Claim pointer** The authors use AlphaFold3-generated structures and FoldX to compute binding energies, claiming these distinguish high-risk from low-risk HPV types.
- **Evidence pointer** Methods section "Structural modeling, thermodynamic assessment, and statistical analysis", Table 1
- **Concern** The manuscript does not provide sufficient validation of the computational pipeline. AlphaFold3 is a structure prediction tool, not a docking or binding affinity prediction tool, and its accuracy for predicting the effects of sequence variation on binding affinity is not well-established. FoldX is a knowledge-based potential that has known limitations in predicting absolute binding energies, and its accuracy for this specific protein-protein interface is not demonstrated. The authors do not compare their predicted ΔG values to any experimental binding data for E1-E2 interactions (which exist in the literature for several HPV types). The manuscript also does not report the confidence metrics for the AlphaFold3 predictions beyond a single ipTM value for one complex.
- **Why it matters** The entire thermodynamic framework depends on the accuracy of these computational predictions. If the predicted ΔG values do not correlate with actual binding affinities, then the claimed correlation with clinical risk is meaningless. Without benchmarking against experimental data, the reader cannot assess whether the observed differences are biologically real or computational artifacts.
- **Resolution test** The authors should benchmark their pipeline against experimentally determined E1-E2 binding affinities (e.g., from surface plasmon resonance or isothermal titration calorimetry studies in the literature). They should report per-residue confidence metrics for all AlphaFold3 models, not just one. They should also perform a sensitivity analysis using alternative thermodynamic calculation methods (e.g., MM-PBSA, Rosetta) to show the results are not method-dependent.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Confounding and causal inference
- **Claim pointer** The authors state that "thermodynamic variations at the E1-E2 interface correlate with distinct clinical risk groups" and imply a mechanistic link between weaker binding and oncogenic potential.
- **Evidence pointer** Abstract, Results section "Thermodynamic stability of the E1-E2 interface differentiates risk groups", Discussion
- **Concern** The observed correlation between E1-E2 binding energy and risk group may be confounded by phylogenetic relatedness or by other sequence features that differ between high-risk and low-risk types. The authors do not control for overall sequence divergence, which is known to be greater between high-risk and low-risk types than within groups. The claim that the E1-E2 interface specifically drives oncogenic potential is speculative; the weaker binding could be a consequence of other evolutionary pressures, or the correlation could be driven by a few outlier genotypes. The authors' own sensitivity analysis shows that removing HPV16 and HPV61 changes the model, indicating the result is not robust.
- **Why it matters** The authors make a strong interpretive claim that the E1-E2 interface thermodynamics are "associated with oncogenic potential" and suggest this has implications for understanding carcinogenesis. If the correlation is confounded or driven by outliers, this interpretation is not supported. The clinical relevance of the finding depends on whether the thermodynamic difference is a cause or a consequence of risk group status.
- **Resolution test** The authors should perform a phylogenetic regression or partial correlation analysis controlling for overall sequence divergence. They should also test whether the correlation holds when using a continuous measure of oncogenic potential (e.g., relative risk estimates) rather than a binary high/low classification. A more cautious interpretation of the results as hypothesis-generating rather than mechanistic would also be appropriate.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and transparency
- **Claim pointer** The authors describe a multi-stage computational pipeline but do not provide sufficient detail for replication.
- **Evidence pointer** Methods section, Supplementary file descriptions
- **Concern** The manuscript lacks critical methodological details: (1) The exact version and parameters of AlphaFold3 are not specified. (2) The multiple sequence alignment parameters and the specific sequences used are not fully described. (3) The FoldX protocol (e.g., number of runs, repair steps, temperature) is only partially described. (4) The logistic regression implementation (software, regularization, variable selection) is not detailed. (5) The supplementary files are described but not provided for review. Without these details, the work cannot be independently replicated or verified.
- **Why it matters** Reproducibility is a core requirement for scientific validity, particularly for computational studies where small methodological differences can lead to different results. The inability to replicate the analysis undermines confidence in the findings.
- **Resolution test** The authors should provide a detailed step-by-step protocol, including software versions, parameters, and commands. They should make the sequence alignments, AlphaFold3 models, and FoldX output files publicly available in a repository. The supplementary files should be provided in full for review.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figure 7
- **Evidence pointer** Results section "E1-E2 binding energy correlates with clinical risk profiles"
- **Issue** The description of Figure 7 indicates a logistic regression curve and ROC plot, but the figure itself is not viewable. The authors should ensure that the figure clearly shows individual data points, not just the fitted curve, so readers can assess the distribution of the data and identify potential outliers.
- **Required correction** Provide a version of Figure 7 that includes individual genotype data points overlaid on the logistic regression curve, with genotypes labeled. This will allow readers to assess the influence of individual data points on the model.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Inconsistent reporting of statistical details
- **Affected element** Results section "E1-E2 binding energy correlates with clinical risk profiles"
- **Evidence pointer** Results section, Figure 7
- **Issue** The authors report a p-value of 0.008 for the logistic regression coefficient but do not specify the test used (e.g., Wald test, likelihood ratio test). The permutation test p-value of 0.0010 is reported, but the number of permutations and the exact procedure are not described.
- **Required correction** Specify the statistical tests used for each reported p-value, including the test statistic and degrees of freedom where applicable. Describe the permutation test procedure in detail.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Overstatement of clinical relevance
- **Affected element** Abstract, Conclusions
- **Evidence pointer** Abstract, Conclusions section
- **Issue** The authors state that their findings "provide a framework for understanding functional sites in the E1-E2 complex" and "motivate future experimental validation." While appropriately cautious in places, the abstract's phrasing "correlate with clinical risk groups" could be misinterpreted as implying a clinically validated biomarker. The study is purely computational and based on a small sample.
- **Required correction** In the abstract, explicitly state that this is an in-silico hypothesis-generating study and that the correlation is observed in a limited computational dataset, not a clinically validated association.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Missing discussion of alternative interpretations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The authors interpret the weaker E1-E2 interface in high-risk types as potentially conferring "more rapid transition to active replication states." However, they do not discuss alternative interpretations, such as the possibility that weaker binding could lead to less efficient replication in some contexts, or that the thermodynamic differences could be neutral with respect to function.
- **Required correction** Add a paragraph in the Discussion acknowledging alternative interpretations of the thermodynamic differences and discussing how the proposed hypothesis could be distinguished from alternatives experimentally.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Incomplete description of risk group classification
- **Affected element** Methods section
- **Evidence pointer** Methods section "Structural modeling, thermodynamic assessment, and statistical analysis"
- **Issue** The authors state that 12 high-risk and 12 low-risk types were selected based on IARC classifications, but the specific genotypes in each group are not listed in the main text. The supplementary file 2 is described as containing this information, but it was not provided.
- **Required correction** List the specific HPV genotypes included in each risk group in the main text or a table, so readers can assess the representativeness of the sample.

## Risk / unsupported claims
1. The claim that "thermodynamic variations at the E1-E2 interface correlate with distinct clinical risk groups" is supported only by computational predictions on a small sample (n=24) and is not validated by any experimental binding data. The correlation may be confounded by phylogenetic relatedness.
2. The claim that weaker E1-E2 binding in high-risk types "may confer more rapid transition to active replication states" is purely speculative and not directly tested in this study.
3. The claim that the E1-E2 interface is "thermodynamically distinct between classes of pathogenicity" is based on predicted ΔG values from FoldX, which has known limitations for absolute binding energy prediction. The accuracy of these predictions for this specific system is not demonstrated.
4. The statement that the deep conservation of E1's catalytic core "marks this enzymatic core as a plausible viral target" is reasonable but is a general statement not specifically supported by new data in this study.
5. The claim that the thermodynamic differences are "robust and invariant to physiological protonation states" is based on a single pH comparison (7.0 vs 6.5) and may not capture the full range of physiological conditions.
6. The generalizability of the logistic regression model to unseen HPV genotypes is not established, as the cross-validation was performed on the same small dataset used for model fitting.