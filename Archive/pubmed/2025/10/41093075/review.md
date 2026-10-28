## Review setup
- **Input scope** Full manuscript text, including abstract, results, experimental procedures, and data availability statements.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and support for claims as presented. No assessment of editorial fit or journal policy.
- **Shared manuscript claim summary** The authors report that Sp100A, one of four main Sp100 isoforms, is required for IFN-induced localization of the histone chaperone HIRA and its associated complex members (Ubinuclein-1, ASF1a) to PML nuclear bodies in NIKS keratinocytes. They generated Sp100 knockout cell lines, demonstrated normal differentiation, PML-NB formation, and interferon responses, and used isoform-specific rescue experiments with mutant constructs to implicate the SUMO-interacting motif (SIM) in this process. Structural predictions and molecular dynamics simulations are used to support mechanistic interpretations.
- **Visible evidence base** Results sections describing CRISPR knockout generation, genotyping, immunofluorescence, Western blot, RNA-seq, and structural modeling. Figures 1–8 and Supplementary Figures S1–S9 are referenced. Data availability statements for GEO and ModelArchive are provided.
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S9, Table S1) were not provided. Full RNA-seq analysis details, including differential expression thresholds and complete gene lists, are not shown. Structural model validation metrics are only partially described. Raw imaging data and quantification methods for immunofluorescence are not fully detailed.

## Reviewer
- **Overall assessment** This manuscript addresses a focused question in nuclear body biology: which Sp100 isoform mediates HIRA recruitment to PML-NBs, and what molecular features are required. The generation of clean Sp100 KO cell lines in a normal keratinocyte background is a valuable resource, and the isoform-specific rescue experiments are well conceived. The finding that Sp100A uniquely promotes HIRA localization is novel and of interest to the chromatin and innate immunity communities. However, several technical concerns limit the strength of the conclusions, particularly regarding the mechanistic role of the SIM, the quantitative rigor of the imaging data, and the interpretative weight placed on low-confidence structural predictions. The manuscript would be strengthened by additional biochemical or biophysical evidence for the proposed interactions, and by clearer presentation of quantification methods and statistical analyses.
- **Who would be interested in the results, and why** Researchers studying PML nuclear bodies, histone chaperones, chromatin dynamics, and innate immune memory. The Sp100 KO keratinocyte cell lines will be of practical value to groups studying HPV infection, interferon signaling, and epigenetic regulation. The isoform-specific functional dissection also speaks to the broader question of how alternatively spliced isoforms of nuclear proteins achieve functional diversification.
- **Major Strengths** 
  - Generation and validation of Sp100 KO cell lines in a normal, differentiation-competent keratinocyte background is a significant technical achievement.
  - The isoform-specific rescue approach in a null background is rigorous and directly addresses the question of isoform specificity.
  - The finding that Sp100A uniquely promotes HIRA localization is novel and clearly demonstrated.
  - The inclusion of multiple AI-based structural prediction methods and molecular dynamics simulation is forward-looking, though the interpretation requires caution.
  - The RNA-seq data showing no major transcriptomic changes in KO cells strengthens the specificity of the phenotype.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic support for SIM requirement
