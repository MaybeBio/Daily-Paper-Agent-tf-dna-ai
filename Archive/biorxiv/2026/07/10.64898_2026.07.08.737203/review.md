## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, limitations, methods, data availability, and footnotes
- **Assessment boundary** Scientific content, methodological rigor, statistical validity, and clarity of claims as presented in the provided text
- **Shared manuscript claim summary** The authors propose that a transcription factor's physical integration into the TF–TF interaction network, quantified as "module fraction," positively predicts the degeneracy of its DNA-binding motif, measured as genome-wide predicted binding-site density, in Drosophila melanogaster
- **Visible evidence base** Abstract, full narrative text of all sections, figure references (Figures 1–5), statistical values reported inline, methodological descriptions
- **Missing materials affecting confidence** Figures and tables themselves, supplementary materials, code repository contents, raw data files, exact JASPAR version details, STRING evidence channel file structure

## Reviewer

- **Overall assessment** This manuscript addresses a genuinely interesting and under-explored question in transcription factor biology: whether the degree to which a TF is embedded in a physical interaction network with other TFs predicts the degeneracy of its DNA-binding motif. The authors report a statistically significant positive correlation between their "module fraction" metric and genome-wide predicted binding-site density, and they present an extensive battery of robustness checks. The writing is clear and the authors are commendably honest about limitations. However, the central claim rests on a correlational analysis whose biological interpretation is complicated by several unresolved issues, including the use of predicted rather than empirical binding data, the uncertain direction of causality, and the possibility that the observed relationship reflects a more parsimonious underlying variable such as TF family size or evolutionary conservation. The methodological finding regarding fixed PWM score thresholds is useful and likely of independent interest. Overall, the work is promising but the case is not fully established from the provided evidence.

- **Who would be interested in the results, and why** Researchers studying transcription factor binding specificity, gene regulatory network evolution, and the relationship between protein interaction architecture and DNA recognition would find this work relevant. The methodological caution about PWM thresholding artifacts is broadly applicable to any genome-wide motif analysis. The proposed "division of labor" framework between intrinsic motif information and extrinsic interaction-based specificity could interest those working on combinatorial regulation and enhancer logic. The paper may also appeal to computational biologists developing predictive models of TF binding.

