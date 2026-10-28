## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, author contributions, acknowledgements) as provided
- **Assessment boundary** Scientific content, methodological rigor, claims vs. evidence alignment, and presentation quality based solely on the provided text
- **Shared manuscript claim summary** The authors investigate how DNA sequence context and chromatin features determine genome-wide binding site selection for eight P. falciparum transcription factor DNA-binding domains, using a novel genomic-context protein-binding microarray (gcPBM), ChIP-seq, and integration with published epigenomic datasets. They report that CACACA-binding TFs are minimally influenced by sequence context, while GTGCAC-binding TFs show distinct sequence preferences; chromatin accessibility and epigenetic marks differentiate in vivo binding; and low-affinity binding to non-cognate motifs may drive co-occupancy.
- **Visible evidence base** Abstract, full introduction, full methods (protein induction, gcPBM design and experiment, ChIP-seq, EMSA, data analysis), full results narrative, full discussion, author contributions, acknowledgements. No figures, tables, or supplementary files were provided.
- **Missing materials affecting confidence** All figures and figure legends, all supplementary files (including Supplemental Files 1–7), the results section appears to be present but without figure references being verifiable, and the specific numerical data (e.g., correlation coefficients, p-values, enrichment scores) are not independently checkable. The absence of figures and supplementary data substantially limits verification of the claims.

## Reviewer
- **Overall assessment** This manuscript addresses a significant and timely question in malaria biology: how a small set of sequence-specific transcription factors achieves regulatory specificity in a highly A/T-rich genome. The authors combine a custom genomic-context protein-binding microarray with existing ChIP-seq and epigenomic datasets, which is a creative and potentially powerful approach. The central findings, that paralogous CACACA-binding domains are not strongly differentiated by sequence context in vitro, while GTGCAC-binding domains show clearer sequence preferences, and that chromatin state distinguishes in vivo occupancy, are interesting and plausible. However, the manuscript as presented has several critical limitations. The absence of all figures and supplementary data makes it impossible to evaluate the quality of the gcPBM data, the ChIP-seq analysis, or the statistical claims. The narrative is dense and sometimes difficult to follow, with key results described only in text. The claim that low-affinity binding to divergent motifs drives co-occupancy is intriguing but is supported only by in vitro data and indirect comparisons, without direct experimental evidence. The discussion is somewhat speculative in places, particularly regarding pioneer factor activity and therapeutic implications. Overall, the study has merit and the approach is novel, but the evidence as presented is insufficient to fully establish the central claims.

- **Who would be interested in the results, and why** Researchers studying transcriptional regulation in Plasmodium falciparum and other Apicomplexan parasites will find this directly relevant, as it addresses how a limited TF repertoire achieves regulatory diversity. The broader gene regulation community, particularly those interested in paralogous TF functional divergence, DNA shape readout, and the integration of in vitro and in vivo binding data, will also be interested. The gcPBM approach itself may be of methodological interest to those studying TF binding in non-model organisms with extreme genomic composition. The potential therapeutic implications for targeting ApiAP2 TFs may interest drug discovery researchers focused on malaria.

- **Major strengths**
  1. The study addresses an important and under-explored question: how P. falciparum TFs achieve binding specificity given the extreme A/T bias of the genome and the small number of TFs.
  2. The development of a P. falciparum-specific genomic-context protein-binding microarray (gcPBM) is a novel and appropriate tool for this question, allowing simultaneous assessment of all genomic instances of a motif with native flanking sequence.
  3. The integration of in vitro binding data with in vivo ChIP-seq, chromatin accessibility, and histone modification datasets is a comprehensive approach that acknowledges the multi-layered nature of TF binding specificity.
  4. The inclusion of multiple TF families (CACACA-binders, GTGCAC-binders, and unique-motif binders) provides a comparative framework that strengthens the conclusions.
  5. The finding that CACACA-binding paralogs are not strongly differentiated by sequence context, but differ in multimerization capacity, is a novel and interesting observation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality and verifiability