- **Claim pointer** The authors claim that the SUMO-interacting motif (SIM) of Sp100A plays an important role in HIRA localization to PML-NBs, based on the observation that the mSIM mutant fails to promote HIRA localization in the absence of IFN, but does so after IFN treatment.
- **Evidence pointer** Results section "Sp100A SUMO interacting motif is important for HIRA localization at PML", Figures 6 and 7, Supplementary Figure S6.
- **Concern** The conclusion that the SIM is important is complicated by the IFN-dependent rescue of the mSIM phenotype. The authors interpret this as IFN-induced SUMOylation compensating for the loss of the SIM, but this is speculative. The alternative interpretation, that the mSIM mutation causes a partial loss-of-function that can be overcome by increased SUMOylation of other substrates, is not tested. The manuscript would be strengthened by direct evidence that the SIM mediates a physical interaction with SUMOylated proteins at PML-NBs, such as co-immunoprecipitation of HIRA with Sp100A or a SUMO pulldown assay. Without such data, the mechanistic claim remains correlative.
- **Why it matters** The SIM is presented as a key mechanistic finding, but the data only show a phenotypic difference. The field would benefit from knowing whether the SIM is required for a direct interaction with HIRA, with a SUMOylated adaptor, or for retention at PML-NBs. The current data do not distinguish these possibilities.
- **Resolution test** Provide biochemical evidence for a SIM-dependent interaction, such as co-immunoprecipitation of HIRA with wild-type versus mSIM Sp100A, or a SUMO-SIM binding assay. Alternatively, demonstrate that the mSIM mutant fails to recruit a SUMOylated intermediate that is required for HIRA binding.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor of imaging data
- **Claim pointer** The authors report percentages of nuclei with HIRA at PML-NBs, and differences between conditions (e.g., wild-type versus mSIM, with and without IFN).
- **Evidence pointer** Results sections "Sp100 is required for localization of HIRA to PML-NBs" and "Sp100A SUMO interacting motif is important for HIRA localization at PML", Figures 3, 5, 6, 7.
- **Concern** The imaging quantification is described as manual scoring of 30–250 cells per condition, but no details are provided on how cells were selected, whether the scorer was blinded, how PML-NB association was defined (e.g., colocalization threshold), or how biological replicates were combined. The error bars are described as "the range of all values," which is unusual and does not convey statistical significance. No statistical tests are reported. For a phenotype that is central to the paper, the quantification must be more rigorous and transparent.
- **Why it matters** The conclusions rest on differences in the percentage of cells showing HIRA at PML-NBs. If the scoring criteria are subjective or the sampling is biased, the reported differences may not be robust. The lack of statistical analysis prevents the reader from assessing the reliability of the findings.
- **Resolution test** Provide a detailed description of the scoring criteria, including how PML-NB association was defined, whether the scorer was blinded to condition, and how many cells were scored per replicate. Report the results of appropriate statistical tests (e.g., mixed-effects model or ANOVA with post-hoc comparisons) for the key comparisons.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Structural prediction interpretation
- **Claim pointer** The authors use AI-based structural predictions and molecular dynamics simulations to propose that interspersed structural domains and intrinsically disordered regions (IDRs) influence isoform-specific localization and function.
- **Evidence pointer** Results section "Structural prediction of the Sp100 isoforms and location of Sp100A mutations", Figures 7D, S7–S9.
- **Concern** The authors acknowledge that the global pLDDT scores are poor (<50) and that only individual domains have high confidence. Despite this, they interpret the models to support a hypothesis about steric hindrance by C-terminal domains in longer isoforms. This is speculative. The molecular dynamics simulation was performed on Sp100B, not Sp100A, and the relevance to the HIRA localization phenotype is unclear. The structural analysis is presented as supportive but does not add strong evidence for the mechanistic claims.
- **Why it matters** The structural modeling is used to rationalize why only Sp100A promotes HIRA localization. If the models are low-confidence, this rationalization is not compelling. Overinterpretation of low-quality structural predictions could mislead readers.
- **Resolution test** Either provide experimental validation of the predicted domain organization (e.g., limited proteolysis, crosslinking, or hydrogen-deuterium exchange) or temper the claims to clearly state that the structural models are purely speculative and do not constitute evidence for the proposed mechanism.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the KO phenotype
- **Claim pointer** The authors state that Sp100 KO cells show normal differentiation, PML-NB formation, and interferon responses, and that HIRA localization to PML-NBs is not required for immediate interferon signaling.
- **Evidence pointer** Results sections "The absence of Sp100 does not affect keratinocyte differentiation", "PML-NB formation and localization of Daxx are unaltered in Sp100 KO keratinocytes", and "RNA-seq analysis shows no significant changes in basal or interferon-stimulated gene expression in the Sp100 KO cells", Figures 2, 8, S2, S3.
- **Concern** The RNA-seq analysis is described only briefly. The authors state there were "no major differences" but do not report the number of differentially expressed genes, the thresholds used, or whether any genes approached significance. The claim that HIRA localization is not required for immediate interferon signaling is based on a lack of observed difference, which is a null result that requires careful statistical justification. Additionally, the KO cells were generated with a mix of gRNAs targeting exons 3, 6, and 8; the possibility of residual truncated isoforms or off-target effects is not fully addressed.
- **Why it matters** The paper argues that the Sp100 KO cells are a clean system for studying HIRA localization. If the KO is incomplete or the transcriptomic analysis is underpowered, the conclusions about the dispensability of HIRA localization for IFN signaling may be premature.
- **Resolution test** Report the full differential expression analysis, including the number of genes passing significance thresholds and the effect sizes. Confirm the absence of truncated Sp100 isoforms by Western blot with antibodies against different regions of the protein. Consider whether the sample size (n=3) is sufficient to detect meaningful differences.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figures 3, 5, 6, 7
- **Evidence pointer** Results sections as above.
- **Issue** The figures show representative images and quantification, but the color coding and labeling of conditions are not always consistent across panels. For example, in Figure 5, the categories for HIRA association are described in the legend but are not always intuitive from the figure itself.
- **Required correction** Ensure that all conditions are clearly labeled in each panel, and consider adding a schematic or table that summarizes the scoring categories and how they map to the colors used.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** All quantification figures
- **Evidence pointer** Figures 2, 3, 4, 5, 7
- **Issue** No statistical tests are reported for any of the quantification data. The error bars are described as the range, which is not standard for biological replicates.
- **Required correction** Report the mean and standard deviation or standard error of the mean for each condition, and perform appropriate statistical tests for the key comparisons. State the test used and the p-values in the figure legends or results text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail for structural predictions
- **Affected element** Experimental procedures, "Protein structural prediction and molecular dynamics simulation"
- **Evidence pointer** Methods section.
- **Issue** The description of the structural prediction pipeline is brief. The authors state that "meta-/homology models" were constructed but do not specify which templates were used, how the models were combined, or how the final models were validated beyond a Z-score.
- **Required correction** Provide more detail on the modeling pipeline, including the specific software versions, template PDB IDs, and validation metrics for each model. This will allow readers to assess the reliability of the structural claims.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of alternative hypotheses
- **Affected element** Discussion section
- **Evidence pointer** Discussion.
- **Issue** The authors propose that IFN-induced SUMOylation compensates for the mSIM defect, but do not discuss alternative explanations, such as the possibility that the mSIM mutation affects protein stability or folding.
- **Required correction** Add a brief discussion of alternative interpretations and how they might be distinguished experimentally.

