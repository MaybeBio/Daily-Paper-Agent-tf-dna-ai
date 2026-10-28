## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Discussion, Materials and Methods) as provided
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and evolutionary inference as presented in the provided text
- **Shared manuscript claim summary** The authors propose that the N-terminal DNA-binding domain (DBD) of CGGBP1 restricts cytosine methylation at GC-rich transcription factor binding sites (TFBSs) in proximal promoters, thereby protecting these sites from C-to-T transition mutations and regulating gene expression. This function is presented as evolutionarily conserved in amniotes.
- **Visible evidence base** Results sections 1-4, Figures 1-5 (referenced), Supplementary Figures S1-S14 (referenced), Supplementary Tables S1-S9 (referenced), Methods section
- **Missing materials affecting confidence** Raw sequencing data, complete figure panels, statistical details for several analyses, exact numbers for enrichment/depletion calculations, full lists of TFBSs in Table S7, details of the "randomly-derived null set" construction, and complete phylogenetic tree outputs

## Reviewer
- **Overall assessment** This manuscript addresses an interesting and potentially important question about how a DNA-binding protein with a simple domain architecture can integrate multiple functions. The central hypothesis, that CGGBP1 protects TFBSs from methylation-associated mutation, is novel and could have broad implications for understanding gene regulation and genome evolution. However, the evidence presented is largely correlative and indirect. The causal link between CGGBP1 DBD binding, methylation restriction, and gene expression changes is not firmly established. Several key analyses lack sufficient detail or appropriate controls, and the evolutionary inference, while intriguing, is based on a limited set of comparisons. The manuscript would benefit from more direct experimental evidence, such as targeted methylation analysis at specific loci, and a more rigorous statistical framework for the comparative genomics analyses.
- **Who would be interested in the results, and why** Researchers studying DNA-binding proteins, epigenetic regulation, particularly cytosine methylation, and the evolution of gene regulatory elements. The work may also be of interest to those studying the functional consequences of transposable element domestication, given the proposed origin of CGGBP1 from a transposase. The potential link between TFBS protection and evolutionary conservation of regulatory sequences could attract interest from evolutionary biologists.
- **Major strengths** 
  1. The study addresses a significant gap in understanding how CGGBP1's simple structure relates to its diverse functions.
  2. The use of complementary approaches (MeDIP-seq, expression microarrays, ChIP-seq, comparative genomics) is commendable.
  3. The hypothesis linking methylation restriction to TFBS conservation is creative and testable.
  4. The evolutionary analysis, while preliminary, adds a valuable dimension to the study.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Causal inference
  - **Claim pointer** The claim that CGGBP1 DBD binding directly restricts cytosine methylation at TFBSs, thereby regulating gene expression.
  - **Evidence pointer** Results sections 1-4, Figures 1-5
  - **Concern** The manuscript establishes correlations between CGGBP1 DBD presence, methylation levels, and gene expression, but does not provide direct evidence of a causal mechanism. The authors show that loss of the DBD (C-term expression) leads to increased methylation and altered expression, but this could be an indirect effect of disrupted protein function or altered nuclear localization. The claim of "steric protection" is speculative and not directly tested.
  - **Why it matters** The central thesis of the paper rests on this causal link. Without direct evidence that CGGBP1 binding physically prevents methylation at specific sites, the proposed mechanism remains unproven. Alternative explanations, such as indirect effects through other chromatin modifiers, are not ruled out.
  - **Resolution test** Provide direct evidence of CGGBP1 DBD binding at specific TFBSs (e.g., ChIP-qPCR or targeted bisulfite sequencing) and demonstrate that this binding is required for local methylation changes. Alternatively, use a DBD-dead mutant to show that DNA binding is necessary for the observed effects.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical rigor
  - **Claim pointer** The claim that the inverse correlation between TFBS GC-content and cytosine methylation is specific to amniote-conserved TFBSs.
  - **Evidence pointer** Results section 2, Figure 2E-G
  - **Concern** The statistical analysis comparing TFBS categories across evolutionary groups is not described in sufficient detail. The authors report Spearman correlation coefficients but do not provide confidence intervals, effect sizes, or details on how multiple testing was handled. The classification of TFBSs into "euteleostomi, tetrapoda, amniota" etc. is based on TF conservation, but the analysis does not appear to account for the phylogenetic non-independence of the species compared.
  - **Why it matters** The evolutionary conclusion is a key part of the paper's significance. If the statistical framework is flawed, the conclusion that this is an amniote-specific phenomenon is not supported.
  - **Resolution test** Provide a detailed description of the statistical model, including how phylogenetic relationships were accounted for. Include confidence intervals and effect sizes for the reported correlations. Consider using phylogenetic comparative methods.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Data availability and quality
  - **Claim pointer** The claim that CGGBP1 DBD occupies the 45 identified TFBSs.
  - **Evidence pointer** Results section 5, Figure 5A-B
  - **Concern** The ChIP-seq data for N-term and full-length CGGBP1 are presented as evidence of binding at the 45 TFBSs. However, the analysis appears to be based on motif enrichment in ChIP-seq reads rather than peak calling. The authors note that N-term ChIP-seq had "no significantly scoring peaks," which raises questions about the quality and interpretability of this dataset. The enrichment analysis may be confounded by the GC-rich nature of the motifs and the input DNA.
  - **Why it matters** Direct binding evidence is crucial for the proposed mechanism. If the ChIP-seq data are not robust, the claim of occupancy is weakened.
  - **Resolution test** Provide a more detailed analysis of the ChIP-seq data, including peak calling with appropriate controls, and validate binding at a subset of loci by ChIP-qPCR. Address the potential GC-bias in the enrichment analysis.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Evolutionary inference
  - **Claim pointer** The claim that the methylation restriction function was "progressively acquired during vertebrate evolution" and is specific to amniotes.
  - **Evidence pointer** Results section 4, Figure 4
  - **Concern** The evolutionary analysis is based on a comparison of promoter sequences across 36 species, but the authors do not provide a clear phylogenetic framework for interpreting the results. The observation that the signal is strongest in mammals is interesting, but the authors do not adequately address why this might be the case. The analysis of C-to-T transitions is indirect and does not directly measure historical methylation.
  - **Why it matters** The evolutionary narrative is a major part of the paper's broader significance. If the evidence is weak, the claim of an amniote-specific adaptation is not convincing.
  - **Resolution test** Provide a more robust phylogenetic analysis, including ancestral state reconstruction. Directly test for differences in substitution rates at TFBSs versus flanking regions. Consider analyzing methylation data from additional species if available.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 1A
  - **Evidence pointer** Results section 1, Figure 1A
  - **Issue** The schematic of the truncated constructs is not described in the text. It is unclear what the exact boundaries of the N-term and C-term are relative to the DBD and the nuclear localization signal (NLS).
  - **Required correction** Add a clear description of the constructs in the text or figure legend, including the position of the NLS and the DBD.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Methodology
  - **Affected element** MeDIP-seq analysis
  - **Evidence pointer** Results section 1, Methods
  - **Issue** The description of the MeDIP-seq analysis is brief. It is unclear how the "MeDIP signals" were calculated and normalized, and how the "1-100" and "100-1000" signal ranges were defined.
  - **Required correction** Provide a more detailed description of the MeDIP-seq data processing and analysis pipeline, including normalization methods and how signal ranges were determined.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Figure 3C
  - **Evidence pointer** Results section 3, Figure 3C
  - **Issue** The statement that C-repressed gene promoters are "GC-poor" is based on a comparison with a null set, but the details of this comparison are not provided. It is unclear if the null set was matched for other features such as gene expression level or genomic location.
  - **Required correction** Describe the construction of the null set in more detail and discuss potential confounding factors.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Figure 4G
  - **Evidence pointer** Results section 4, Figure 4G
  - **Issue** The figure shows methylation differences at the 45 motifs, but the statistical significance of these differences is not reported in the text.
  - **Required correction** Add statistical details to the figure legend or text, including p-values and effect sizes.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section
  - **Issue** The discussion of the evolutionary implications is somewhat speculative and could be more focused. The link between the proposed mechanism and the domestication of a transposase is interesting but not fully developed.
  - **Required correction** Consider revising the discussion to more clearly separate established findings from speculation.
