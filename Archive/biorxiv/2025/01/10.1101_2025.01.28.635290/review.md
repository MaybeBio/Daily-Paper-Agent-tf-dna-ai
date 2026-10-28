## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific and technical evaluation of the described method, its validation, and the claims made; no evaluation of code functionality beyond what is described
- **Shared manuscript claim summary** The authors present ShapeME, a unified workflow for de novo discovery of short DNA structural motifs (shape motifs) that can utilize diverse data types (binary, categorical, continuous) and integrates sequence motif inference via STREME, with model selection via CAMI-based pruning and LASSO regression. They claim ShapeME outperforms the alternative tool ShapeMotifEM on ENCODE ChIP-seq benchmarks, and demonstrate its utility on bacterial (H-NS) and human (29 TFs) datasets, as well as an RNA-seq-based application suggesting a regulatory hierarchy involving JunD and SP5.
- **Visible evidence base** Abstract; Introduction; Results sections (DNA shape landscape, synthetic benchmarks, H-NS analysis, ENCODE 29 TF analysis, ShapeMotifEM comparison, JunD RNA-seq analysis); Discussion; Methods (algorithm description, data processing, statistical approaches); Figure legends referenced but figures not fully visible in provided text
- **Missing materials affecting confidence** Figures and supplementary figures are referenced but not provided in full; exact numerical results for many comparisons are not given in the text; details of the ShapeMotifEM comparison methodology are incomplete; the RNA-seq analysis lacks statistical detail; no information on runtime or computational cost

## Reviewer
- **Overall assessment** This manuscript presents a timely and potentially valuable tool for de novo discovery of DNA structural motifs. The methodological framework is well-conceived, combining information-theoretic motif discovery with DNAshapeR-derived shape features and integrating sequence motif inference. The synthetic benchmarks are encouraging, and the application to diverse biological datasets demonstrates versatility. However, several technical concerns must be addressed, particularly regarding the statistical rigor of the biological comparisons, the completeness of the ShapeMotifEM benchmarking, and the interpretability of the RNA-seq-based findings. The manuscript would benefit from clearer presentation of quantitative results and more thorough validation of the claimed advantages.

- **Who would be interested in the results, and why** Researchers studying transcriptional regulation, particularly those interested in DNA shape as a determinant of protein-DNA binding specificity. The tool will be of interest to computational biologists developing motif discovery methods, as well as experimentalists seeking to interpret ChIP-seq, SELEX, or RNA-seq data in terms of structural DNA features. The web interface and containerized distribution lower the barrier for adoption by non-specialists.

- **Major strengths**
  1. The method addresses a genuine gap: de novo discovery of structural motifs without anchoring to sequence motifs, applicable to diverse data types.
  2. The integration of shape and sequence motif inference with principled model selection (CAMI + LASSO) is a thoughtful design.
  3. The synthetic benchmarks provide evidence of the method's ability to recover known motifs.
  4. The application to H-NS is biologically meaningful and connects structural features to a well-studied protein.
  5. The RNA-seq application demonstrates the method's flexibility beyond ChIP-seq data.
  6. The tool is distributed with a web interface and open-source code, enhancing accessibility and reproducibility.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor of biological comparisons