- **Technical failings that need to be addressed before the case is established** 
  - R1-M1: Lack of biochemical evidence for SIM-dependent interaction.
  - R1-M2: Insufficient detail on imaging quantification and lack of statistical analysis.
  - R1-M3: Overinterpretation of low-confidence structural predictions.
  - R1-M4: Incomplete reporting of RNA-seq analysis and potential for residual SpAM expression.

- **Assessment against Nature-style criteria** 
  - **Originality** The finding that Sp100A specifically promotes HIRA localization is novel and adds to the understanding of isoform-specific functions within the Sp100 family. The use of a clean KO system in normal keratinocytes is a methodological advance. However, the conceptual advance is incremental, as the role of Sp100 in HIRA recruitment was already known.
  - **Scientific importance** The work is of moderate importance. It clarifies which isoform is responsible and identifies the SIM as a contributing factor, but the broader significance for chromatin dynamics or innate immunity is not fully established. The null result for IFN signaling is useful but not transformative.
  - **Interdisciplinary readership** The topic will appeal to cell biologists, chromatin biologists, and immunologists. The structural prediction component may attract computational biologists, but the low confidence of the models limits this appeal.
  - **Technical soundness** The cell biology is generally sound, but the quantification and statistical reporting need improvement. The structural analysis is technically competent but overinterpreted. The RNA-seq analysis is underreported.
  - **Readability for nonspecialists** The manuscript is clearly written and the figures are generally understandable. The structural prediction section may be challenging for nonspecialists, but the main conclusions are accessible.
- **Recommendation posture** Supportive if technical concerns are resolved. The core finding, that Sp100A is the primary isoform for HIRA recruitment, is likely correct and of interest. However, the mechanistic claims regarding the SIM and the structural interpretations require additional evidence or tempering. The quantification and statistical reporting must be improved to support the conclusions.