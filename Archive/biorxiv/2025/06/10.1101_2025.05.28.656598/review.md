## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, data availability, author contributions, competing interests, acknowledgements, footnotes)
- **Assessment boundary** Scientific content, methodological soundness, statistical rigor, interpretation of results, and clarity of presentation as presented in the provided text
- **Shared manuscript claim summary** The authors analyze the broad sequence context (±5000 bp) around in vivo transcription factor binding sites identified by ChIP-seq and Cut&Tag experiments, and report statistically significant increases in GC content spanning 1000–1500 bp around binding sites for most TFs tested, along with directional dinucleotide frequency alterations for certain TFs (e.g., MYC), predicted DNA shape changes, and altered predicted affinities for potential cooperating TFs. They propose that these patterns represent a "statistical funnel" guiding TF scanning via facilitated diffusion.
- **Visible evidence base** Abstract, full introduction, full methods (data curation, feature extraction, statistical analysis, biological relevance assessment, clustering, sequence alignment, ATAC-seq integration), full results (GC content analysis, dinucleotide analysis, shape feature analysis, TF affinity analysis, non-B DNA analysis), discussion, conclusion, data availability statement
- **Missing materials affecting confidence** Figures 1–4 are referenced but not provided; Supplementary Figures S1–S35 and Supplementary Tables S1–S13 are referenced but not provided; specific numerical results (effect sizes, p-values, confidence intervals) are largely absent from the text; exact statistical test parameters and multiple testing correction details are incomplete

## Reviewer

### Overall assessment
This manuscript addresses an interesting and potentially important question: whether the broad sequence context around transcription factor binding sites carries statistical signals that could influence TF scanning dynamics. The authors analyze a curated set of ChIP-seq and Cut&Tag experiments across 10 TFs and multiple cell lines, examining GC content, dinucleotide frequencies, predicted DNA shape features, and predicted TF affinities in 10 kb windows centered on binding sites. The core observation, that GC content is elevated in a broad region around binding sites for most TFs tested, is potentially interesting, though it is important to note that this general phenomenon has been described previously (including by Dror et al., as the authors themselves acknowledge). The extension to dinucleotide asymmetries and shape feature predictions adds some novelty, but the manuscript has substantial methodological and interpretive weaknesses that prevent the central claims from being established. The statistical approach is described at a high level but key details are missing, the interpretation of predicted shape features as mechanistically relevant is speculative, and the connection between the observed sequence statistics and the proposed "scanning funnel" mechanism is not directly tested. The manuscript would benefit from clearer presentation of effect sizes, explicit handling of confounders (e.g., CpG islands, promoter proximity, chromatin state), and a more cautious framing of the mechanistic hypothesis.

### Who would be interested in the results, and why
Researchers studying transcription factor binding specificity, DNA shape readout, facilitated diffusion mechanisms, and the role of non-consensus sequence context in gene regulation would find this manuscript relevant. The work sits at the intersection of computational genomics, biophysics of protein-DNA interactions, and gene regulatory mechanisms. The observation that GC content and dinucleotide composition vary systematically over kilobase scales around binding sites could inform future models of TF search dynamics and binding site prediction. The methodological approach, combining ChIP-seq/Cut&Tag data with sequence feature analysis and shape prediction, may also be of interest to bioinformaticians developing tools for regulatory genomics.

