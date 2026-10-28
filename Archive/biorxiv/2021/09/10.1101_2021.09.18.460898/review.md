## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results and Discussion, Summary and Conclusions, Materials and Methods, and supplementary table/figure references)
- **Assessment boundary** Scientific claims, methodology, data interpretation, and internal consistency based solely on the provided text. No external literature or unpublished data were consulted.
- **Shared manuscript claim summary** The authors propose that the intrinsic torsional flexibility of p53 response elements (REs), quantified by the deformability parameter V(B), is a key determinant of the timing and level of p53-dependent gene activation. They classify 211 p53 target genes into functional categories, show that genes involved in early stress responses have more flexible REs than those involved in later or strictly regulated processes, and support this with cyclization kinetics measurements and reporter gene assays.
- **Visible evidence base** Abstract, full Introduction, Results and Discussion sections (including Figure 1, Figure 2, Figure 3, Figure 4, Figure 5 references), Summary and Conclusions, Materials and Methods, and references to Tables S1-S5 and Figures S1-S4.
- **Missing materials affecting confidence** The actual figures and tables (Figures 1-5, Tables 1-2, S1-S5) are not provided. Specific numerical data for cyclization kinetics, reporter assay values, and statistical outputs are therefore not directly verifiable. The Hafner et al. dataset is referenced but not described in detail.

## Reviewer
- **Overall assessment** This manuscript addresses a significant and timely question in the p53 field: the mechanistic basis for the orderly activation of p53 target genes. The central hypothesis, that DNA torsional flexibility of REs contributes to functional selectivity, is well-motivated by the authors' prior work and is conceptually appealing. The computational classification of REs by functional category and the correlation with calculated flexibility is a valuable contribution. However, the strength of the conclusions is currently limited by the lack of direct presentation of the key data (figures and tables) in the provided material, and by the reliance on a single, albeit rigorous, biophysical parameter. The experimental validation is promising but is based on a small number of REs. The manuscript is well-written and the logic is clear, but the evidence as presented is not fully sufficient to establish the broad claim that DNA flexibility is a primary driver of cell-fate decisions in the p53 network.
- **Who would be interested in the results, and why** Researchers in the fields of p53 biology, gene regulation, biophysics of protein-DNA interactions, and systems biology. The work is relevant to those studying how transcription factor binding site sequence and structure encode information beyond simple affinity, and to those interested in the mechanisms of cell-fate decisions in response to stress.
- **Major strengths**
    1.  The hypothesis is novel and builds logically on the authors' previous findings, proposing a mechanistic link between a physical property of DNA (torsional flexibility) and the temporal dynamics of gene expression.
    2.  The study integrates computational analysis (deformability calculations, functional classification) with experimental validation (cyclization kinetics, reporter assays), providing a multi-pronged approach.
    3.  The use of a curated set of validated p53 target genes and the careful consideration of RE clusters and spacer sequences demonstrates methodological rigor.
    4.  The analysis of published RNA-seq data (Hafner et al.) provides an independent, albeit preliminary, test of the hypothesis in a more natural context.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The claim that genes in the "flexible REs category" (early DDR, innate immunity, development, energy metabolism) are activated early and at low p53 levels, while those in the "rigid REs category" (intrinsic apoptosis, p53 negative regulation) are activated later or require higher p53 levels, is central to the paper.