- **Claim pointer** The claim that "shape motifs identified by the shape-based component of ShapeME often outperform both sequence motifs arrived at by STREME alone and the best PWM for that protein at the JASPAR database" (Abstract and Introduction)
- **Evidence pointer** Results section "Shape motifs are often complementary to, and sometimes outperform, sequence motifs in biological datasets"; Figure 4; Supplementary Figure 2
- **Concern** The manuscript reports that in 11 of 29 cases shape motifs outperformed sequence motifs, in 12 cases sequence outperformed shape, and in 15 cases combined models were best. However, the statistical significance of these differences is not reported. It is unclear whether "outperform" means a statistically significant improvement in cross-validated AUPR, or simply a numerically higher value. The threshold for significance (e.g., a minimum AUPR difference) is not defined. Furthermore, the comparison to JASPAR motifs is potentially confounded: JASPAR motifs are derived from curated databases and may not be optimized for the specific cell types or conditions of the ENCODE datasets used.
- **Why it matters** Without statistical significance testing, the reader cannot assess whether the observed differences are meaningful or within the range of cross-validation noise. The claim of "often outperform" is central to the paper's thesis and must be supported by rigorous statistical evidence.
- **Resolution test** Provide confidence intervals or significance tests (e.g., paired tests across folds) for the AUPR comparisons. Define a priori criteria for what constitutes "outperformance." Consider using a null model or permutation test to establish a baseline for AUPR differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Completeness of benchmarking against ShapeMotifEM
- **Claim pointer** "ShapeME motifs outperform motifs returned by ShapeMotifEM in all cases that ShapeMotifEM was able to run to completion" (Results section "ShapeME outperforms the alternative shape motif inference tool ShapeMotifEM")
- **Evidence pointer** Results section "ShapeME outperforms the alternative shape motif inference tool ShapeMotifEM"; Figure 5
- **Concern** The comparison to ShapeMotifEM is described only briefly. Key details are missing: (1) How many of the 29 datasets did ShapeMotifEM fail on, and why? (2) What were the exact AUPR values for both methods across all datasets? (3) Was ShapeMotifEM run with its default parameters, or were parameters tuned? (4) The statement that ShapeME "outperforms" in all cases where ShapeMotifEM completed is strong, but the magnitude of the improvement is not reported. (5) The claim that ShapeMotifEM "crashed" in 59% of cases is concerning but not contextualized; was this due to resource limits, numerical issues, or input format problems?
- **Why it matters** A fair and complete benchmark is essential to substantiate the claim of superiority over the state of the art. Incomplete reporting of failures and missing quantitative comparisons undermines confidence in the conclusion.
- **Resolution test** Provide a table with AUPR values for both methods on all 29 datasets, including cases where ShapeMotifEM failed. Report the failure modes and whether any attempts were made to resolve them. Discuss whether the comparison is fair given potential differences in parameter settings or input requirements.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability and validation of RNA-seq-based findings
- **Claim pointer** The suggestion that the shape motif identified from JunD knockdown RNA-seq data may reflect SP5 activity, and the proposed regulatory hierarchy involving JunD and SP5
- **Evidence pointer** Results section "ShapeME run on RNA-seq results reveals potential regulatory hierarchy of JunD"; Figure 6
- **Concern** The RNA-seq analysis is intriguing but the evidence linking the identified shape motif to SP5 is indirect. The authors use ShapeIT to identify motif instances, then MEME to find sequence motifs in the underlying sequences, and then TomTom to match to SP5. Each step introduces potential noise. The statistical significance of the TomTom match is not reported. The claim that the motif "could be an SP5 motif" is speculative, and the authors acknowledge that experimental validation is required. However, the presentation in the Results section may overstate the strength of the evidence.
- **Why it matters** The RNA-seq application is presented as a demonstration of the method's versatility, but if the biological interpretation is not well-supported, it may mislead readers into overinterpreting the results.
- **Resolution test** Report the TomTom match statistics (e.g., p-value, q-value) for the SP5 match. Consider additional validation, such as comparing the identified shape motif to shape profiles of known SP5 binding sites, or testing whether the motif is enriched in SP5 ChIP-seq peaks (which the authors do, but the results are not quantified in the text).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and parameter sensitivity
- **Claim pointer** The claim that ShapeME is "capable of utilizing virtually any type of data representing sequence coverage or enrichment" (Abstract)
- **Evidence pointer** Methods section "ShapeME input data and arguments of note"
- **Concern** The method's flexibility is a key selling point, but the manuscript does not systematically explore how performance varies with key parameters (e.g., motif length k, number of quantiles q, maximum hits per strand, batch size, number of batches). The synthetic benchmarks use specific parameter choices, and it is unclear how sensitive the results are to these choices. Additionally, the method's performance on data types other than ChIP-seq (e.g., RNA-seq with continuous scores) is only demonstrated in one case study.
- **Why it matters** Users need guidance on parameter selection and an understanding of the method's robustness. If performance is highly sensitive to parameters, the tool's utility is diminished.
- **Resolution test** Provide a parameter sensitivity analysis on at least one synthetic and one biological dataset. Offer practical guidance on parameter selection in the documentation or manuscript.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figure 1
- **Evidence pointer** Results section "DNA shapes provide a distinct landscape from DNA sequences"
- **Issue** The description of Figure 1B-C is qualitative ("Qualitative assessment of all pairwise edit... distances revealed a dramatically different landscape"). The figure itself is not provided in the manuscript text, making it difficult to assess the claim.
- **Required correction** Provide a more quantitative description of the differences between sequence and shape distance landscapes, and ensure the figure is clearly labeled and legible.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical detail in synthetic benchmarks
- **Affected element** Results section "ShapeME correctly identifies shape motifs in synthetic datasets"
- **Evidence pointer** Figure 2
- **Issue** The synthetic benchmark results are reported as AUPR values, but the variability across the 5 folds is not reported for all cases. For example, the statement "The lowest AUPR for any fold of any of the five categories was 0.96" is useful, but the distribution of AUPRs across folds is not shown.
- **Required correction** Report mean and standard deviation (or range) of AUPR across folds for each synthetic benchmark.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity of the "both" mode description
- **Affected element** Methods section "General Description of the Algorithm"
- **Evidence pointer** Methods, step 3c
- **Issue** The description of how shape and sequence motifs are merged and subjected to a final LASSO regression is somewhat terse. It is unclear how the design matrix is constructed when both motif types are present, and how the final model selection handles potential interactions between shape and sequence motifs.
- **Required correction** Expand the description of the merging and final model selection steps, possibly with a small illustrative example.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Accessibility of the web interface
- **Affected element** Abstract and Introduction
- **Evidence pointer** URL provided in Abstract
- **Issue** The web interface URL is provided, but there is no information on usage limits, data privacy, or whether the interface supports all features of the command-line tool.
- **Required correction** Add a brief description of the web interface's capabilities and any limitations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Comparison to existing tools
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 2
- **Issue** The introduction mentions that "only a few approaches have been developed for the de novo discovery of short motifs in DNA shape information" but does not provide a detailed comparison of these approaches and their limitations. This makes it difficult to position ShapeME's novelty.
- **Required correction** Briefly describe the existing approaches and explicitly state what ShapeME adds beyond them.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of statistical significance testing for the central claim of outperformance.
  - R1-M2: Incomplete reporting of the ShapeMotifEM comparison, including failure cases and quantitative results.
  - R1-M3: Insufficient statistical support for the SP5-related interpretation of the RNA-seq analysis.
  - R1-M4: No parameter sensitivity analysis to support the claim of general applicability.