### Major Strengths
1. The question addressed is of genuine interest: understanding how TFs efficiently locate their binding sites in the genome is a fundamental problem in gene regulation.
2. The dataset curation is thoughtful, with attention to experimental quality (filtering for audit flags, using conservative IDR peaks) and inclusion of a Cut&Tag experiment for method validation.
3. The analysis spans a broad sequence context (±5000 bp), which is more extensive than most previous studies that focused on immediate flanking regions.
4. The inclusion of multiple TFs with diverse DNA-binding domains and functions allows for comparative observations.
5. The authors take some steps to address confounders, such as filtering out CpG island-overlapping peaks in one analysis and cross-referencing with ATAC-seq data.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and reproducibility
- **Claim pointer** The authors claim statistically significant increases in GC content spanning 1000–1500 bp around binding sites, identified via a "cluster-based permutation test" with a cluster-forming threshold of |t| > 2.0 and 1000 permutations.
- **Evidence pointer** Methods, Statistical analysis; Results, GC content section; Table 1; Supplementary Table S3
- **Concern** The statistical methodology is described at a level of detail that is insufficient for reproducibility. Key missing elements include: (1) how the "edge" regions (first and last 500 bp) were validated as neutral, given that the authors themselves show GC content varies systematically across the 10 kb window; (2) whether the permutation procedure accounts for the non-independence of overlapping 50 bp windows (25 bp overlap); (3) how multiple testing across features, TFs, and cell lines was handled; (4) whether the cluster-forming threshold and permutation count were pre-specified or optimized; (5) the exact definition of the test statistic and how the null distribution was constructed. Without these details, the reported p-values cannot be evaluated. Furthermore, the claim that the increase spans "1000–1500 bp" appears inconsistent with the statement in the Results that the affected area "can span around 2000–4000 bp" — these numbers need to be reconciled.
- **Why it matters** The central empirical claim of the paper rests entirely on this statistical analysis. If the methodology is not fully specified and the effect sizes are not reported, the findings cannot be independently verified or compared with previous work. The discrepancy between the abstract (1000–1500 bp) and results (2000–4000 bp) further undermines confidence.
- **Resolution test** Provide a complete statistical appendix with: exact definitions of all test statistics, null distributions, and permutation schemes; explicit handling of overlapping windows; multiple testing correction details; effect sizes (e.g., mean GC content difference with confidence intervals) for each TF and cell line; and a reconciliation of the reported patch sizes. Ideally, the analysis should be made available as a reproducible workflow (e.g., Jupyter notebook or R markdown) with the underlying data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Confounding factors and causal interpretation
- **Claim pointer** The authors propose that the observed GC content elevation and dinucleotide asymmetries around binding sites reflect a "statistical funnel" that guides TF scanning via facilitated diffusion, and that these patterns are indicative of a "coarse scanning mechanism."
- **Evidence pointer** Results, GC content and dinucleotide sections; Discussion; Conclusion
- **Concern** The manuscript does not adequately address well-known confounders that could explain elevated GC content around binding sites without invoking a scanning mechanism. These include: (1) promoter and CpG island proximity — many TF binding sites are located in promoter regions, which are GC-rich; the authors mention CpG islands but do not systematically control for promoter overlap or distance to transcription start sites; (2) chromatin state — open chromatin regions are generally GC-rich, and the ATAC-seq analysis is presented only descriptively; (3) sequence composition biases in the genome overall; (4) the possibility that the observed GC content elevation simply reflects the fact that many TF binding motifs are GC-rich, and the flanking sequence composition is influenced by the same regional genomic features. The authors' own data show that the GC content effect largely disappears when controlling for predicted TF affinities (only 20–30 of >400 TFs show changes after scramble normalization), which suggests that the GC content signal may be a proxy for other features rather than a direct mechanistic driver.
- **Why it matters** The central mechanistic claim of the paper, that the observed sequence patterns represent a "statistical funnel" guiding TF scanning, requires that the patterns are not simply byproducts of genomic architecture. Without rigorous control for confounders, the interpretation is not supported.
- **Resolution test** Perform analyses that: (1) match binding sites to control regions with similar GC content, promoter proximity, and chromatin state; (2) stratify by distance to TSS and CpG island overlap; (3) compare the observed GC content elevation to what would be expected from the motif composition alone; (4) test whether the "funnel" pattern is specific to bound sites or also present at unbound motif occurrences. If the signal persists after these controls, the mechanistic interpretation becomes more plausible.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of DNA shape predictions and their interpretation
- **Claim pointer** The authors state that "the average shape of propeller twist, minor groove width, opening, stretch, stagger, roll and helical twist changes near the putative binding site" and interpret these changes as indicating "a more flexible DNA helix that is relatively more open to intercalators."
- **Evidence pointer** Results, DNA shape features section; Figure 3.3; Supplementary Tables S6–S12; Supplementary Figure S22
- **Concern** The DNA shape features are predicted using deepDNAshape, a computational tool, and the authors do not validate these predictions against experimental structural data (e.g., X-ray crystallography, NMR, or molecular dynamics simulations) for the specific sequences analyzed. The interpretation of predicted shape changes as evidence for "flexibility" and "openness to intercalators" is a significant inferential leap. The authors also report that the effect of position relative to the binding site on shape features is "minimal or almost negligible" (η² close to zero), which appears to contradict the claim that shape changes around the binding site are meaningful. If position has minimal effect, what is driving the observed shape differences? The relationship between the sequence composition changes and the predicted shape changes is not quantitatively established.
- **Why it matters** The shape analysis is presented as a key piece of evidence linking sequence composition to a structural mechanism. If the predictions are not validated and the effect sizes are negligible, this line of evidence does not support the authors' conclusions.
- **Resolution test** Validate deepDNAshape predictions on a subset of sequences with known experimental structures; report effect sizes (η²) with confidence intervals for all shape features; explicitly test whether the predicted shape changes are statistically significant after controlling for sequence composition; and temper the mechanistic interpretation to match the strength of the evidence.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability and external validity
- **Claim pointer** The authors state that the observed GC content increase around binding sites is "consistent" across experiments targeting the same TF in different cell lines, and that the pattern is shared between most cell lines.
- **Evidence pointer** Results, GC content section; Figure 2.4; Table 1; Supplementary Table S3
- **Concern** The analysis is limited to 10 TFs and a small number of cell lines, with the dataset heavily weighted toward certain TFs (e.g., CTCF, MYC) that have been studied extensively. The authors note exceptions (NANOG in GM23338, NFRKB in MCF-7) but do not explore what distinguishes these cases. The claim of consistency across cell lines is based on visual inspection of figures rather than a formal statistical test of consistency. The choice of TFs is not justified, and it is unclear whether the findings would generalize to the broader set of human TFs, particularly those with different DNA-binding domain families or those that bind as heterodimers.
- **Why it matters** The authors propose a general mechanism ("statistical funnel") that should apply broadly to TF-DNA interactions. If the pattern is not consistently observed across a diverse set of TFs and cell lines, the generality of the claim is weakened.
- **Resolution test** Expand the analysis to a larger and more diverse set of TFs; formally test for consistency across cell lines using appropriate statistical methods (e.g., mixed-effects models); report the proportion of TFs and cell lines that show the effect; and discuss potential reasons for exceptions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Alternative explanations and competing hypotheses
- **Claim pointer** The authors propose that the observed sequence patterns are indicative of a "coarse scanning mechanism" and that the "statistical funnel" guides TFs toward binding sites.
- **Evidence pointer** Discussion; Conclusion
- **Concern** The manuscript does not seriously consider alternative explanations for the observed sequence patterns. For example: (1) the GC content elevation could reflect selection for thermodynamically stable DNA in regulatory regions, independent of TF scanning; (2) the patterns could be a byproduct of nucleosome positioning or other chromatin features; (3) the dinucleotide asymmetries could reflect strand-specific mutational biases rather than functional signals; (4) the patterns could be explained by the fact that ChIP-seq peaks are enriched for certain genomic features (e.g., enhancers, promoters) that have their own sequence characteristics. The authors briefly mention that their findings are "hypothesis-generating rather than definitive," but the discussion does not engage with these alternatives in a substantive way.
- **Why it matters** A strong scientific paper should consider and rule out alternative explanations. Without this, the proposed mechanism remains one of several possible interpretations.
- **Resolution test** Add a dedicated section in the Discussion that systematically addresses alternative explanations and, where possible, performs analyses to distinguish between them (e.g., comparing binding sites in different genomic contexts, controlling for mutational biases, testing for nucleosome positioning signals).

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and precision of reporting
- **Affected element** Abstract and Results
- **Evidence pointer** Abstract; Results, GC content section
- **Issue** The abstract states the GC content increase spans "1000–1500 bp" while the Results state the affected area "can span around 2000–4000 bp." This discrepancy is confusing and should be resolved. Additionally, the abstract claims the increase is "statistically significant" but does not report effect sizes or confidence intervals, making it difficult to assess the magnitude of the effect.
- **Required correction** Reconcile the reported patch sizes between the abstract and Results. Report effect sizes (e.g., mean GC content difference with 95% confidence intervals) for the main findings in the abstract or at least in the Results section.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** Methods, Statistical analysis
- **Evidence pointer** Methods, Statistical analysis
- **Issue** The description of the cluster-based permutation test is incomplete. The authors state "cluster-forming threshold |t| > 2.0" and "1000 permutations" but do not specify the exact test statistic, how clusters were defined, or how the permutation null distribution was constructed. The use of the MNE package is mentioned but the specific function parameters are not given.
- **Required correction** Provide a complete description of the statistical procedure, including the exact test statistic, cluster definition, permutation scheme, and software parameters. Consider including pseudocode or a link to a reproducible analysis script.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability and reproducibility
- **Affected element** Data availability statement
- **Evidence pointer** Data availability
- **Issue** The data availability statement indicates that source codes and data are stored in a Zenodo archive, but the specific DOI is provided only in the footnote. The main text should include the DOI in the Data availability section for clarity.
- **Required correction** Move the Zenodo DOI (10.5281/zenodo.17900173) into the Data availability section.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality and accessibility
- **Affected element** Figures 1–4
- **Evidence pointer** Results; Figure legends (not provided)
- **Issue** The figures are referenced throughout the text but were not provided for review. Based on the text descriptions, it is unclear whether the figures include error bars, confidence intervals, or statistical annotations. The authors should ensure that all figures clearly display the statistical significance of the reported effects.
- **Required correction** Ensure all figures include appropriate error bars or confidence intervals and clearly indicate statistical significance. Provide detailed figure legends that explain all panels and annotations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Language and terminology
- **Affected element** Throughout
- **Evidence pointer** Abstract; Introduction; Discussion
- **Issue** The manuscript uses terms such as "statistical beacons," "funnel-like sequence signature," and "statistical funnel" which are evocative but not precisely defined. The relationship between these terms and the underlying statistical findings should be clarified.
- **Required correction** Define these terms explicitly when first introduced and use them consistently throughout the manuscript. Consider whether more standard terminology (e.g., "sequence context effects") would be more appropriate.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction; Discussion
- **Evidence pointer** Introduction; Discussion
- **Issue** The authors cite relevant literature on TF binding, DNA shape, and facilitated diffusion, but the discussion of previous work on GC content around binding sites is brief. The authors acknowledge Dror et al. but do not provide a systematic comparison of their findings with this and other prior studies.
- **Required correction** Expand the Discussion to include a more thorough comparison with previous studies on sequence context around TF binding sites, highlighting what is new in the present work and what confirms prior findings.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, non-B DNA section
- **Evidence pointer** Results, non-B DNA section; Figure 3.6
- **Issue** The authors report that the frequency of k-mers overlapping with Z-DNA or G-quadruplex motifs is higher at binding sites for certain TFs, but the effect sizes are described as "small" without quantitative details. The Mann-Whitney U test is mentioned but p-values are not reported in the text.
- **Required correction** Report the effect sizes and p-values for the non-B DNA analyses, and clarify whether multiple testing corrections were applied.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Methods, Clustering of peaks based on GC content
- **Evidence pointer** Methods, Clustering of peaks based on GC content
- **Issue** The clustering analysis is described briefly and its purpose is not entirely clear. The authors state that they cluster peaks from pairs of experiments and report "the result with the best accuracy," but the definition of accuracy is not provided.
- **Required correction** Clarify the purpose of the clustering analysis, define the accuracy metric, and explain how the results inform the main findings.