- **Claim pointer** The manuscript claims that the gcPBM data reveal differential sequence context preferences between TF groups and that these data support conclusions about in vitro binding specificity.
- **Evidence pointer** Methods (gcPBM design and analysis), Results (Figures 2, 3, and associated supplementary figures), location not provided
- **Concern** The entire results section is presented without any figures, tables, or supplementary data being visible. The gcPBM is a custom, novel platform, and the quality of the data, the reproducibility of the array, the dynamic range of the binding signal, and the statistical treatment of the data cannot be assessed. The authors reference correlation coefficients (R² values), p-values, and enrichment analyses, but none of these are verifiable without the actual data. The claim that "sequence context had limited importance" for CACACA-binders versus "greater impact" for GTGCAC-binders is a central distinction, but the supporting distributions, thresholds, and statistical tests are not visible.
- **Why it matters** The central conclusions of the paper rest entirely on the quality and interpretation of the gcPBM data. Without the ability to inspect the raw distributions, the thresholding approach, the reproducibility between replicates, or the statistical comparisons, the claims cannot be evaluated. This is particularly important because the gcPBM is a new method, and the field will need to assess its reliability before accepting conclusions drawn from it.
- **Resolution test** The authors must provide all figures and supplementary data, including representative array images, scatter plots of replicate reproducibility, distributions of binding intensities for each TF across all probes, the thresholding approach clearly shown, and the full statistical output for all comparisons. The R² values and p-values cited in the text must be traceable to specific analyses.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The manuscript claims that "chromatin accessibility, epigenetic patterns, co-factor recruitment, and dimerization contribute to differential binding" for CACACA-binders, and that GTGCAC-binders "prefer different DNA sequence context in addition to chromatin dynamics."
- **Evidence pointer** Results (Figures 4, 5, and supplementary figures), location not provided
- **Concern** The integration of ChIP-seq, ATAC-seq, and histone modification data is described in the text, but the actual analyses are not shown. For example, the claim that AP2-LT ChIP-bound sites become accessible during late-stage development is stated, but the ATAC-seq profiles, the statistical comparison between ChIP-bound and ChIP-unbound sites, and the temporal dynamics are not visible. Similarly, the claim that AP2-HC binds inaccessible chromatin is stated but not shown. The comparison of epigenetic mark enrichment between ChIP-bound and ChIP-unbound sites is described as showing "modest differences," but the data supporting this are absent. The co-occupancy analysis between AP2-G, AP2-I, and AP2-LT/AP2-EXP is described but the Venn diagrams, overlap statistics, and the low-affinity binding data are not shown.
- **Why it matters** The manuscript's key contribution is the integration of multiple data types to explain in vivo binding specificity. If the supporting analyses are not visible, the claims cannot be distinguished from speculation. The "modest differences" in epigenetic marks between bound and unbound sites is a particularly important observation, as it may undermine the argument that chromatin state is a primary determinant; this needs to be carefully examined.
- **Resolution test** The authors must provide all ChIP-seq, ATAC-seq, and histone modification analyses, including heatmaps or profile plots at bound vs. unbound sites, statistical comparisons, and the co-occupancy overlap analyses. The temporal ATAC-seq data must be shown to support the claim about dynamic chromatin opening.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of the gcPBM approach
- **Claim pointer** The manuscript claims that the gcPBM can simultaneously assess binding of eight DBDs to all genomic instances of their cognate motifs with native flanking sequence context.
- **Evidence pointer** Methods (gcPBM design), Results (Figures 2, 3), location not provided
- **Concern** The gcPBM design is described, but several technical aspects require clarification. First, the authors state that "any sequence containing another instance of the centered motif in the left or right flanks was mutated to prevent multiple binding sites per 36-bp window," but the mutation strategy is not described. Mutating flanking sequence could itself alter binding affinity in ways that confound the interpretation. Second, the authors used a motif E-score cutoff of >0.45 to identify genomic instances, but the sensitivity and specificity of this cutoff for each TF is not discussed. Third, the gcPBM measures binding of isolated DBDs, not full-length TFs, and the authors do not discuss how the absence of flanking domains might affect binding specificity. Fourth, the authors note that HDP1 was "included due to PWM similarities to SIP2_D1 and AP2-I_D3," but the criteria for this inclusion and the potential for cross-reactivity are not addressed.
- **Why it matters** The gcPBM is the foundation of the study. If the array design has systematic biases, such as the mutation strategy altering binding in unpredictable ways, or if the DBD constructs do not recapitulate full-length TF behavior, the conclusions about sequence context preferences could be artifacts. The field will need to understand these technical details to evaluate the reliability of the platform.
- **Resolution test** The authors must provide a detailed description of the mutation strategy, including the number and positions of mutations introduced, and ideally a validation showing that the mutations do not systematically alter binding. They should also discuss the limitations of using isolated DBDs and provide evidence that the DBD constructs behave similarly to full-length TFs where possible.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of in vitro-in vivo discordance
- **Claim pointer** The manuscript claims that the shift from in vitro CACACA preference to in vivo TGCAC preference for AP2-LT suggests that "specific features of the nuclear environment such co-factor interactions, multimerization, chromatin accessibility, and/or epigenetic marks may contribute to the divergent in vivo sequence specificity."
- **Evidence pointer** Results (Figure 4, Supplemental Figures 15, 16), location not provided
- **Concern** The observation that AP2-LT binds a TGCAC motif in vivo, which is different from its in vitro CACACA preference, is striking and potentially important. However, the explanation offered is speculative and not directly tested. The authors do not present any experiments to distinguish between the possible mechanisms. For example, they do not test whether AP2-LT can bind TGCAC in vitro under different conditions, whether cofactors alter its specificity, or whether the ChIP-seq motif is an artifact of antibody specificity or peak calling. The claim that AP2-LT may act as a pioneer factor is particularly speculative and is not supported by any direct evidence.
- **Why it matters** The in vitro-in vivo discordance is one of the most interesting findings in the paper, but the interpretation is currently under-supported. If the mechanism is not understood, the conclusion that chromatin context overrides sequence specificity is weakened. The pioneer factor hypothesis, if incorrect, could mislead the field.
- **Resolution test** The authors should either provide direct experimental evidence for the proposed mechanisms (e.g., EMSA with TGCAC probes under various conditions, co-immunoprecipitation to identify cofactors, or mutation of the TGCAC motif in vivo) or temper the claims to reflect the speculative nature of the interpretation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor and multiple testing
- **Claim pointer** The manuscript reports numerous pairwise comparisons, correlation coefficients, and enrichment analyses without describing how multiple testing was handled.
- **Evidence pointer** Results (Figures 2, 3, 5, and supplementary figures), location not provided
- **Concern** The authors perform many statistical tests, including pairwise comparisons of binding intensities between TFs, comparisons between ChIP-bound and ChIP-unbound sites, and enrichment analyses for histone modifications. The manuscript does not describe how multiple testing was controlled. Given the large number of probes on the array and the many comparisons made, the risk of false positives is substantial. The R² values reported for pairwise correlations are descriptive, but the significance of differences between correlation coefficients is not addressed.
- **Why it matters** Without appropriate multiple testing correction, some of the reported differences may be due to chance. This is particularly relevant for the claims about modest differences in sequence context preferences between CACACA-binders, where the effects are described as small.
- **Resolution test** The authors must describe their multiple testing correction strategy for all analyses, or justify why it was not applied. They should also report confidence intervals or effect sizes for the key comparisons.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Results section, overall structure
- **Evidence pointer** Results, location not provided
- **Issue** The results section is written as a continuous narrative without clear subheadings or figure callouts. This makes it difficult to follow which experiment corresponds to which claim.
- **Required correction** The authors should restructure the results with clear subheadings corresponding to each major finding, and ensure every claim is tied to a specific figure or table.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Use of "motif" vs. "extended motif" vs. "sequence context"
- **Evidence pointer** Throughout, location not provided
- **Issue** The terms "motif," "extended motif," and "sequence context" are used somewhat interchangeably, which can confuse the reader about what exactly is being measured or compared.
- **Required correction** The authors should define these terms clearly at first use and use them consistently throughout.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion, location not provided
- **Issue** The discussion does not adequately address the limitations of the study, such as the use of isolated DBDs rather than full-length TFs, the lack of direct testing of the pioneer factor hypothesis, and the absence of functional validation of the co-occupancy claims.
- **Required correction** A dedicated limitations paragraph should be added to the discussion.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods, Data availability
- **Evidence pointer** Methods, location not provided
- **Issue** The manuscript does not include a data availability statement describing where the raw and processed gcPBM, ChIP-seq, and ATAC-seq data will be deposited.
- **Required correction** A data availability statement should be added, specifying repository names and accession numbers.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** All figures
- **Evidence pointer** Figures, location not provided
- **Issue** Since no figures were provided, it is impossible to assess their quality, but the text suggests that some figures may be overly complex, with multiple panels combining different data types.
- **Required correction** The authors should ensure that each figure is focused and legible, with clear labels and legends that can be understood independently of the text.

## Risk / unsupported claims
- The claim that "chromatin accessibility, epigenetic patterns, co-factor recruitment, and dimerization contribute to differential binding" for CACACA-binders is not directly tested; it is an inference from correlative data.
- The claim that AP2-LT may act as a pioneer factor is speculative and not supported by any direct experimental evidence.
- The claim that low-affinity binding to divergent motifs "may influence the co-occupancy observed in vivo" is based on in vitro data and indirect comparisons; no direct evidence is provided.
- The claim that "TF binding site selection relies on a combination of DNA sequence and chromatin features" is a reasonable synthesis, but the relative contributions of each are not quantified.
- The claim that the gcPBM approach can comprehensively interrogate all possible genomic binding sites is dependent on the completeness of the motif instance identification, which relies on the PWM cutoff and the quality of the genome annotation; this is not fully validated.
- The therapeutic implications discussed in the final paragraph of the discussion are speculative and not supported by any data in the manuscript.