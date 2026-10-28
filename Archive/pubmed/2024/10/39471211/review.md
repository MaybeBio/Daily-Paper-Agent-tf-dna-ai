## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Discussion, Methods, and Supporting Information references)
- **Assessment boundary** Scientific content, methodological soundness, data interpretation, and claims as presented in the provided text. No external data or supplementary files were accessed.
- **Shared manuscript claim summary** The authors map genome-wide binding of RpoD, RpoS, and RpoH in Salmonella Typhimurium under control and heat shock conditions using ChIP-mini, integrate with RNA-seq and iModulon analysis, and propose that heat shock induces anaerobic and oxidative stress responses, with RpoS expanding its regulon and competing with RpoD at shared promoters.
- **Visible evidence base** Main text figures (Fig 1A–C, 2A–C, 3A–D, 4A–D, 5A–F, 6A–D, 7A–D), Tables 1 and 2, and references to Supporting Information (S1–S11 Figs, S1–S4 Tables). Methods section describes ChIP-mini, RNA-seq, peak calling, differential binding, motif analysis, COG enrichment, and iModulon inference.
- **Missing materials affecting confidence** Supporting Information files (S1–S11 Figs, S1–S4 Tables) were not provided. Raw sequencing data, peak lists, and iModulon definitions were not accessible. This limits independent verification of several quantitative claims.