- **Technical failings that need to be addressed before the case is established** 
  1. Lack of direct causal evidence linking DBD binding to methylation restriction (R1-M1).
  2. Insufficient statistical detail for the comparative genomics analyses (R1-M2).
  3. Potential issues with ChIP-seq data quality and interpretation (R1-M3).
  4. Incomplete description of the evolutionary analysis framework (R1-M4).
- **Assessment against Nature-style criteria** 
  - **Originality** The hypothesis that a DNA-binding protein protects TFBSs from methylation-associated mutation is novel and represents a potentially significant conceptual advance. The idea that a protein can shape the evolution of its own binding sites through methylation protection is creative.
  - **Scientific importance** If the mechanism is confirmed, it would have broad implications for understanding how regulatory elements are maintained and evolve, and how DNA-binding proteins can influence the epigenome. The potential link to transposon domestication adds to its importance.
  - **Interdisciplinary readership** The work bridges epigenetics, gene regulation, and evolutionary biology, which could appeal to a broad audience. However, the current presentation is heavily focused on the specific details of CGGBP1, which may limit its immediate accessibility.
  - **Technical soundness** The experimental approaches are generally appropriate, but the lack of direct causal evidence and the statistical weaknesses in the comparative analyses are significant concerns. The ChIP-seq data quality is questionable.
  - **Readability for nonspecialists** The manuscript is written in a technical style that assumes familiarity with epigenetics and comparative genomics. The main hypothesis is clearly stated, but the supporting evidence is presented in a way that may be difficult for a general reader to follow.
- **Recommendation posture** Currently not established from the provided evidence. The central hypothesis is interesting and potentially important, but the evidence is largely correlative and indirect. The manuscript would require substantial revision, including direct experimental tests of the proposed mechanism and a more rigorous statistical framework for the evolutionary analyses, before it could be considered for publication in a high-impact journal.

## Risk / unsupported claims
- The claim that CGGBP1 DBD binding directly restricts cytosine methylation at TFBSs is not directly supported by the data presented.
- The claim that this function was "progressively acquired during vertebrate evolution" is not fully supported by the limited comparative analysis.
- The claim that the C-terminal part of CGGBP1 is responsible for gene repression is not directly tested.
- The statement that "CGGBP1 binding restricts C-T transitions" is an inference from indirect evidence and is not directly demonstrated.
- The claim that the N-terminal DBD is conserved in amniotes is based on sequence analysis, but the functional significance of this conservation is not directly tested.