- **Evidence pointer** Figure 1, Figure 3, Figure 5, Table 1, Table 2
- **Concern** The core evidence for this claim is presented in figures and tables that are not included in the provided manuscript text. The statistical analysis (F = 19.71, P < 0.0001) is mentioned, but the actual distribution of deformability values, the post-hoc test results, and the specific data points for the reporter assays are not visible. Without these data, it is impossible to assess the magnitude of the differences, the overlap between groups, or the strength of the correlations. The claim that transactivation from flexible REs occurs at lower p53 levels and faster rates is based on Figure 3, which is not available for review.
- **Why it matters** The entire thesis of the paper rests on the validity and strength of these correlations. The reader cannot evaluate whether the differences are robust, whether there are outliers, or whether the effect sizes are biologically meaningful without seeing the primary data.
- **Resolution test** The authors must provide the actual figures and tables, along with the specific statistical outputs (e.g., effect sizes, confidence intervals, post-hoc p-values) for the deformability comparisons and the reporter assay time-course and dose-response experiments.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Experimental validation scope
- **Claim pointer** The claim that "the global structural properties of several p53 REs belonging to the different pathways were experimentally validated" and that this supports the computational predictions.
- **Evidence pointer** Table 2, Figure S1
- **Concern** The experimental validation of DNA flexibility is performed on only five REs. While this is a reasonable starting point, it is a very small sample size to validate a computational parameter that is then used to classify over 200 REs. The selection criteria for these five REs are not explicitly stated, and it is unclear if they are representative of the full range of flexibility values or if they were chosen to maximize the contrast between categories.
- **Why it matters** The predictive power of the V(B) parameter for functional classification depends on its accuracy across a wide range of sequences. Validation on a small, potentially biased subset weakens the generalizability of the findings.
- **Resolution test** The authors should justify the choice of the five REs, ideally showing they span the range of calculated flexibilities. If possible, expanding the experimental validation to a larger, more diverse set of REs would significantly strengthen the case.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Alternative explanations
- **Claim pointer** The claim that DNA flexibility is a key factor in determining p53 functional outcome, implying a direct causal link.
- **Evidence pointer** Figure 3, Figure 5, Discussion
- **Concern** The manuscript does not adequately address alternative explanations for the observed correlation between RE flexibility and gene expression timing. For example, the sequence composition that confers flexibility (e.g., AT-richness) may also affect the binding of other transcription factors, nucleosome positioning, or the local chromatin environment. The authors acknowledge that other factors are at play, but the discussion does not deeply explore how the proposed mechanism might integrate with these other layers of regulation. The analysis of the Hafner et al. data is correlative and does not establish causality.
- **Why it matters** The field is aware that p53 target gene selection is complex. To make a strong claim for the importance of DNA flexibility, the authors need to demonstrate that this parameter provides explanatory power beyond what is already known about p53 binding affinity or chromatin state.
- **Resolution test** The authors should discuss and, if possible, provide preliminary analyses that control for other known determinants of p53 target gene activation, such as binding affinity, chromatin accessibility, or the presence of co-factor binding sites.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor of functional classification
- **Claim pointer** The classification of 211 genes into functional supergroups and the subsequent analysis of deformability differences between these groups.
- **Evidence pointer** Table 1, Table S1, Table S2, Figure 1
- **Concern** The functional classification is a critical step, but the process appears to be largely manual and based on literature curation. The criteria for grouping specific biological processes into supergroups (e.g., "Cytoskeleton/cell migration") are described, but the potential for subjectivity and misclassification is a concern. The assignment of genes with multiple functions (e.g., PRDM1, PTP4A1, XPC) to a single category is a simplification that could influence the results. The statistical analysis treats these groups as independent, but the classification itself is a source of uncertainty.
- **Why it matters** If the classification is biased or inconsistent, the observed differences in deformability between groups could be an artifact of the classification scheme rather than a true biological phenomenon.
- **Resolution test** The authors should provide a more detailed and transparent description of the classification process, perhaps including a table showing the evidence for each gene's assignment. A sensitivity analysis, where genes with ambiguous functions are re-assigned or excluded, would help demonstrate the robustness of the findings.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and reproducibility
- **Affected element** Materials and Methods, "Cyclization kinetics and simulation of cyclization data"
- **Evidence pointer** Materials and Methods section
- **Issue** The description of the cyclization kinetics method is brief and refers to previous work. While this is acceptable, the specific parameters for the current experiments (e.g., ligase concentrations, DNA lengths, simulation details) are only partially given. The exact sequences of the test constructs are in Table S5, which is not provided.
- **Required correction** Ensure that the provided Table S5 and Figure S1 contain all necessary details for a reader to reproduce the experiments and simulations without referring to multiple prior publications.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 5
- **Evidence pointer** Figure 5, Footnotes
- **Issue** The footnote states "Figure 5 has been replaced" but no replacement is described. This is confusing and suggests the manuscript is incomplete.
- **Required correction** Clarify the status of Figure 5. If it has been replaced, describe the new figure in the text and ensure the legend is updated.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of results
- **Affected element** Discussion of intermediate flexibility groups
- **Evidence pointer** Results and Discussion, Figure 1
- **Concern** The authors focus on the extreme categories (flexible vs. rigid) and note that some groups have "median flexibility" (e.g., lipid metabolism, extrinsic apoptosis). The interpretation of these intermediate groups is somewhat speculative.
- **Required correction** Provide a more explicit discussion of what the intermediate flexibility might mean functionally. Does it represent a graded response, a mixed population of REs, or a different regulatory logic?

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Statistical tests
- **Evidence pointer** Materials and Methods, "Other computational and statistical tests"
- **Issue** The methods state that ANOVA and post-hoc tests were used, but the specific results (e.g., F-statistics, p-values for all comparisons) are only partially reported in the text. The full statistical details are presumably in Table S3.
- **Required correction** Ensure that Table S3 is comprehensive and includes all pairwise comparisons, effect sizes, and confidence intervals, not just p-values.

## Risk / unsupported claims
- The claim that DNA flexibility is a "key factor" in determining cell-fate decisions is not fully supported by the evidence presented, as the primary data (figures and tables) are missing and the analysis is largely correlative.
- The claim that the five experimentally validated REs are representative of the broader categories is not established.
- The interpretation of the Hafner et al. RNA-seq data is based on a small subset of genes (18 of 32) and is presented as supportive, but the analysis is not described in sufficient detail to assess its validity.
- The statement that "the REs base sequences are information-rich by virtue of their structural properties" is a strong conclusion that goes beyond the data presented, which shows a correlation but not a proven mechanism.