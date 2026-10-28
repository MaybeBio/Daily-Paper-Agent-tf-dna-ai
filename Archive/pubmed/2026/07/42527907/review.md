## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and figure/table captions
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and clarity of claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors investigate whether residual-stream geometry in single-cell foundation models (scGPT, Geneformer) carries incremental gene-regulatory signal beyond expression-level confounds, using curated TF-target edges from TRRUST across four tissue contexts from Tabula Sapiens. They report significant incremental predictive value under edge-level cross-validation, robustness to harder negatives and leave-TF-out/leave-target-out splits, collapse under leave-both-out evaluation, and attribute apparent cross-model differences to representation-construction choices.
- **Visible evidence base** Results sections with tables (Tables 1-8), figures (Figures 1-5), methods descriptions, and statistical details (bootstrap CIs, permutation tests, FDR correction)

## Reviewer
- **Overall assessment** This manuscript addresses a timely and important question about the interpretability of single-cell foundation models, specifically whether their internal representations encode regulatory information beyond co-expression. The study is carefully designed with multiple controls and cross-validation schemes, and the authors are appropriately cautious in delimiting the signal's scope. However, several methodological concerns regarding statistical rigor, baseline construction, and generalizability need to be addressed before the claims are fully established. The work is potentially valuable for the computational biology community, but the current evidence base has gaps that limit confidence in the strongest conclusions.
- **Who would be interested in the results, and why** Researchers working on single-cell foundation models, gene regulatory network inference, and representation learning in genomics would be interested. The findings inform whether these models can be used for regulatory edge prioritization and how to extract such signals, which is relevant for both model developers and users in functional genomics. The methodological insights about layer selection and feature construction also have broader applicability to interpretability studies of biological transformers.
- **Major strengths**
  1. The study addresses a novel and important question: whether residual-stream geometry in single-cell foundation models carries regulatory signal beyond expression confounds, which has not been systematically investigated before.
  2. The experimental design is thorough, including multiple geometric metrics, layer analyses, null controls (label permutation, geometry shuffle), and multiple cross-validation schemes (edge-level, leave-TF-out, leave-target-out, leave-both-out).
  3. The authors are commendably honest in reporting negative results and limitations, including the collapse under leave-both-out evaluation and the modest absolute performance.
  4. The cross-model comparison with matched extraction is a strong methodological contribution, demonstrating that apparent differences can be artifacts of representation construction.
  5. The confirmatory rerun on held-out domains with a frozen pipeline is a good practice for avoiding overfitting in exploratory analyses.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that geometric features provide "significant incremental signal" validated by "stringent null controls and multiplicity-corrected across the full grid of comparisons."
