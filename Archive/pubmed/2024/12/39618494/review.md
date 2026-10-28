## Review setup
- **Input scope** Full manuscript text (iScience, 2024)
- **Assessment boundary** Scientific claims, methodology, validation, and interpretation as presented in the provided text
- **Shared manuscript claim summary** The authors propose a "unified-field theory" of genome organization and gene regulation, arguing that transcription initiation frequency is determined primarily by the 3D proximity of promoters to clusters of transcription factors and RNA polymerases ("transcription factories"). They derive a simple, fitting-free "looping formula" with a single variable (genomic distance to the nearest active promoter) and claim it predicts transcriptional activity of all promoters in three human cell types, performing comparably to RNA-seq and 3D polymer simulations.
- **Visible evidence base** Main text, Methods (STAR Methods), Figures 1–6 (described), Figure S1–S9 (referenced), Supplemental Videos (referenced)
- **Missing materials affecting confidence** Raw data files, full figure panels, supplemental figures S1–S9, video files, code repository contents, detailed parameter tables for simulations, and complete statistical outputs were not accessible in the provided material.

## Reviewer

- **Overall assessment** This manuscript presents an ambitious and intellectually stimulating attempt to unify genome organization and gene regulation under a single parsimonious framework. The core idea—that transcription rate is governed by 3D proximity to factor-rich clusters—is not new, but the authors' specific formulation of a one-variable "looping formula" and its systematic comparison against experimental data and simulations is a valuable contribution. The writing is clear and the conceptual framing (reconciling Yamanaka and GWAS perspectives) is compelling. However, the manuscript's central claim—that this formula can "predict" transcriptional activity genome-wide—is only partially supported by the evidence presented. The correlations with GRO-seq data (Spearman ~0.6) are modest, and the comparison against RNA-seq is not consistently favorable. The theoretical derivation rests on several simplifying assumptions (e.g., equal affinities, neglect of trans contacts) whose impact on predictive accuracy is not fully explored. The manuscript would be strengthened by a more critical discussion of the formula's limitations, additional validation across more cell types and conditions, and a clearer articulation of what "prediction" means in this context versus descriptive correlation.

- **Who would be interested in the results, and why** Researchers in gene regulation, chromatin organization, and computational biology would find this work of interest. The proposed formula offers a remarkably simple heuristic for estimating promoter activity from genomic distance alone, which could be useful for hypothesis generation and for interpreting genome-wide datasets. The conceptual reconciliation of "simple" (Yamanaka) and "complex" (GWAS) views of regulation is also of broad interest to the transcription field. The paper may also appeal to physicists and modelers interested in polymer physics approaches to biology.

- **Major strengths**
  1. **Conceptual clarity and ambition**: The manuscript tackles a fundamental question—what determines transcription rate—and offers a unified, testable framework.
  2. **Parsimony**: The one-variable formula is elegant and contrasts favorably with complex, data-hungry machine-learning approaches.
  3. **Multi-method validation**: The authors compare their formula against both experimental data (GRO-seq, RNA-seq) and 3D polymer simulations, providing a multi-pronged assessment.
  4. **Biological plausibility**: The model is grounded in the well-documented phenomenon of transcription factories and the observed clustering of active loci.
  5. **Accessibility**: The writing is generally clear, and the use of Feynman-like diagrams to explain the dominant interaction terms is a helpful pedagogical device.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for central claim
