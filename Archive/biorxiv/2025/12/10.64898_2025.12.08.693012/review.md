## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Discussion, Methods) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific validity, technical soundness, and generalizability claims of the TREND platform as described in the provided text
- **Shared manuscript claim summary** The authors present TREND, a lentiviral massively parallel reporter assay (MPRA) platform screening approximately 2.7 million enhancer-barcode constructs (57,715 designs) targeting 1,068 DNA-binding proteins. They claim TREND identifies context-specific synthetic enhancers without requiring pre-existing genomic annotations or training data, demonstrated through cancer-selective enhancers in ovarian cancer models and activation-responsive enhancers in primary human T cells. They further claim these enhancers enable logic-gated gene circuits with reduced off-target activity and therapeutic efficacy in vivo.
- **Visible evidence base** Text descriptions of results, methods, and figure references (Figures 1-5, S1-S11) without actual data, figures, or numerical values
- **Missing materials affecting confidence** All figures, tables, supplementary materials, numerical data, statistical outputs, and raw sequencing results are absent from the provided text

## Reviewer
- **Overall assessment** The manuscript describes an ambitious and potentially valuable platform for synthetic enhancer discovery. The conceptual advance of screening TF-binding motifs directly in target cellular contexts, rather than relying on pre-existing genomic annotations, is intellectually appealing. However, the provided text is almost entirely descriptive, with no quantitative data, statistical analyses, or visual evidence to support the central claims. The platform's generalizability, the specificity of identified enhancers, and the therapeutic efficacy in vivo cannot be evaluated from the current submission. The work may represent a meaningful contribution to synthetic biology and gene therapy, but the evidence base as presented is insufficient to establish the claims.
- **Who would be interested in the results, and why** Researchers in synthetic biology, gene therapy, and cancer immunotherapy would find this work relevant. The platform addresses a recognized bottleneck in cell-type-specific gene regulation, and the demonstration of logic-gated circuits for tumor-restricted immunotherapy has translational appeal. Those working on CAR-T cell engineering, inducible gene expression systems, and enhancer design would be the primary audience.
- **Major strengths** The conceptual framework of directly assaying TF-responsive motifs across cellular contexts is a reasonable and potentially generalizable strategy. The scale of the library (57,715 designs, 1,068 targets) is substantial. The extension from cancer cell lines to primary human T cells suggests versatility. The comparison to conventional NFAT-based enhancers for T-cell activation is a practically relevant benchmark. The open-source pipeline and dashboard for community use is commendable.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (no quantitative evidence), R1-M2 (generalizability claim unsupported), R1-M3 (in vivo efficacy not established), R1-M4 (comparison to prior work incomplete)
- **Assessment against Nature-style criteria** Originality: The approach of screening TF motif variants in a pooled format is not entirely novel, as similar MPRA-based strategies exist, but the scale and the specific application to therapeutic gene circuits may offer incremental originality. Scientific importance: Potentially high if the claims are substantiated, as cell-type-specific gene regulation is a major challenge in gene therapy. Interdisciplinary readership: The work bridges synthetic biology, immunology, and cancer biology, which could attract broad interest. Technical soundness: Cannot be assessed from the provided text, as no data are shown. Readability for nonspecialists: The text is generally clear and logically organized, though some sections assume familiarity with MPRA and gene circuit terminology.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires substantial additional data, including figures, numerical results, and statistical analyses, before the claims can be evaluated.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that TREND identified cancer-selective enhancers with robust specificity and T-cell activation-responsive enhancers with lower basal activity than conventional NFAT-based elements.
- **Evidence pointer** Results sections "TREND platform identifies candidate cancer-selective synthetic enhancers" and "TREND platform identifies activation-responsive synthetic enhancers for T cell activation-dependent gene control"; Figures 1, 2, 5
- **Concern** The manuscript provides no quantitative data whatsoever. No enrichment scores, activity ratios, fold changes, p-values, confidence intervals, or effect sizes are reported. The claims of "robust cancer selectivity," "markedly improved specificity," and "greater inducibility" are entirely unsupported by numerical evidence. The reader cannot assess the magnitude of the observed effects or the statistical reliability of the findings.
- **Why it matters** Without quantitative data, the central claims of the paper cannot be verified. The platform's utility depends on demonstrating that identified enhancers achieve meaningful specificity and activity differences, not merely that some constructs show differential activity. The absence of data prevents any assessment of effect sizes, variability, or reproducibility.
- **Resolution test** Provide the actual activity measurements for the identified enhancers, including RNA/DNA ratios, fold changes relative to controls, statistical tests, and variability estimates. Show the distribution of activities across the library and the specific values for the highlighted candidates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability claim
- **Claim pointer** The title and abstract claim TREND is a "generalizable synthetic enhancer discovery platform," and the Discussion states it "provides a broadly applicable approach for precise gene control across diverse biological systems."
- **Evidence pointer** Abstract; Discussion section; Results sections on ovarian cancer and T cells
- **Concern** The generalizability claim is based on only two application contexts: ovarian cancer cell lines and primary human T cells. Both are cancer or immune-related. No evidence is provided for other tissue types, disease states, or non-cancer contexts. The claim of generalizability is therefore overstated relative to the demonstrated scope.
- **Why it matters** The title and framing of the paper hinge on the generalizability of the platform. If the approach only works in certain cellular contexts or requires specific conditions, the claim would need to be substantially qualified. Overstating generalizability could mislead potential users and overstate the platform's utility.
- **Resolution test** Either provide additional application examples in diverse cell types or disease contexts, or revise the claims to accurately reflect the demonstrated scope. At minimum, discuss the known limitations and conditions under which the platform may not generalize.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** In vivo efficacy
- **Claim pointer** The manuscript claims that AND-gate circuits driving immunomodulatory payloads produced "robust antitumor responses" and "reduced tumor burden" in murine ovarian cancer models.
- **Evidence pointer** Results section "Tumor-restricted AND-gate circuits drive conditional combinatorial immunotherapy in vivo"; Figure 4
- **Concern** The in vivo results are described only qualitatively. No survival curves, tumor growth measurements, statistical comparisons, or effect sizes are provided. The claim of "robust antitumor responses" cannot be evaluated without knowing the magnitude of the survival benefit, the consistency across animals, or the comparison to appropriate controls.
- **Why it matters** The in vivo demonstration is a key translational claim of the paper. If the therapeutic effect is modest or inconsistent, the practical significance of the platform would be diminished. The absence of data prevents any assessment of the clinical potential.
- **Resolution test** Provide the actual survival data, tumor burden measurements, statistical analyses, and the number of animals per group. Show the dose-response relationship and the comparison to relevant control groups.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison to prior work
- **Claim pointer** The Discussion states that TREND's identified enhancers showed "higher output and improved cancer selectivity" compared to earlier manually designed synthetic enhancers, and that FOSL1_v1 is "tighter and more precise" than conventional NFAT-based designs.
- **Evidence pointer** Discussion section; Figure 2E, 2F; Figure 5E-5J
- **Concern** The comparisons to prior designs are described without quantitative data. The reader cannot verify whether the improvements are statistically significant, consistent across replicates, or practically meaningful. Additionally, the comparison to NFAT-based enhancers appears to be limited to a single construct, which may not represent the full range of NFAT-based designs.
- **Why it matters** The claim of superiority over existing approaches is important for establishing the value of the platform. Without quantitative comparisons, the reader cannot determine whether the improvements are real or within the range of experimental variability.
- **Resolution test** Provide the actual activity and specificity measurements for both the TREND-derived enhancers and the comparator constructs, including statistical tests and effect sizes. Clarify the scope of the comparison and any limitations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Terminology precision
- **Affected element** Abstract and throughout
- **Evidence pointer** Abstract; Introduction
- **Issue** The term "generalizable" is used in the title and abstract, but the manuscript does not define what constitutes generalizability in this context. It is unclear whether this refers to applicability across cell types, disease states, or species.
- **Required correction** Define the scope of generalizability explicitly and ensure the claims match the demonstrated evidence.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** MPRA normalization and filtering
- **Evidence pointer** Methods section "Barcode quantification and enhancer activity analysis"
- **Issue** The description of the filtering thresholds is vague. The text states that a reporting threshold of 75% and a minimum barcode count of 3 were selected, but the rationale for these specific values and their impact on the results is not explained.
- **Required correction** Provide a more detailed justification for the chosen thresholds and discuss their potential impact on the sensitivity and specificity of enhancer identification.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** All results sections
- **Evidence pointer** Figures 1-5
- **Issue** No statistical methods are described for comparing enhancer activities between conditions. The text mentions t-tests and ANOVA in the Methods, but it is unclear which comparisons were tested and whether multiple testing corrections were applied.
- **Required correction** Specify the statistical tests used for each comparison, the number of replicates, and whether corrections for multiple testing were applied.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Code and data availability section
- **Evidence pointer** Code and data availability section
- **Issue** The manuscript states that processed data will be made available upon publication, but the raw sequencing data are only available upon reasonable request. For a platform paper, access to raw data is important for independent verification and reanalysis.
- **Required correction** Consider depositing raw sequencing data in a public repository to facilitate transparency and reproducibility.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** All figures
- **Evidence pointer** Figures 1-5
- **Issue** The text refers to figures extensively, but the figures themselves are not provided in the manuscript text. This makes it impossible to evaluate the data visually.
- **Required correction** Ensure that all figures are included in the submission and that they are of sufficient quality to assess the data.

## Risk / unsupported claims
- The claim that TREND is "generalizable" across diverse biological systems is unsupported, as only ovarian cancer and T cell contexts are demonstrated.
- The claim that TREND-derived enhancers show "higher output and improved cancer selectivity" compared to prior designs is unsupported without quantitative comparisons.
- The claim that FOSL1_v1 is "tighter and more precise" than conventional NFAT-based enhancers is unsupported without quantitative data.
- The claim of "robust antitumor responses" in vivo is unsupported without survival data, tumor measurements, or statistical analyses.
- The claim that TF expression alone is a poor predictor of enhancer activity is based on a correlation analysis that is not shown.
- The claim that the library captures 75% of lineage-specific master transcription factors and 70% of core identity transcription factors is not verifiable without the underlying data and definitions.