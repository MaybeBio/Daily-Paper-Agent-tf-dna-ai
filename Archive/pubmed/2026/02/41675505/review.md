## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, conclusion, materials and methods) as provided. No figures, tables, or supplementary materials were available for review.
- **Assessment boundary** Assessment is limited to the written text. Claims referring to figures, tables, or supplementary data are evaluated based on textual description only. No raw data, statistical outputs, or experimental protocols beyond those described were accessible.
- **Shared manuscript claim summary** The authors present SPECIFIC, a computational-experimental framework that integrates ATAC-seq profiling, differential motif analysis, and synthetic promoter engineering to identify cell state-specific regulatory elements. Applied to T cell exhaustion, the pipeline identifies 56 conserved transcription factor binding motifs across mouse and human models, engineers 22 into synthetic promoters, and demonstrates that promoters containing NFATc2 or MEF2C binding sites suppress CAR expression and exhaustion markers in primary human T cells.
- **Visible evidence base** Textual descriptions of results, methods, and figure references. No actual figures, tables, supplementary tables, or numerical data were provided.
- **Missing materials affecting confidence** All figures (Figures 1–4), Supplementary Tables S1 and S2, raw ATAC-seq data, statistical analyses, flow cytometry data, and detailed computational parameters. The absence of these materials substantially limits verification of the central claims.

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful framework for engineering cell state-specific synthetic promoters, with an application to T cell exhaustion. The conceptual approach, combining chromatin accessibility data with motif analysis and functional validation, is reasonable and timely. However, the evidence as presented in the text is insufficient to fully support the claims. Key quantitative data, statistical analyses, and methodological details are missing. The claim that specific promoters "effectively attenuated T cell dysfunction" is not substantiated by the data described. The manuscript would benefit from clearer presentation of results, additional controls, and more rigorous statistical treatment.
- **Who would be interested in the results, and why** Researchers in synthetic biology, immunology, and cell therapy development would be interested. The framework offers a systematic approach to designing state-responsive promoters, which is relevant for building gene circuits that sense cellular states. The application to T cell exhaustion is of direct interest to those working on CAR-T cell therapy and adoptive cell transfer, as modulating exhaustion could improve therapeutic outcomes.
- **Major strengths** The conceptual framework is well organized and addresses a real need in synthetic promoter design. The cross-species comparative approach is a strength, as it may increase the generalizability of identified regulatory elements. The use of a functional gene circuit to validate promoter activity is appropriate. The discussion of limitations and future directions is thoughtful and balanced.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "Several synthetic promoters, particularly those containing NFATc2 or MEF2C binding sites, demonstrated remarkable specificity in recognizing the exhausted state and effectively attenuated T cell dysfunction by reducing both CAR expression and exhaustion markers."
  - **Evidence pointer** Figures 3 and 4, described in text; location not provided
  - **Concern** The central functional claim is based on flow cytometry measurements of CAR and exhaustion marker expression. However, no quantitative data, statistical tests, or effect sizes are reported. The text states "nearly complete suppression" and "significantly lower levels" without providing numerical values, error bars, or p-values. The number of biological replicates, donor variability, and gating strategies are not described. Without these data, the claim of "remarkable specificity" and "effective attenuation" cannot be evaluated.
  - **Why it matters** The functional validation is the core evidence that the synthetic promoters work as claimed. If the effect sizes are small or variable, the conclusions would be substantially weakened. The absence of quantitative data prevents assessment of robustness and reproducibility.
  - **Resolution test** Provide representative flow cytometry plots, summary statistics (mean ± SD or SEM), statistical comparisons (e.g., t-tests or ANOVA) for CAR and exhaustion marker expression across all constructs and time points, and specify the number of independent experiments and donors.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "By intersecting motifs that showed significant enrichment (p < 0.05) across all three datasets, we identified 56 transcription factor binding motifs consistently associated with the exhausted state."
  - **Evidence pointer** Figure 2, described in text; location not provided
  - **Concern** The identification of 56 conserved motifs is a key computational result. However, the text does not describe the differential peak calling criteria, the number of peaks analyzed, the multiple testing correction method, or how the intersection across datasets was performed. The p-value threshold of 0.05 without correction is likely to yield false positives given the large number of motifs tested. The use of different genome builds (mm9 and hg19) and different model systems (in vitro mouse, in vivo mouse, human CAR-T) raises questions about comparability.
  - **Why it matters** The reliability of the motif list underpins the entire downstream design. If the motif identification is not statistically rigorous, the selected promoters may not be truly exhaustion-specific.
  - **Resolution test** Describe the full computational pipeline, including peak calling parameters, motif scanning approach, multiple testing correction, and the exact intersection method. Provide the number of peaks and motifs at each step. Consider using a more stringent threshold or validation of motif enrichment in independent datasets.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** "The SPECIFIC pipeline not only advances our understanding of T cell exhaustion but also provides a generalizable framework for engineering synthetic promoters responsive to any well-defined cellular state."
  - **Evidence pointer** Methods section; location not provided
  - **Concern** The generalizability claim is not supported by evidence. The framework is demonstrated in one context (T cell exhaustion) with a limited set of promoters. No data are presented to show that the pipeline works in other cell states or that the computational steps are transferable. The methods section lacks details on how the framework would be adapted to other systems.
  - **Why it matters** The title and abstract emphasize the systematic and generalizable nature of the framework. If the pipeline is not shown to be broadly applicable, the claims are overstated.
  - **Resolution test** Either temper the generalizability claims or provide additional examples of applying SPECIFIC to other cell states. At minimum, describe the steps required to adapt the pipeline to a new system.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** "The classical NFAT promoter [21] serving as a control based on its well-characterized role in T cell regulation."
  - **Evidence pointer** Methods section, "Synthetic promoter design"; location not provided
  - **Concern** The choice of the NFAT promoter as a control is problematic. NFAT is known to be involved in T cell exhaustion, so it may not be an appropriate negative control. The text does not clarify whether the NFAT promoter was used as a positive control or a comparator. The distinction matters for interpreting the results.
  - **Why it matters** If the control is not appropriate, the specificity claims for the synthetic promoters are weakened. A proper control should be a promoter that is not responsive to exhaustion-associated transcription factors.
  - **Resolution test** Clarify the role of the NFAT promoter control. If it is intended as a positive control, state this explicitly. Consider including a minimal promoter-only construct as a negative control.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract states "56 conserved transcription factor binding motifs" but does not specify the conservation criteria. It is unclear whether conservation refers to sequence conservation across species or statistical enrichment across datasets.
  - **Required correction** Define "conserved" in the abstract or rephrase to "motifs consistently enriched across three exhaustion models."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, "Synthetic promoter design"
  - **Evidence pointer** Methods section; location not provided
  - **Issue** The text states "The number of repeats was calculated to achieve approximately 120bp of binding sites." The calculation method is not described, and it is unclear how the length of binding sites varies among different transcription factors.
  - **Required correction** Provide the formula or rationale for determining repeat numbers, and specify the range of binding site lengths used.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Methods, "Lentiviral transduction"
  - **Evidence pointer** Methods section; location not provided
  - **Issue** The multiplicity of infection (MOI) is stated as 10, but the transduction efficiency is not reported. Variability in transduction efficiency could affect the interpretation of CAR expression levels.
  - **Required correction** Report transduction efficiency (e.g., percentage of GFP+ or CAR+ cells) and consider normalizing data to transduction efficiency.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Results, "Construction of synthetic promoters"
  - **Evidence pointer** Results section; location not provided
  - **Issue** The text mentions "some motifs sourced from Homer-generated PWMs during differential analysis" but does not specify which motifs or how they were selected. This introduces potential ambiguity in reproducibility.
  - **Required correction** List all motifs used, their sources (JASPAR or Homer), and the criteria for selection.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results, "Construction of synthetic promoters"
  - **Evidence pointer** Results section; location not provided
  - **Issue** The text states "some constructs showed divergent effects on different markers" but does not provide statistical analysis to support these observations. It is unclear whether the differences are significant.
  - **Required correction** Provide statistical comparisons for all marker measurements across constructs, or clearly state that the observations are qualitative.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of quantitative data for functional claims), R1-M2 (insufficient computational details for motif identification), R1-M3 (overstated generalizability), R1-M4 (inappropriate control choice).