- **Major strengths** The question is well-posed and addresses a gap in the literature. The authors take evident care with confound control, including family-level cluster bootstrapping, exclusion of major TF families, and adversarial checks against tautology. The decision to restrict STRING evidence to physical interaction channels is methodologically sound and well-justified. The identification and documentation of the fixed-threshold artifact is a valuable contribution. The authors are transparent about limitations and report attenuated effect sizes honestly.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Validity of the central claim
- **Claim pointer** The manuscript claims that "module fraction showed a significant positive association with binding-site density (partial r = 0.379, P = 5.6e-11) after controlling for motif information content, network degree, and literature bias."
- **Evidence pointer** Results section, first paragraph; Figure 1
- **Concern** The central outcome variable, "genome-wide predicted binding-site density," is derived from JASPAR2026 PWM predictions, not from empirical binding measurements. The authors acknowledge this in the Limitations section, but the concern is more fundamental than a simple caveat. Predicted binding-site density is a function of the PWM itself, and PWMs are constructed from known binding data. The relationship between module fraction and predicted site density could reflect a bias in how PWMs are constructed for TFs that are well-studied in interaction networks, rather than a genuine biological relationship. The authors control for "annotation-text length" as a literature-attention proxy, but this may not fully capture the ascertainment bias inherent in PWM construction. The claim as stated implies a biological relationship between interaction network position and DNA-binding degeneracy, but the evidence base is entirely computational and predicted.
- **Why it matters** If the relationship only holds for predicted sites and not for empirically measured occupancy, the biological interpretation is substantially weakened. The authors themselves note that the relationship between predicted density and true occupancy is "an open question." Without validation against ChIP-seq or similar data, the central claim cannot be considered established.
- **Resolution test** The authors should either (a) validate the relationship using empirical binding data (e.g., ChIP-seq peak counts or occupancy measurements) for at least a subset of TFs, or (b) demonstrate that the relationship holds when using a binding-site density measure that is independent of PWM construction biases, such as conservation-weighted motif occurrences or experimentally derived position frequency matrices from independent sources.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical independence and confounding
- **Claim pointer** The manuscript claims that the relationship between module fraction and binding-site density persists after controlling for motif information content, network degree, and literature bias, and after excluding the homeodomain family.
- **Evidence pointer** Results section, first and third paragraphs; Figures 1, 2, and 5
- **Concern** The family-level cluster bootstrap is described as the key correction for non-independence of TF observations, but the authors themselves report that in one replication the 95% confidence interval "narrowly included zero." This is presented as a limitation, but it is a serious one. The number of DNA-binding-domain families is small (roughly a dozen), and the bootstrap is therefore imperfectly powered. More fundamentally, the analysis does not appear to control for evolutionary conservation or sequence constraint at the motif level. TFs with more conserved, functionally constrained binding motifs may be both less degenerate and less likely to have evolved extensive interaction networks, or vice versa. The relationship between module fraction and site density could be confounded by the evolutionary age or constraint of the TF family. The authors control for family membership via bootstrapping, but this does not address the possibility that the relationship is driven by a continuous underlying variable such as evolutionary rate.
- **Why it matters** The central claim is that interaction network position predicts binding degeneracy. If the relationship is confounded by evolutionary constraint or family-specific properties that are not captured by the coarse family-level bootstrap, the interpretation is incorrect. The authors' own admission that the bootstrap interval can include zero in some replications undermines confidence in the robustness of the finding.
- **Resolution test** The authors should (a) report the family-level bootstrap results more completely, including the distribution of bootstrap estimates and the proportion of replications with positive values, (b) add controls for evolutionary conservation (e.g., phyloP scores at motif positions, dN/dS ratios for TF orthologs), and (c) test whether the relationship holds within individual large families (e.g., zinc finger, bHLH) with sufficient sample sizes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation and mechanism
- **Claim pointer** The manuscript proposes a "division of labor" model in which TFs embedded in interaction-rich modules tolerate more degenerate motifs, while network-generalist TFs rely on more information-rich motifs.
- **Evidence pointer** Discussion section, final paragraph
- **Concern** The proposed model is presented as a plausible interpretation, and the authors are appropriately cautious. However, the model is not tested in any direct way. The correlation between module fraction and site density is consistent with the model, but it is also consistent with alternative explanations. For example, TFs with degenerate motifs may be older, more pleiotropic genes that have accumulated more interaction partners over evolutionary time, with no causal relationship between interaction network position and motif degeneracy. The authors do not test whether the relationship is specific to TF–TF interactions as opposed to general protein interaction degree, nor do they examine whether the relationship holds for non-TF DNA-binding proteins. The mechanistic link to IDR-mediated condensates is speculative and explicitly acknowledged as such.
- **Why it matters** The paper's broader significance depends on the biological interpretation. If the relationship is causal and reflects a genuine trade-off between interaction-based and sequence-based specificity, it would be an important insight. If it is a correlational byproduct of other factors, the paper's contribution is more limited.
- **Resolution test** The authors should (a) test whether the relationship is specific to TF–TF interactions by comparing with general protein interaction degree or non-TF interaction partners, (b) examine whether the relationship holds for DNA-binding proteins that are not classified as TFs, and (c) if possible, test the IDR hypothesis by correlating predicted disorder content with module fraction and site density.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological transparency and reproducibility
- **Claim pointer** The manuscript states that "all analysis code is provided in full" and that the pipeline "reproduces every result and figure in this manuscript end-to-end from the raw STRING, JASPAR, phyloP, GTF, and FlyBase input files."
- **Evidence pointer** Methods section, Data and Code Availability section
- **Concern** The code repository is referenced by a URL in the footnotes, but the manuscript text does not provide sufficient detail for a reader to assess the code independently. The methods describe the pipeline in general terms, but key parameters are not fully specified. For example, the exact regular expressions used for TF identification and family classification are not provided in the text. The criteria for "confirmed by name-matching against JASPAR" are not detailed. The construction of the "two independent ~18 Mb genomic samples" is described, but the exact genomic coordinates and filtering criteria are not given. The JASPAR2026 version and the specific PWM scoring method are not fully described. Without these details, the reproducibility claim cannot be fully evaluated.
- **Why it matters** Reproducibility is a core requirement for computational biology papers. The authors' claim of full reproducibility is strong, but the manuscript text alone does not provide enough information for a reader to verify it. The code repository may contain all necessary details, but the manuscript should provide sufficient information for assessment.
- **Resolution test** The authors should (a) provide the exact regular expressions and matching criteria in the methods or supplementary material, (b) specify the exact genomic coordinates and construction criteria for the 18 Mb samples, (c) provide the JASPAR2026 version and PWM scoring details, and (d) ensure the code repository is publicly accessible and includes a README with version information for all dependencies.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract states that TFs recognize "short, degenerate DNA motifs that occur thousands of times throughout the genome." This is presented as a general fact, but the degree of degeneracy varies substantially across TFs, and some motifs are relatively information-rich. The phrasing could be more precise.
- **Required correction** Consider revising to acknowledge the range of motif degeneracy across TFs, e.g., "Transcription factors recognize DNA motifs that are typically short and often substantially degenerate, occurring thousands of times throughout the genome."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section, first paragraph
- **Evidence pointer** Results section, first paragraph
- **Issue** The manuscript reports raw and partial correlation coefficients with p-values but does not report confidence intervals for the main correlations. Given the authors' emphasis on robustness and honest reporting, confidence intervals would strengthen the presentation.
- **Required correction** Add 95% confidence intervals for the key correlation coefficients (raw and partial) in the main text or figure legends.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results section, fourth paragraph
- **Evidence pointer** Results section, fourth paragraph
- **Issue** The term "hyper-assortative" is used to describe the TF–TF interaction enrichment. This is not a standard term in network biology, and its meaning may not be immediately clear to all readers.
- **Required correction** Define the term on first use or use a more standard phrasing such as "strongly assortative" or "significantly enriched for TF–TF edges relative to degree-matched expectation."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, first paragraph
- **Evidence pointer** Introduction, first paragraph
- **Issue** The introduction cites references [1–7] for the general properties of TF binding motifs and the specificity problem, but does not cite any of the recent large-scale studies on TF binding specificity prediction or the relationship between motif degeneracy and regulatory complexity. The introduction would benefit from a more current and comprehensive literature context.
- **Required correction** Add citations to recent reviews or primary studies on TF binding specificity, motif degeneracy, and the role of protein interactions in determining binding location.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1–5
- **Evidence pointer** Figures 1–5 (referenced in text)
- **Issue** The figures are referenced but not provided in the manuscript text. The figure legends are not included. Without seeing the figures, it is difficult to assess the quality of the visual presentation and whether the data support the claims made in the text.
- **Required correction** Ensure that figures and their legends are included in the manuscript or supplementary material, and that they clearly display the data with appropriate axis labels, error bars, and statistical annotations.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and Code Availability section
- **Evidence pointer** Data and Code Availability section
- **Issue** The section states that the code is provided at a GitHub URL, but the URL is only given in the footnotes. The manuscript text should include the URL or a persistent identifier (e.g., DOI) in the Data and Code Availability section itself.
- **Required correction** Include the full URL or a DOI in the Data and Code Availability section.