- **Evidence pointer** Results section "Geometric signal is tissue-dependent but recoverable through methodological refinement", Table 2, and Methods "Uncertainty decomposition and multiplicity"
- **Concern** The multiplicity correction is applied across 148 comparisons, but the authors do not clarify whether the reported p-values for individual domains (e.g., kidney ΔAUROC = +0.122) remain significant after FDR control when considered in the context of the full grid. The text states "64 reached raw p < 0.05 and 42 survived Benjamini–Hochberg FDR control at q < 0.05, including all headline bundle and PCA-projected results," but it is unclear which specific comparisons are included in the "headline" set and whether the kidney and immune results (which were used for exploratory selection) are appropriately penalized. Additionally, the bootstrap CIs are described as "widened to include the across-seed term," but the exact method for combining within-run and across-seed variance is not specified, making it difficult to assess whether the reported CIs are valid.
- **Why it matters** The central claim of incremental signal depends on the statistical significance of the ΔAUROC estimates. If the FDR correction is not properly applied to the exploratory domains or if the CI construction is flawed, the significance of the headline results could be overstated, undermining the main conclusion.
- **Resolution test** Provide a clear table showing which of the 148 comparisons remain significant after FDR control, with explicit indication of which domains were used for exploratory selection versus confirmatory testing. Specify the exact formula or procedure for combining within-run and across-seed variance in the bootstrap CIs, and show that the headline results (e.g., kidney, immune) remain significant under a conservative correction that accounts for the exploratory nature of those analyses.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Baseline construction
- **Claim pointer** The authors claim that geometric features provide "incremental predictive value" beyond "expression-level confounds," with baseline features including "mean expression, variance, and detection frequency for both source and target genes."
- **Evidence pointer** Methods "Edge classification framework" and Results "Residual-stream geometry carries regulatory signal beyond expression confounds"
- **Concern** The baseline model includes only six expression-level features (mean, variance, detection frequency for source and target). This is a very limited set of confounders. Expression-level confounds could include more complex patterns such as co-expression modules, cell-type composition effects, or library size, which are not captured by these simple summary statistics. The authors acknowledge cell-type composition as a potential confound in the introduction but do not include cell-type proportions or other compositional features in the baseline. Without a more comprehensive baseline, the "incremental" signal attributed to geometry could partly reflect these unmodeled confounds.
- **Why it matters** The claim of "incremental" signal is only meaningful if the baseline captures the relevant confounds. If the baseline is too weak, the geometric features may be capturing expression-related information that is not truly regulatory, inflating the apparent incremental value.
- **Resolution test** Expand the baseline model to include additional expression-derived features (e.g., co-expression module scores, cell-type composition estimates, library size, detection rate distributions) and re-run the edge-level and grouped cross-validation analyses. Show that the incremental ΔAUROC remains positive and significant with the expanded baseline, or quantify how much of the reported effect is attenuated.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors claim the signal is "incremental gene-regulatory signal across tissues" and that the refined methodology is a "uniform improvement" across domains.
- **Evidence pointer** Results "Geometric signal is tissue-dependent but recoverable through methodological refinement", Tables 2 and 5
- **Concern** The study uses only four tissue contexts from a single atlas (Tabula Sapiens) and a single regulatory reference (TRURST). The external lung domain is described as an independent cohort, but it is unclear how independent it is (e.g., same atlas, different donors?). The generalizability to other tissues, developmental stages, disease states, or other regulatory databases (e.g., ENCODE ChIP-seq, GTEx eQTL) is not tested. The authors note that the signal is strongest in immune cells, but the reasons for this tissue-dependence are not explored mechanistically.
- **Why it matters** The title and abstract imply a general phenomenon ("across tissues"), but the evidence is limited to a narrow set of contexts. Without broader validation, the claim of generalizability is not established, and the practical utility for diverse biological settings remains unclear.
- **Resolution test** Add at least one additional tissue or cell type from a different atlas or dataset (e.g., mouse, disease state) and one additional regulatory reference (e.g., a ChIP-seq-derived database) to test whether the signal generalizes. If this is not feasible, temper the claims in the title and abstract to reflect the specific contexts tested.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors claim the pipeline is "pre-specified" and applied to confirmatory domains, and that the cross-model comparison uses "matched per-layer extraction."
- **Evidence pointer** Methods "Exploratory versus confirmatory analyses" and "Geneformer residual-stream extraction"
- **Concern** The manuscript does not provide code, configuration files, or a detailed hyperparameter list for the models (e.g., logistic regression regularization strength, PCA solver parameters, number of components tested). The description of the "pre-specified" pipeline is not accompanied by a protocol or versioned code, making it difficult for others to reproduce the exact analyses. Additionally, the Geneformer extraction uses 192 cells while scGPT uses 256 cells; the rationale for this difference is not explained, and it could affect the comparability of the two models' results.
- **Why it matters** Reproducibility is a core requirement for computational biology studies. Without code and detailed parameters, the results cannot be independently verified, and the claim of a "pre-specified" pipeline is not auditable.
- **Resolution test** Provide a public repository with the full analysis code, including configuration files, random seeds, and version numbers for all dependencies. Justify the difference in cell counts between scGPT and Geneformer, or use identical cell counts for both models.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** The authors propose that the geometric signal "reflects co-regulatory program structure" and that cell-type differences are "consistent with a biologically plausible hypothesis."
- **Evidence pointer** Discussion "What geometric signal represents biologically" and Results "Cell-type and donor stratification reveals biological specificity"
- **Concern** The interpretation that the signal reflects co-regulatory programs is speculative and not directly tested. The authors do not validate whether the geometric features correlate with known regulatory programs (e.g., using pathway enrichment or motif analysis) or whether the cell-type differences align with known regulatory biology beyond the cited literature. The discussion acknowledges this is a hypothesis, but the framing in the abstract and conclusion is more assertive.
- **Why it matters** The biological significance of the findings depends on the interpretation. If the signal is not linked to specific regulatory mechanisms, the practical value for hypothesis generation is limited, and the claim of "gene-regulatory signal" may be overstated.
- **Resolution test** Add a validation analysis linking geometric features to known regulatory programs (e.g., enrichment of TF motifs in target gene promoters, correlation with ChIP-seq binding) or explicitly temper the interpretation in the abstract and conclusion to state that the biological basis is not yet established.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Results "Residual-stream geometry carries regulatory signal beyond expression confounds"
- **Evidence pointer** Abstract and Table 1
- **Issue** The abstract states "geometric features provided significant incremental signal" but does not report the magnitude of the effect (e.g., ΔAUROC range) or the absolute performance, which is modest (AUROC 0.60-0.69). This could mislead readers about the practical significance.
- **Required correction** Include the range of ΔAUROC values and absolute AUROC in the abstract to provide context for the effect size.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results "Geometric signal is tissue-dependent but recoverable through methodological refinement"
- **Evidence pointer** Table 2
- **Issue** The table reports ΔAUROC and ΔAUPRC but does not include the baseline AUROC for each domain consistently (only in the text for some). This makes it difficult to compare effect sizes across domains.
- **Required correction** Add a column for baseline AUROC in Table 2, or ensure it is reported in the text for all domains.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods "Geneformer residual-stream extraction"
- **Evidence pointer** Methods section
- **Issue** The description of Geneformer extraction is brief; it is unclear how the 18-layer hidden states are aggregated (e.g., mean across layers, concatenation) and whether the same PCA and bundling procedures are applied.
- **Required correction** Provide a more detailed description of the Geneformer extraction and feature construction, including any differences from the scGPT pipeline.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods "Data sources and preprocessing"
- **Evidence pointer** Methods section
- **Issue** The manuscript does not specify the exact version of Tabula Sapiens used, the download URLs, or the preprocessing steps (e.g., normalization, filtering) applied to the expression data before model inference.
- **Required correction** Add a data availability statement with specific version numbers, URLs, and preprocessing details to ensure reproducibility.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1-5
- **Evidence pointer** Figure captions
- **Issue** The figure captions are descriptive but do not include statistical details (e.g., number of bootstrap resamples, error bar definitions) or the exact model configuration used for each panel.
- **Required correction** Expand figure captions to include all relevant statistical and methodological details.