### Technical failings that need to be addressed before the case is established
1. Incomplete statistical methodology (R1-M1): The cluster-based permutation test is not described in sufficient detail for reproducibility, and the discrepancy in reported patch sizes (1000–1500 bp vs. 2000–4000 bp) must be resolved.
2. Inadequate control for confounders (R1-M2): The analysis does not systematically control for promoter proximity, CpG island overlap, or chromatin state, which could explain the observed GC content elevation.
3. Unvalidated DNA shape predictions (R1-M3): The deepDNAshape predictions are not validated against experimental data, and the reported minimal effect of position on shape features appears to contradict the interpretation.
4. Missing figures and supplementary materials: Figures 1–4 and all supplementary materials were not provided for review, making it impossible to fully evaluate the results.

### Assessment against Nature-style criteria
**Originality:** Moderate. The observation that GC content is elevated around TF binding sites has been reported previously (including by Dror et al., as the authors acknowledge). The extension to dinucleotide asymmetries and the proposed "statistical funnel" mechanism provides some novelty, but the core finding is not entirely new. The analysis of predicted shape features and non-B DNA conformations adds a new dimension, though the interpretation is speculative.

**Scientific importance:** Moderate. If the findings are robust, they could contribute to understanding how TFs search for their binding sites, which is a fundamental question in gene regulation. However, the mechanistic claims are not directly tested, and the practical implications for understanding TF function are not clearly articulated.

**Interdisciplinary readership:** Moderate. The work bridges computational genomics, biophysics, and molecular biology, and could appeal to researchers in these fields. However, the presentation is heavily computational and may be challenging for experimental biologists without a strong bioinformatics background.

**Technical soundness:** Weak to moderate. The statistical methodology is incompletely described, confounders are not adequately addressed, and the DNA shape predictions are not validated. The analysis of TF affinities using HOCOMOCO models is reasonable, but the interpretation of the results is not fully supported.

**Readability for nonspecialists:** Weak. The manuscript uses specialized terminology and assumes familiarity with ChIP-seq, Cut&Tag, DNA shape prediction, and facilitated diffusion concepts. The abstract is relatively accessible, but the methods and results sections would be challenging for nonspecialists.

### Recommendation posture
Currently not established from the provided evidence. The manuscript addresses an interesting question and contains potentially valuable observations, but the statistical methodology is incompletely described, confounders are not adequately controlled, and the mechanistic interpretation is not supported by the strength of the evidence. The authors should be encouraged to revise the manuscript to address these concerns, but the case for the central claims is not made in the current version.