## Risk / unsupported claims
- The claim that "TF module fraction showed a significant positive association with binding-site density" is supported by the reported statistics, but the biological interpretation of this correlation as evidence for a "division of labor" model is not established and is acknowledged by the authors as a hypothesis.
- The claim that the relationship is not an artifact of TF family size is supported by the family-level cluster bootstrap, but the authors themselves note that the bootstrap is imperfectly powered and that in one replication the confidence interval included zero. This claim should be considered only partially supported.
- The claim that the fixed-threshold artifact is "likely to recur in any similar genome-wide, multi-motif binding-site counting exercise" is plausible but is presented without a systematic survey of existing methods. This is a reasonable cautionary statement, but it is not a demonstrated claim.
- The claim that the TF–TF interaction enrichment "far exceeds degree-matched random expectation" is supported by the reported z-scores, but the manuscript does not provide details on the number of permutations or the stability of the z-score estimates across different random seeds.
- The claim that the physical-evidence network is "largely independent" of the direct interaction screens by Rhee et al. and Shokri et al. is not fully supported. STRING's database channel may incorporate data from those very screens, and the manuscript does not provide an analysis of the overlap between the STRING-derived network and the published interaction sets.
- The claim that "expression breadth is an independently measured, theoretically related axis" is reasonable, but the composite index combining module fraction and inverse expression breadth is a derived metric whose properties are not fully characterized. The manuscript does not report the correlation between the two components of the composite index, which would be informative for interpreting the composite results.