## Reviewer
- **Overall assessment** This manuscript presents a substantial dataset on sigma factor binding in Salmonella under heat shock, using a state-of-the-art ChIP-mini approach. The integration of binding, expression, and iModulon data is ambitious and potentially valuable. However, several key claims, particularly the proposed competition mechanism between RpoD and RpoS, and the inferred physiological consequences (anaerobic and oxidative stress), rest on indirect evidence and require stronger experimental or computational support. The manuscript is technically sound in its core methodology but would benefit from clearer presentation of statistical thresholds and validation of the iModulon-based inferences.
- **Who would be interested in the results, and why** Researchers in bacterial transcriptional regulation, sigma factor biology, stress response, and systems biology. The dataset on genome-wide sigma factor binding under heat shock is a useful resource. Those studying Salmonella pathogenesis and thermal adaptation would also find relevance.
- **Major strengths** 1. The use of ChIP-mini to achieve near-base-pair resolution for three sigma factors under two conditions is a technical advance. 2. The integration of binding, expression, and iModulon activity provides a multi-layered view. 3. The observation of RpoS regulon expansion under heat shock is interesting and potentially important. 4. The comparative discussion with E. coli adds context.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (competition mechanism), R1-M2 (iModulon inference), R1-M3 (RpoH binding and HSP regulation), R1-M4 (iron metabolism and oxidative stress link).
- **Assessment against Nature-style criteria** **Originality** Moderate. The application of ChIP-mini to this system is novel, but the conceptual framework (sigma factor competition, stress cross-talk) is established. **Scientific importance** Moderate to high. The dataset is valuable, but the conceptual advances are incremental. **Interdisciplinary readership** Limited. Primarily of interest to microbiologists and systems biologists. **Technical soundness** Generally sound, but with gaps in validation of key inferences. **Readability for nonspecialists** The manuscript is dense and assumes significant background in bacterial genetics and bioinformatics. The abstract is accessible, but the results section would be challenging for a general reader.
- **Recommendation posture** Supportive if technical concerns are resolved. The core dataset is valuable, but the major claims require stronger evidence or more careful qualification.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation / Overclaiming
- **Claim pointer** The authors claim a competition mechanism between RpoD and RpoS at shared promoters under heat shock, based on overlapping binding sites and correlated binding intensity changes.
- **Evidence pointer** Results section, Fig 3A–D, S3C Fig
- **Concern** The evidence for competition is correlative. Overlapping binding sites and similar intensity changes do not demonstrate competition. Competition requires showing that increased RpoS binding leads to decreased RpoD binding (or vice versa) in a causal manner, ideally through perturbation experiments (e.g., overexpression or depletion of one sigma factor) or time-course analysis. The correlation (r2 = 0.76 for DBPs) could also be explained by co-regulation or shared promoter architecture without direct competition.
- **Why it matters** The competition mechanism is a central claim of the paper, highlighted in the abstract and discussion. If not substantiated, the paper's conceptual contribution is weakened.
- **Resolution test** Provide direct experimental evidence, such as ChIP-seq or ChIP-mini in strains with altered RpoS levels (e.g., rpoS overexpression or conditional depletion) to show reciprocal changes in RpoD binding at shared promoters. Alternatively, use an in vitro competition assay with purified sigma factors and RNA polymerase. At minimum, the authors should temper the claim to "consistent with competition" and discuss alternative explanations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology / Validation
- **Claim pointer** The authors use iModulon activity inference to decompose the transcriptional impact of heat shock and to support claims about anaerobic and oxidative stress.
- **Evidence pointer** Results section, Fig 1A, 5A, 7A, Methods section "Inferring activity of iModulons"
- **Concern** The iModulon analysis relies on a pre-existing compendium and the PyModulon package. The manuscript does not provide sufficient detail on the quality control of this inference for the new dataset. Specifically, how well do the four new expression profiles fit the existing iModulon structure? What is the confidence interval for the inferred activities? The authors state that non-overlapping genes were ignored, but the proportion of ignored genes is not reported. This could bias the activity estimates.
- **Why it matters** The iModulon analysis is used to support major conclusions about the physiological nature of the heat shock response (anaerobic and oxidative stress). If the inference is unreliable, these conclusions are unsupported.
- **Resolution test** Provide a detailed assessment of the iModulon inference, including the number of genes used, the reconstruction error, and confidence intervals for activity changes. Ideally, validate key iModulon activity changes (e.g., Fnr-1, Fur) with independent methods, such as qRT-PCR of known target genes or reporter assays.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data Interpretation
- **Claim pointer** The authors state that HSP genes are primarily regulated by increased RpoH binding at promoter regions in response to heat shock.
- **Evidence pointer** Results section, Fig 4A–D
- **Concern** The analysis identifies nine HSP genes bound by RpoH under both conditions. However, the claim of "primarily regulated by increased RpoH binding" is not fully supported. The authors show increased binding intensity, but do not directly demonstrate that this increased binding is necessary or sufficient for the observed expression changes. Other factors, such as mRNA stability or changes in RNA polymerase availability, could contribute. Furthermore, the analysis of HSP genes without RpoH binding (e.g., clpA, clpS, hslJ, hslRO) is brief and does not explore alternative regulatory mechanisms.
- **Why it matters** This is a key part of the sigma factor story. If the causal link between RpoH binding and HSP expression is not established, the paper's central narrative is weakened.
- **Resolution test** Perform a more detailed analysis, such as comparing RpoH binding intensity changes with the magnitude of expression changes for each HSP gene. Consider using a statistical model to assess the contribution of RpoH binding versus other factors. Alternatively, discuss the limitations of the correlative approach more explicitly.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evidence Strength
- **Claim pointer** The authors propose that heat shock induces anaerobic stress, leading to downregulation of ETC genes, and that iron metabolism is regulated to mitigate oxidative stress.
- **Evidence pointer** Results section, Fig 5A–F, 7A–D
- **Concern** The link between heat shock and anaerobic stress is inferred primarily from iModulon activity (Fnr-1) and expression changes of ETC genes. While plausible, this is an indirect inference. The authors do not measure oxygen levels, redox state, or other direct indicators of anaerobic stress. Similarly, the connection between iron metabolism regulation and oxidative stress mitigation is inferred from gene expression patterns and the known role of iron in Fenton chemistry, but no direct measurements of reactive oxygen species or oxidative damage are provided.
- **Why it matters** These claims extend the significance of the work beyond simple transcriptional regulation to physiological stress responses. Without direct evidence, they remain speculative.
- **Resolution test** Provide direct measurements of relevant physiological parameters, such as intracellular oxygen levels, reactive oxygen species, or metabolic fluxes. Alternatively, clearly frame these as hypotheses generated by the data, rather than established conclusions.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "we observed a significant expansion of the RpoD sigmulon from 97 to 301 genes" but this is a typo; it should be RpoS sigmulon.
- **Required correction** Correct the typo in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology / Reporting
- **Affected element** Methods section, ChIP-mini experiment
- **Evidence pointer** Methods section
- **Issue** The Methods state that ChIP-mini experiments were performed in biological duplicate. For a genome-wide binding study, two biological replicates may be insufficient to ensure reproducibility, especially for detecting subtle changes in binding intensity. The authors should justify this choice or acknowledge the limitation.
- **Required correction** Add a sentence justifying the use of biological duplicates or acknowledge this as a limitation in the Discussion.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data Presentation
- **Affected element** Results section, Fig 3C
- **Evidence pointer** Fig 3C
- **Issue** The authors state that 97 out of 301 RpoS sigmulon genes have both RpoD and RpoS binding sites upstream. The significance of this proportion is not discussed. Is this enrichment compared to the genome-wide average?
- **Required correction** Provide a statistical comparison of the overlap proportion against a genomic background to strengthen the claim of competition.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section, Fig 5A
- **Evidence pointer** Fig 5A
- **Issue** The description of the Fnr-1 iModulon activity under anaerobic shock and growth conditions is brief. It is unclear how these conditions relate to the heat shock condition used in this study.
- **Required correction** Clarify the relevance of the anaerobic shock and growth conditions to the heat shock experiments.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The comparison with E. coli is interesting but brief. The authors note differences in gene expression preferences but do not explore the potential reasons for these differences.
- **Required correction** Expand the discussion on the E. coli comparison, considering differences in regulatory network architecture or physiological context.

## Risk / unsupported claims
- The proposed competition mechanism between RpoD and RpoS at shared promoters is not directly demonstrated and is currently an interpretation of correlative data.
- The claim that heat shock induces anaerobic stress is inferred from iModulon activity and gene expression, without direct physiological measurements.
- The claim that iron metabolism regulation mitigates oxidative stress is inferred from gene expression patterns, without direct measurements of oxidative damage.
- The iModulon activity inference for the new dataset is not fully validated, and the proportion of genes used in the analysis is not reported.
- The functional significance of the expanded RpoS sigmulon (301 genes) is not experimentally validated.