- **Assessment against Nature-style criteria**  
  *Originality*: The framework is a useful integration of existing methods, but the individual components (ATAC-seq, motif analysis, synthetic promoter design) are established. The novelty lies in the systematic combination and application to T cell exhaustion. This is moderate originality, not a conceptual breakthrough.  
  *Scientific importance*: T cell exhaustion is a clinically relevant problem, and tools to modulate it are valuable. However, the demonstrated impact is limited to in vitro observations without functional assays (e.g., cytokine production, cytotoxicity). The importance is potential rather than demonstrated.  
  *Interdisciplinary readership*: The work bridges computational biology, synthetic biology, and immunology. It could appeal to readers across these fields, but the technical depth in each area may limit accessibility.  
  *Technical soundness*: The computational and experimental approaches are reasonable in principle, but the lack of quantitative data, statistical rigor, and detailed methods prevents verification. The control choice is questionable.  
  *Readability for nonspecialists*: The manuscript is generally well written and the logic is clear. However, some terms (e.g., "Homer," "PWMs") are used without sufficient explanation for a broad audience. The abstract is accessible, but the results section assumes familiarity with the techniques.
- **Recommendation posture** Currently not established from the provided evidence. The framework is promising, but the central claims require substantial additional data and analysis. I would be supportive if the authors provide quantitative results, statistical analyses, appropriate controls, and sufficient methodological detail to evaluate reproducibility.

## Risk / unsupported claims
- The claim that SPECIFIC is "generalizable" to any cell state is unsupported; only one application is shown.
- The claim that NFATc2 and MEF2C promoters "effectively attenuated T cell dysfunction" is unsupported without functional data (e.g., cytokine production, proliferation, cytotoxicity).
- The claim of "remarkable specificity" is unsupported without quantitative comparison to control promoters.
- The identification of "56 conserved transcription factor binding motifs" is not verifiable without details on the computational pipeline and statistical thresholds.
- The statement that "several synthetic promoters... demonstrated remarkable specificity" is vague and not tied to specific data.
- The claim that the gene circuit "senses and responds to T cell dysfunction" is inferred from CAR and marker expression but not directly demonstrated.