- **Claim pointer** "This simple fitting-free formula contains just one variable (distance on the genetic map to the nearest active promoter), and we suggest it can in principle be applied to any organism." (Summary); "we went on to develop two variants of a simple looping formula that enable prediction of the probability that any promoter (whether genic or non-genic) is transcribed." (Discussion)
- **Evidence pointer** Figures 4, 5, 6; Results section "Testing performance of looping formulae: Comparison with GRO-seq data" and "Predicting transcription genome-wide in different cell types"
- **Concern** The central claim of "prediction" is supported by Spearman correlations of approximately 0.6 between formula ranks and GRO-seq ranks. While statistically significant, this level of correlation indicates that a substantial fraction of variance (roughly 64%) is unexplained. The manuscript does not adequately address what this residual variance represents or whether the formula's predictive power is sufficient for practical applications. Furthermore, the comparison with RNA-seq is inconsistent: the formula outperforms RNA-seq in HUVECs but is outperformed by it in GM12878 and H1-hESC (Figure 5B). This inconsistency is acknowledged but not explained mechanistically. The claim that the formula "can in principle be applied to any organism" is speculative, as only human data are tested.
- **Why it matters** The manuscript's primary contribution is the claim of a simple, generalizable predictor of transcriptional activity. If the predictive power is modest and inconsistent across cell types, the practical utility and the strength of the central claim are diminished. The reader needs a clearer understanding of the formula's limitations and the conditions under which it can be expected to perform well.
- **Resolution test** The authors should provide a more nuanced discussion of the correlation values, including an analysis of where the formula fails (e.g., which promoters are poorly predicted and why). They should also test the formula on additional cell types and, ideally, on non-human species to substantiate the generality claim. A head-to-head comparison with a simple baseline (e.g., distance to any active promoter, not just the nearest) would help establish the specific contribution of the "nearest" assumption.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Theoretical derivation and assumptions
- **Claim pointer** "The two terms in this approximate formula capture interaction in these two Feynman-like diagrams (see STAR Methods for a derivation): ptrans(r)∼b(1+cl(r))" (Results)
- **Evidence pointer** STAR Methods section "A looping formula relating initiation rate to distance from an appropriate factory"; Figure 3C
- **Concern** The derivation of the formula is presented in a condensed form in the STAR Methods, and the key assumptions are not fully scrutinized. Specifically: (1) The model assumes all active promoters have identical affinity for the factory in the 1-state model, which is acknowledged to be unrealistic and is partially addressed in the 3-state model. However, the 3-state model still assumes a single "nearest genic promoter" dominates the looping contribution, neglecting the potential additive or competitive effects of multiple nearby promoters. (2) The formula neglects trans contacts entirely, yet the authors acknowledge that trans contacts are abundant and functionally relevant. (3) The derivation appears to assume a single factory type, whereas the authors' own simulations and the broader literature suggest multiple, specialized factories exist. The impact of these simplifications on the formula's accuracy is not systematically explored.
- **Why it matters** The theoretical foundation of the formula is critical to its credibility. If the derivation relies on assumptions that are known to be violated in real cells, the reader needs to understand why the formula still works (or to what extent its success is coincidental). A more rigorous sensitivity analysis would strengthen the theoretical contribution.
- **Resolution test** The authors should expand the derivation in the Methods, explicitly stating each assumption and its justification. They should also perform a sensitivity analysis, e.g., by testing the formula's performance when the "nearest promoter" is replaced by "any promoter within a window" or when trans contacts are included in an approximate manner. This would clarify the robustness of the formula to its key assumptions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Comparison with simulations
- **Claim pointer** "Both 1- and 3-state polymer simulations lead to activity patterns down chromosomes that match those seen by GRO-seq (Figure 6C). Both also yield Spearman correlations that correlate well with those given by formulae across the activity range (Figure 6D)." (Results)
- **Evidence pointer** Figure 6; STAR Methods section "Polymer physics modeling"
- **Concern** The comparison between formula predictions and polymer simulation results is presented as a validation, but the logic is somewhat circular. The polymer simulations are themselves based on the same underlying model (attraction of TFs to promoters, clustering, looping), so it is not surprising that the formula, derived from the same model, agrees with the simulations. This agreement demonstrates internal consistency but does not independently validate the model against reality. The only independent validation is the comparison with GRO-seq data, which shows modest correlations. The manuscript would benefit from a clearer distinction between "internal consistency" (formula vs. simulation) and "external validation" (formula vs. experiment).
- **Why it matters** The reader needs to understand what the simulation comparison actually demonstrates. If it is presented as independent validation, this would be misleading. Clarifying the role of the simulations would strengthen the paper's scientific rigor.
- **Resolution test** The authors should explicitly state that the formula and simulations share the same underlying model, and that the simulation comparison serves as a consistency check. They should also discuss what additional insights the simulations provide beyond the formula (e.g., spatial distribution of clusters, dynamics of looping) that could inform future model refinements.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and scope
- **Claim pointer** "we suggest it can in principle be applied to any organism" (Summary); "they are general in that they can be applied in any organism" (Discussion)
- **Evidence pointer** Discussion; Limitations section
- **Concern** The claim of generalizability to any organism is not supported by evidence. The formula is tested only in three human cell types. The model relies on the existence of transcription factories and the specific scaling of looping probability with genomic distance (fractal globule), which may not hold in organisms with different genome architectures (e.g., bacteria with circular chromosomes, organisms with different chromatin compaction). The authors acknowledge this in the Limitations but do not temper the generalizability claim in the Summary and Discussion accordingly.
- **Why it matters** Overstating the scope of the findings could mislead readers into applying the formula in contexts where it is not valid. A more cautious framing would be scientifically more appropriate.
- **Resolution test** The authors should revise the Summary and Discussion to state that the formula is proposed for organisms with similar genome organization to humans, and that testing in other organisms is a future direction. They could also discuss what minimal data would be needed to adapt the formula to a new organism.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** "unified-field theory" (Title, Summary)
- **Evidence pointer** Title; Summary
- **Issue** The term "unified-field theory" is borrowed from physics and may be seen as overclaiming. While the authors use it metaphorically, it could be misinterpreted as implying a more fundamental unification than is actually achieved.
- **Required correction** Consider using a more modest term, such as "a unifying framework" or "a parsimonious model," to avoid potential misinterpretation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Spearman correlations
- **Evidence pointer** Figures 4, 5, 6; Results
- **Issue** The manuscript reports Spearman correlation coefficients but does not provide confidence intervals or p-values for all comparisons (p-values are mentioned for Figure 5 but not for Figures 4 and 6). The number of promoters used in each correlation is also not stated.
- **Required correction** Provide confidence intervals and p-values for all reported correlations, and state the number of data points (promoters) used in each analysis.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Parameter sensitivity
- **Affected element** Constants b and c
- **Evidence pointer** Results; STAR Methods
- **Issue** The manuscript states that the formula's performance is insensitive to the exact values of b and c, but the supporting analysis is only referenced (Figure S7) and not described in the main text.
- **Required correction** Briefly describe the sensitivity analysis in the main text or Results section, stating the range of values tested and the resulting range of Spearman correlations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Comparison with existing models
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The manuscript does not compare the formula's performance with other predictive models, such as the omnigenic model or machine-learning approaches like Enformer, beyond a brief mention in the Introduction.
- **Required correction** Add a brief comparison in the Discussion, noting how the formula's simplicity and performance compare with these alternative approaches, and under what conditions each might be preferred.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Code and data repository
- **Evidence pointer** Data and code availability section
- **Issue** The repository link is provided, but the contents are not described in detail. It is unclear whether the code for the formula, the simulation scripts, and the processed data are all included and documented.
- **Required correction** Provide a brief description of the repository contents and ensure that all code and data needed to reproduce the main results are included and documented.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 4, 5, 6
- **Evidence pointer** Figures 4, 5, 6 (described)
- **Issue** The figure descriptions suggest that some panels may be dense or difficult to read, particularly the heatmaps in Figures 4C and 6D.
- **Required correction** Ensure that all figure panels are legible at publication size, with clear labels and legends. Consider enlarging key panels or providing higher-resolution versions.

## Risk / unsupported claims
- The claim that the formula "can in principle be applied to any organism" is unsupported, as only human data are tested.
- The claim that the formula "performs as well as RNA-seq" is only true for HUVECs; in the other two cell types, RNA-seq outperforms the formula. This inconsistency is not fully explained.
- The statement that the model "reconciles" the Yamanaka and GWAS views is presented as a conceptual argument, not a quantitative demonstration. The reconciliation is plausible but not rigorously tested.
- The claim that the formula is "fitting-free" is technically correct, but the values of b and c are chosen based on experimental data (e.g., average loop length from HeLa cells), which introduces a degree of calibration.
- The biological interpretation of the "nearest active promoter" as the dominant looping partner is an assumption that is not directly tested against experimental data on promoter-promoter interactions.