- **Assessment against Nature-style criteria**
  - **Originality** The concept of de novo shape motif discovery without sequence anchoring is a meaningful advance over existing approaches that require a sequence motif seed. The integration of shape and sequence motifs in a unified framework with principled model selection is novel. However, the underlying information-theoretic approach is inspired by existing methods (e.g., FIRE), and the novelty lies primarily in the application to shape features and the unified workflow.
  - **Scientific importance** Understanding the structural determinants of protein-DNA binding is of broad importance in gene regulation. A tool that can discover such determinants from diverse data types has the potential to be widely used. The demonstration that shape motifs can outperform sequence motifs for some TFs is an important finding that challenges the primacy of sequence-based models.
  - **Interdisciplinary readership** The work bridges computational biology, biophysics, and molecular biology. The web interface and clear documentation could make it accessible to experimentalists. However, the manuscript's technical depth may limit its readability for non-specialists in the methods sections.
  - **Technical soundness** The algorithmic design is sound, and the synthetic benchmarks provide evidence of correct implementation. However, the statistical rigor of the biological comparisons is insufficient, and the benchmarking against ShapeMotifEM is incomplete. These issues must be resolved to establish technical soundness.
  - **Readability for nonspecialists** The abstract and introduction are clear and accessible. The results sections are generally readable, but the methods section is dense and assumes familiarity with information theory and regression techniques. The figures, if well-designed, could aid comprehension, but they are not fully visible in the provided text.

- **Recommendation posture** Supportive if technical concerns are resolved. The method addresses a real need and shows promise, but the central claims require stronger statistical support and more complete benchmarking. The RNA-seq application, while interesting, needs more careful interpretation. With these revisions, the manuscript could make a valuable contribution to the field.