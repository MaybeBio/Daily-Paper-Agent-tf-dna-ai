## Review setup
- **Input scope** Full manuscript text (abstract, background, results, discussion, methods, declarations)
- **Assessment boundary** Scientific claims, experimental design, data analysis, and interpretation as presented in the provided text
- **Shared manuscript claim summary** The authors propose that H3.3, deposited at promoter-proximal regulatory elements via the HIRA chaperone complex, contributes to chromatin accessibility, transcription factor binding, and downstream chromatin features (p300, H3K27ac, BRD4, RNAPII engagement) in mouse embryonic stem cells. They further propose that H3.3 is dispensable for maintaining established gene regulatory networks but required for establishing new TF binding patterns during differentiation.
- **Visible evidence base** Results sections describe ATAC-seq, ChIP-seq, GRO-seq, and RNA-seq analyses. Figures referenced: Fig. 1A-E, Fig. S1A-I, Fig. S2A-C, Fig. S3, Fig. 2A-D, Fig. S4, Fig. S5A-E, Fig. 3A-F, Fig. S6A-M, Fig. 4A-B, Fig. 5A-B, Fig. S7A-D. Tables referenced: Table S1, Table S2, Table S3.
- **Missing materials affecting confidence** Figure panels and actual data plots are not provided. Statistical details (effect sizes, confidence intervals, exact p-values) are not fully reported in the text. ChIP-seq quality metrics (e.g., FRiP scores, signal-to-noise ratios) are not described. Details on ATAC-seq replicate numbers for each condition are not fully specified. The manuscript is a preprint and has not undergone peer review.

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question regarding the functional contribution of the histone variant H3.3 to chromatin accessibility and transcription factor binding at promoter-proximal regulatory elements. The authors present a comprehensive set of genomic analyses in mouse embryonic stem cells, integrating ATAC-seq, ChIP-seq, GRO-seq, and RNA-seq data. The central claims are plausible and consistent with prior literature, but the evidence as presented in the text is largely descriptive and correlative. The manuscript would benefit from additional mechanistic dissection and clearer presentation of effect sizes. The differentiation experiments are conceptually important but require more detailed analysis to support the claim that H3.3 is specifically required for establishing new TF binding patterns.
- **Who would be interested in the results, and why** Researchers studying chromatin biology, histone variants, transcription factor dynamics, and epigenetic regulation of cell fate decisions. The findings are also relevant to those interested in the mechanisms underlying developmental transitions and the role of chromatin in disease, given the links between H3.3 mutations and pediatric cancers and neurological disorders.
- **Major strengths** The study addresses a significant gap in understanding the functional role of H3.3 at promoters. The use of multiple complementary genomic approaches (ATAC-seq, ChIP-seq, GRO-seq) is appropriate. The inclusion of chaperone-specific knockouts (HIRA, ATRX, DAXX) provides genetic evidence linking H3.3 deposition pathways to the observed phenotypes. The differentiation experiments extend the findings to a physiologically relevant context.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (effect size and statistical rigor), R1-M2 (causality), R1-M3 (differentiation analysis), R1-M4 (data availability)
- **Assessment against Nature-style criteria** Originality: The question of H3.3 function at promoters is not entirely new, but the systematic integration of accessibility, TF footprinting, and chromatin marks in the context of chaperone-specific knockouts provides a useful contribution. Scientific importance: Understanding how histone variants contribute to regulatory element function is of broad interest. Interdisciplinary readership: The topic is relevant to chromatin biologists, developmental biologists, and those studying gene regulation. Technical soundness: The genomic methods are standard and appropriate, but the analysis as described lacks sufficient statistical detail and causal evidence. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some sections assume familiarity with genomic terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core observations are potentially interesting, but the current evidence does not fully establish the causal role of H3.3 in the proposed pathway.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and effect size
- **Claim pointer** The authors claim "subtle yet widespread promoter dysregulation" and "reduced chromatin accessibility" in H3.3 KO cells.
- **Evidence pointer** Fig. 1B-E, Fig. S1B, Fig. S2A
- **Concern** The text describes changes as "subtle" and "slight" but does not provide quantitative effect sizes or confidence intervals. The number of differentially accessible regions (335) is reported, but the magnitude of change at these regions is not described. Without effect sizes, it is difficult to assess the biological significance of the observed changes.
- **Why it matters** The central claim of the paper is that H3.3 contributes to chromatin accessibility. If the effect is very small, it may not be biologically meaningful, or it may be driven by a small subset of regions. The current presentation does not allow the reader to evaluate this.
- **Resolution test** Provide effect sizes (e.g., mean fold change in ATAC-seq signal at H3.3-dependent regions), confidence intervals, and a clear description of the distribution of changes. Show representative genome browser tracks for individual loci to illustrate the magnitude of the effect.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors state that "H3.3 itself plays a role in regulating histone acetylation at promoters" and propose a pathway from H3.3 deposition to TF binding to p300 recruitment to H3K27ac.
- **Evidence pointer** Fig. 3A-F, Fig. S6A-M
- **Concern** The data are correlative. The authors show that H3.3 KO leads to reduced p300, H3K27ac, and BRD4, but they do not demonstrate that these changes are downstream of reduced TF binding. It is possible that H3.3 loss independently affects chromatin structure and histone modification, with TF binding changes being a consequence rather than a cause. The proposed hierarchy of events is not tested.
- **Why it matters** The proposed model has specific causal ordering. Without experimental manipulation (e.g., tethering p300 to a promoter in H3.3 KO cells, or expressing a TF whose binding is reduced), the model remains speculative.
- **Resolution test** Perform experiments that test the epistatic relationship between H3.3, TF binding, and p300 recruitment. For example, artificially recruit p300 to a promoter in H3.3 KO cells and assess whether H3K27ac and BRD4 recruitment are restored. Alternatively, use a system where TF binding can be induced independently of H3.3.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Differentiation analysis
- **Claim pointer** The authors claim that H3.3 is "required for TF binding at new promoters during differentiation" and that H3.3 KO cells "fail to generate footprints of lineage-specific TF motifs."
- **Evidence pointer** Fig. 5A-B, Table S3
- **Concern** The differentiation experiments are described briefly. It is unclear how many biological replicates were used, how the EB differentiation was validated (e.g., expression of lineage markers), and whether the observed differences in TF footprinting are due to a failure to establish new binding or a delay in differentiation. The analysis is restricted to promoters, but lineage-specific TF binding often occurs at enhancers.
- **Why it matters** The differentiation phenotype is a key part of the paper's conclusion. If the effect is due to a general delay in differentiation rather than a specific failure to establish TF binding, the interpretation would be different.
- **Resolution test** Provide a more detailed characterization of the EB differentiation time course, including validation of differentiation status. Include analysis of enhancer regions. Perform footprinting analysis at multiple time points to distinguish between a delay and a block in establishing new TF binding.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Data availability
- **Claim pointer** The authors state that "Code to generate figures is available" and that datasets are deposited in GEO.
- **Evidence pointer** Data Availability section
- **Concern** The GEO accession numbers are listed as "GSExxx" placeholders. The code repository link points to a repository named "Tafessu-et-al-2021", which may not match the current manuscript. Without accessible data and code, the analyses cannot be independently verified.
- **Why it matters** Reproducibility is a core requirement for genomic studies. The current placeholder information prevents assessment.
- **Resolution test** Provide valid GEO accession numbers and confirm that the code repository is publicly accessible and matches the analyses described in the manuscript.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of definitions
- **Affected element** Definition of "active promoters"
- **Evidence pointer** Results section "H3.3 increases DNA accessibility at promoters"
- **Issue** The definition of "active promoters" (based on >20 baseMean expression) is provided, but it is not clear whether this threshold was applied to both WT and KO samples or only WT. The choice of threshold is not justified.
- **Required correction** Clarify the definition and provide a rationale for the chosen threshold.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Differential accessibility analysis
- **Evidence pointer** Fig. S2A
- **Issue** The text states that 335 regions were differentially accessible, but the statistical threshold and multiple testing correction method are not described.
- **Required correction** Report the statistical criteria used to define differential accessibility (e.g., FDR threshold, fold change cutoff).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of TF footprinting
- **Affected element** TOBIAS analysis
- **Evidence pointer** Fig. 2A-D, Fig. 5A-B
- **Issue** The text states that "nearly all expressed TFs show reduced binding" but does not discuss whether this is a specific effect or a consequence of reduced accessibility. The distinction between reduced accessibility and reduced TF binding is not clearly addressed.
- **Required correction** Discuss the relationship between accessibility changes and TF footprinting changes, and consider whether the TOBIAS analysis accounts for accessibility differences.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Fig. 1D-E
- **Evidence pointer** Fig. 1D-E
- **Issue** The text describes correlations and quartile binning, but the figure panels are not available for review. It is unclear how the correlation was calculated and whether it is statistically significant.
- **Required correction** Provide the figure panels and report correlation coefficients and p-values.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion does not address potential limitations of the study, such as the use of bulk cell populations, potential indirect effects of H3.3 loss, or the possibility that the observed changes are secondary to other cellular defects.
- **Required correction** Add a limitations paragraph to the discussion.

## Risk / unsupported claims
- The claim that H3.3 "is required for TF binding at new promoters during differentiation" is not fully supported by the presented data, as the analysis is limited to promoters and the differentiation time course is not fully characterized.
- The proposed causal pathway (H3.3 → TF binding → p300 → H3K27ac → BRD4) is not tested and should be presented as a model rather than a conclusion.
- The claim that H3.3 "contributes to chromatin accessibility" is supported by the data, but the effect size is described as "subtle" and its biological significance is not established.
- The statement that "H3.3 itself plays a role in regulating histone acetylation" is not directly tested, as the authors do not manipulate H3.3 independently of other factors.
- The claim that "H3.3 KO cells retain footprinting of ESC-specific TFs motifs" during differentiation is based on a single time point and requires validation.