## Risk / unsupported claims
- The claim that the geometric signal "reflects co-regulatory program structure" is not directly supported by the data; it is presented as a hypothesis but framed assertively in the conclusion.
- The claim of "incremental gene-regulatory signal across tissues" is not fully supported given the limited number of tissue contexts (four) and the lack of validation on independent datasets or regulatory references.
- The assertion that the "apparent Geneformer advantage mostly disappeared" under matched extraction is based on a single comparison with different cell counts (256 vs. 192), which may not be fully matched.
- The claim that the signal is "fully robust" to leave-TF-out and leave-target-out is based on ΔAUROC values, but the absolute performance under these splits is not reported, making it difficult to assess practical utility.
- The statement that the signal "complements expression-based GRN inference" is supported by the incremental ΔAUROC, but the effect sizes are modest and the practical significance for real-world GRN inference is not demonstrated with downstream analyses (e.g., enrichment of known regulatory pathways in top-ranked edges).

## Assessment against Nature-style criteria
- **Originality** The question of whether residual-stream geometry in single-cell foundation models carries regulatory signal is novel and timely. The systematic comparison of multiple geometric metrics, layer analyses, and cross-validation schemes is a fresh contribution to the interpretability literature for biological transformers. However, the core idea of using representation geometry for regulatory inference has precedents in protein language models, so the novelty is incremental rather than paradigm-shifting.
- **Scientific importance** The findings are important for the growing community using foundation models in genomics, as they clarify what these models encode and how to extract regulatory information. The honest delimitation of the signal's scope (e.g., collapse under leave-both-out) is valuable for setting realistic expectations. However, the modest effect sizes and limited generalizability temper the immediate impact.
- **Interdisciplinary readership** The manuscript bridges machine learning, computational biology, and gene regulation, and the writing is generally accessible. The methods are described in sufficient detail for a computational audience, but the biological interpretation sections may be challenging for ML-focused readers without a genomics background.
- **Technical soundness** The experimental design is rigorous with multiple controls and cross-validation schemes. However, the concerns about baseline construction, multiplicity correction, and reproducibility (lack of code) need to be addressed. The statistical methods are appropriate but the reporting of CIs and p-values could be more transparent.
- **Readability for nonspecialists** The abstract and introduction are clear, but the results sections are dense with technical details. The figures are informative but could benefit from more explicit annotations. The discussion is well-structured and helps contextualize the findings for a broader audience.

## Recommendation posture
**Supportive if technical concerns are resolved.** The manuscript addresses a relevant question with a thoughtful experimental design and honest reporting of limitations. However, the concerns about baseline construction (R1-M2), statistical reporting (R1-M1), and reproducibility (R1-M4) need to be addressed before the claims are fully established. The generalizability concern (R1-M3) is significant but could be mitigated by tempering the claims or adding validation. If the authors can strengthen the baseline model, clarify the statistical methods, and provide code, the work would be a valuable contribution to the field.