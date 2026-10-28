## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific claims, methodology, and interpretation as presented in the provided text; no external data or supplementary figures were independently verified
- **Shared manuscript claim summary** The authors analyze 6,153 ENCODE ChIP-seq datasets to identify nuclear transcription factors (TFs) with evidence of occupancy over the mitochondrial genome (chrM), reporting 50 sequence-specific TFs and two other chromatin proteins with putative chrM association, with bZIP family members most strongly represented. They emphasize variable reproducibility across antibodies and protocols, and propose criteria for evaluating chrM occupancy evidence.
- **Visible evidence base** Main text figures referenced (Figures 1–15), supplementary figures (Supplementary Figures 1–56), methods section, abstract, introduction, results, discussion
- **Missing materials affecting confidence** Supplementary figures and tables not provided; detailed peak-calling thresholds and statistical significance criteria not fully specified; UCSC Track Hub data not accessed; no raw data or code availability beyond a track hub URL

## Reviewer
- **Overall assessment** This manuscript provides a valuable and timely update to the compendium of nuclear TFs potentially occupying the mitochondrial genome, leveraging a substantially expanded ENCODE dataset and incorporating deep learning predictions. The systematic documentation of reproducibility issues across antibodies and protocols is a useful contribution. However, the evidence for chrM occupancy for most TFs rests on ChIP-seq alone, and the authors themselves note widespread non-replication. The manuscript would benefit from clearer criteria for distinguishing genuine occupancy from artifacts, quantitative metrics for reproducibility, and a more explicit framework for how the field should validate candidate mtDNA-binding TFs. The deep learning predictions are presented as corroborative but are not systematically validated against independent experimental data in the visible text.
- **Who would be interested in the results, and why** Researchers studying mitochondrial biology, transcription regulation, and the growing phenomenon of nuclear-encoded proteins localizing to mitochondria. The compendium will be a reference for those investigating TF moonlighting functions and for methodologists developing standards for ChIP-seq analysis of repetitive or high-copy genomic regions. The discussion of reproducibility criteria will interest the broader genomics community.
- **Major strengths** 1) Comprehensive and systematic analysis of a large, publicly available dataset. 2) Inclusion of deep learning predictions as an orthogonal computational approach. 3) Honest and critical assessment of the limitations of ChIP-seq evidence for chrM occupancy, including documentation of non-reproducibility. 4) Clear identification of bZIP TFs as a family of particular interest. 5) Practical discussion of evidential standards for future studies.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (reproducibility criteria), R1-M2 (deep learning validation), R1-M3 (quantitative thresholds), R1-M4 (artifact exclusion)
- **Assessment against Nature-style criteria** **Originality**: Moderate to high. The question of nuclear TF occupancy of mtDNA is not new, and the authors build directly on their prior work. The novelty lies in the scale of the updated analysis and the application of deep learning, but the conceptual advance is incremental. **Scientific importance**: Moderate. The findings are of interest to a specialized community and may inform future studies on mitochondrial regulation, but the lack of functional validation and the unresolved reproducibility issues limit the immediate impact. **Interdisciplinary readership**: Limited. The manuscript is written for a specialist audience familiar with ChIP-seq, TF biology, and mitochondrial genetics. The broader significance for cell biology or medicine is not articulated. **Technical soundness**: Generally sound in terms of data processing and computational modeling, but the lack of quantitative reproducibility metrics and the unresolved artifact concerns weaken the central claims. **Readability for nonspecialists**: The abstract and introduction are accessible, but the results section is dense and assumes substantial background knowledge. The discussion is clear and helpful.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a useful resource and an honest assessment of evidence quality, but the central claims of chrM occupancy for 50 TFs require more rigorous quantitative support and clearer criteria for distinguishing signal from artifact. The deep learning component needs validation against independent data. If these issues are addressed, the manuscript would be a valuable contribution to the field.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and evidence strength
- **Claim pointer** The manuscript claims evidence for chrM occupancy for 50 sequence-specific TFs and two other proteins, but also documents widespread non-replication across antibodies, protocols, and cell lines.
- **Evidence pointer** Results sections on bZIP, bHLH, RFX, C2H2 zinc finger, and other TF families; Discussion section
- **Concern** The authors report that for many TFs, chrM peaks are observed in some experiments but not others, even when the same antibody is used. For example, JUND peaks are seen in K562, HepG2, and SK-N-SH but not in multiple other cell lines, and additional K562 datasets do not replicate the finding. Similarly, ATF2 shows peaks with some antibodies but not others. The manuscript lacks a systematic, quantitative assessment of reproducibility across all 50 TFs. The authors state that "in many cases occupancy profiles are not replicated in all cases where multiple immune reagents have been used," but do not provide a summary statistic or a clear framework for how a reader should weigh conflicting evidence.
- **Why it matters** The central claim of the manuscript is the identification of TFs with evidence for chrM occupancy. If the evidence is not reproducible across experiments, the claim is substantially weakened. Without a quantitative reproducibility metric, it is impossible to distinguish TFs with robust support from those with isolated, potentially artifactual signals. The authors' own discussion acknowledges this problem, but the results section does not resolve it.
- **Resolution test** Provide a quantitative summary of reproducibility for each of the 50 TFs, such as the number of experiments with and without peaks, stratified by antibody, protocol, and cell line. Define a priori criteria for what constitutes "reproducible" evidence (e.g., peaks in at least two independent experiments with different antibodies or orthogonal methods). Reclassify TFs based on these criteria and present the results in a summary table.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Computational model validation
- **Claim pointer** The manuscript uses BPNet deep learning models to predict chrM occupancy and states that predictions "corroborate" experimental observations for several TFs.
- **Evidence pointer** Results sections; Methods section "BPNet model training and predictions"
- **Concern** The BPNet models are trained on nuclear genome data and then applied to predict chrM occupancy. The manuscript does not provide any validation of these predictions against independent experimental data beyond the ChIP-seq datasets used for comparison. For several TFs (e.g., BHLHE40, MITF), the observed peaks do not match BPNet predictions, and the authors note this discrepancy. However, for TFs where predictions and observations align, the manuscript does not demonstrate that the models are specifically accurate for chrM, as opposed to reflecting general sequence features. The models are described as "state-of-the-art," but no metrics of prediction accuracy on held-out chrM data are provided.
- **Why it matters** The deep learning predictions are presented as a key methodological innovation and as corroborative evidence. If the models are not validated for chrM, their contribution to the central claims is unclear. The discrepancies between predictions and observations for some TFs also raise questions about the reliability of the models for this application.
- **Resolution test** Provide quantitative validation of BPNet predictions on chrM, such as area under the precision-recall curve or similar metrics, using held-out ChIP-seq datasets. For TFs where predictions and observations disagree, discuss potential reasons (e.g., model limitations, indirect binding, artifacts) and how this affects the interpretation. If validation is not possible, clearly state the limitations of the computational predictions and reduce their weight in the evidence assessment.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative thresholds and statistical significance
- **Claim pointer** The manuscript identifies "strong peaks," "weak peaks," and "elevated signal" for various TFs over chrM, but does not define quantitative thresholds for these categories.
- **Evidence pointer** Results sections throughout; Methods section "Screening for TF occupancy over the mitochondrial genome"
- **Concern** The screening process is described as manual examination of Circos plots to identify "likely TF occupancy events" and to "screen out potentially artifactual high ChIP signal localization events." This approach is subjective and does not provide quantitative criteria for what constitutes a genuine peak. The manuscript does not report peak heights, enrichment over input, or statistical significance for any of the identified peaks. The distinction between "strong" and "weak" peaks is not defined.
- **Why it matters** Without quantitative thresholds, the reader cannot assess the strength of evidence for any individual TF. The manual screening approach is not reproducible by other researchers and may introduce bias. The lack of statistical significance testing means that some reported peaks could be due to noise or artifacts.
- **Resolution test** Define and apply quantitative criteria for peak calling over chrM, such as fold enrichment over input, Poisson or negative binomial significance thresholds, and minimum peak width. Report these metrics for all identified peaks in a supplementary table. If manual screening is retained, provide a detailed protocol and inter-rater reliability assessment.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Artifact exclusion
- **Claim pointer** The manuscript acknowledges that the D-loop region shows "enriched" signal in nearly all ChIP datasets and attributes this to an artifact, but does not systematically address other potential sources of artifact.
- **Evidence pointer** Results section "Evaluating the evidence for mitochondrial occupancy of nuclear TFs in the expanded ENCODE ChIP-seq collection"; Discussion section
- **Concern** The authors identify the D-loop artifact but do not discuss other potential sources of false positives, such as mitochondrial DNA copy number variation between cell lines, cross-reactivity of antibodies with mitochondrial proteins, or non-specific binding of antibodies to mitochondrial membranes. The manuscript also does not address the possibility that some peaks could arise from NUMTs (nuclear mitochondrial DNA segments) despite the mapping strategy. The authors state that mapping was done against an index containing the mitochondrial genome, but the details of how multi-mapping reads were handled are not fully described.
- **Why it matters** If artifacts are not systematically excluded, the list of 50 TFs may include false positives. The manuscript aims to provide a reliable compendium, and failure to address known artifact sources undermines this goal. The discussion of the D-loop artifact is useful but incomplete.
- **Resolution test** Describe and implement a comprehensive artifact exclusion strategy, including: (a) assessment of mtDNA copy number in each cell line and normalization of ChIP signals accordingly; (b) testing antibody specificity against mitochondrial protein extracts; (c) explicit handling of multi-mapping reads and exclusion of NUMT-derived signals; (d) comparison with input DNA controls for all datasets. Present the results of these controls in supplementary materials.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Abstract and Results
- **Evidence pointer** Abstract; Results sections
- **Issue** The term "occupancy" is used throughout, but the manuscript does not define what constitutes occupancy in the context of ChIP-seq over chrM. Does it mean direct DNA binding, or could it include indirect association via protein-protein interactions?
- **Required correction** Define "occupancy" operationally in the context of this study, and discuss the limitations of ChIP-seq in distinguishing direct from indirect binding.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results sections
- **Evidence pointer** Figures 2–15
- **Issue** The manuscript refers to "strong," "weak," and "moderate" peaks without a consistent scale or definition. This makes it difficult to compare across TFs and experiments.
- **Required correction** Use a consistent quantitative scale (e.g., peak height relative to input, or a standardized score) and define thresholds for qualitative descriptors.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of reporting
- **Affected element** Methods
- **Evidence pointer** Methods section "ChIP-seq data processing"
- **Issue** The mapping strategy is described as using an index containing the mitochondrial genome, but the exact reference (e.g., hg38 chrM sequence) and the handling of reads that map to both nuclear and mitochondrial genomes are not fully specified.
- **Required correction** Provide full details of the reference sequence used, the mapping parameters, and the criteria for assigning reads to chrM versus nuclear genome.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of negative results
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The manuscript notes that many TFs previously proposed to act in mitochondria (e.g., GR, ERα, CREB, STAT3, p53) show no evidence of chrM occupancy in the ENCODE data, but does not discuss the implications of these negative results in detail.
- **Required correction** Discuss possible reasons for the discrepancy (e.g., cell-type-specific effects, limitations of ChIP-seq, indirect mechanisms) and how the field should interpret the lack of ChIP-seq evidence.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility of data
- **Affected element** Data availability
- **Evidence pointer** Data availability section
- **Issue** The data availability statement provides a UCSC Track Hub URL but does not mention whether the underlying ChIP-seq data, processed files, or analysis scripts are available in a public repository.
- **Required correction** Provide a clear statement on the availability of raw and processed data, as well as analysis code, in a recognized public repository.

## Risk / unsupported claims
- The claim of chrM occupancy for 50 TFs is not quantitatively supported due to lack of defined thresholds and reproducibility metrics.
- The use of BPNet predictions as corroborative evidence is not validated for chrM, and discrepancies with experimental data are not systematically addressed.
- The assertion that the D-loop signal is "certainly an artifact" is presented without direct experimental evidence, although the reasoning is plausible.
- The statement that bZIP TFs are "most likely to be playing a role in mitochondria" is speculative and not supported by functional data.
- The claim that the compendium is "the most comprehensive" is not verifiable without a systematic comparison to other published datasets or compendia.