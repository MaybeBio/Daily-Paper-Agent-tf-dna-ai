## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends referenced but not provided in full)
- **Assessment boundary** Scientific content, experimental logic, data interpretation, and claims as presented in the provided text; no assessment of figures or supplementary data that were not included
- **Shared manuscript claim summary** The authors propose that TET2, induced in differentiating B cells, recruits OGT through its C-terminal end to mediate both TET2 O-GlcNAcylation and H2B-S112 O-GlcNAcylation at Aicda and Prdm1 loci, thereby driving AID and BLIMP-1 expression, CSR, SHM, plasma cell differentiation, and maturation of T-dependent and T-independent antibody responses. They further propose that TET2 transduces metabolic cues, with fumarate inhibiting and vitamin C enhancing these processes.
- **Visible evidence base** Text descriptions of experiments including mouse genetics (AicdaCre-driven conditional deletion), in vitro B cell stimulation, ChIP-qPCR, MeDIP/hMeDIP-seq, flow cytometry, AlphaFold 3.0 modeling, inhibitor studies, and humanized mouse experiments
- **Missing materials affecting confidence** All figures, figure legends, supplementary figures, tables, and raw sequencing data; exact statistical values beyond p-value thresholds; details of antibody validation; gating strategies for flow cytometry; complete AlphaFold confidence metrics

## Reviewer
- **Overall assessment** This manuscript addresses a significant question in B cell immunology: how TET2 coordinates epigenetic remodeling and metabolic sensing to drive antibody diversification and plasma cell differentiation. The central claim that TET2 recruits OGT for both its own O-GlcNAcylation and H2B-S112 O-GlcNAcylation at Aicda and Prdm1 loci is conceptually interesting and potentially important. However, the evidence as presented has several gaps that prevent full confidence in the conclusions. The genetic approach using AicdaCre-driven deletion is appropriate for studying activated B cells, but the manuscript does not clearly establish whether the effects on antibody responses are due to TET2 catalytic activity, OGT recruitment, or both. The distinction between TET2 catalytic and non-catalytic functions is a key strength of the conceptual framework, but the experimental separation of these functions is incomplete. The AlphaFold 3.0 modeling is used to support the interaction, but this is predictive rather than experimental evidence. The metabolic regulation experiments are intriguing but the in vivo relevance requires stronger validation. Overall, the manuscript has potential but needs additional experiments and clearer data presentation to fully support its claims.

- **Who would be interested in the results, and why** Immunologists studying B cell differentiation, antibody responses, and germinal center biology would be the primary audience. Researchers interested in epigenetic regulation of immune responses, particularly TET proteins and DNA demethylation, would also find this relevant. The connection between metabolism and epigenetic regulation in B cells could interest researchers studying immunometabolism. The potential therapeutic implications for vitamin C and fumarate in modulating antibody responses might attract translational researchers.

- **Major strengths** The manuscript addresses a novel and important question about how TET2 coordinates epigenetic and metabolic programs in B cell differentiation. The use of B cell-specific conditional knockout mice (AicdaCre) is appropriate for studying activated B cells. The conceptual framework distinguishing TET2 catalytic function from its non-catalytic OGT recruitment adaptor function is innovative. The combination of genetic, biochemical, and computational approaches is comprehensive. The inclusion of both mouse and human B cell experiments strengthens the translational relevance. The metabolic regulation experiments with fumarate and vitamin C provide a physiologically relevant dimension.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal mechanism
- **Claim pointer** The manuscript claims that TET2 recruits OGT for TET2 O-GlcNAcylation, which supports TET2 catalytic activity, and that this is required for AID and BLIMP-1 expression.
- **Evidence pointer** Results section "B cell TET2 recruits OGT for its O-GlcNAcylation and catalytic DNA 5mC to 5hmC oxidation"; Figures 4B-4F (described in text)
- **Concern** The manuscript does not clearly demonstrate that TET2 O-GlcNAcylation is required for TET2 catalytic activity. The experiments show that OGT deletion reduces TET2 O-GlcNAcylation and reduces 5mC to 5hmC oxidation, but this correlation does not establish causation. The authors do not show that a TET2 mutant lacking O-GlcNAcylation sites has reduced catalytic activity. Additionally, the Tet2OGT-Δmut experiment shows reduced CSR and plasma cell differentiation, but this mutant also lacks the C-terminal domain which may have other functions beyond OGT recruitment. The manuscript does not provide direct evidence that O-GlcNAcylation of TET2 specifically enhances its catalytic activity rather than affecting TET2 stability, localization, or other functions.
- **Why it matters** The central mechanistic claim of the manuscript is that TET2 O-GlcNAcylation supports TET2 catalytic activity. Without direct evidence for this, the causal chain from TET2-OGT interaction to DNA demethylation to gene expression is not fully established. This is critical for the overall conclusion that TET2 recruits OGT for its catalytic function.
- **Resolution test** The authors should perform experiments with TET2 mutants lacking identified O-GlcNAcylation sites to show that these mutants have reduced catalytic activity. Alternatively, they could use in vitro demethylation assays with O-GlcNAcylated versus non-O-GlcNAcylated TET2 to directly demonstrate enhanced activity. They should also test whether the Tet2OGT-Δmut phenotype is specifically due to loss of OGT recruitment by showing that a TET2 mutant that cannot bind OGT but retains other C-terminal functions has the same phenotype.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental evidence
- **Claim pointer** The manuscript claims that TET2 recruits OGT to Aicda and Prdm1 loci for H2B-S112 O-GlcNAcylation, and that this is required for gene expression.
- **Evidence pointer** Results section "B cell TET2 recruits OGT for O-GlcNAcylation of Aicda and Prdm1 loci chromatin H2B-S112"; Figures 4G and 6D (described in text)
- **Concern** The ChIP experiments described show TET2 and OGT occupancy at Aicda and Prdm1 regulatory regions, and H2B-S112 O-GlcNAcylation at these loci. However, the manuscript does not provide evidence that H2B-S112 O-GlcNAcylation directly promotes transcription of these genes. The claim that H2B-S112 O-GlcNAcylation "promotes chromatin accessibility and transcription" is stated but not directly tested. The manuscript does not show whether H2B-S112 O-GlcNAcylation affects RNA polymerase II recruitment, chromatin accessibility (e.g., ATAC-seq), or histone modifications associated with active transcription. Additionally, the manuscript does not demonstrate that the H2B-S112 O-GlcNAcylation at these loci is specifically dependent on TET2-recruited OGT, as opposed to OGT recruited by other factors.
- **Why it matters** The claim that TET2 recruits OGT for H2B-S112 O-GlcNAcylation at specific loci is a key part of the proposed mechanism. Without direct evidence that this histone modification affects gene expression, the functional significance of this finding is unclear. This is important for understanding how TET2 coordinates DNA demethylation and histone modification to regulate gene expression.
- **Resolution test** The authors should perform experiments to directly test the role of H2B-S112 O-GlcNAcylation in Aicda and Prdm1 expression. This could include ATAC-seq to assess chromatin accessibility, ChIP for RNA polymerase II or active histone marks, or experiments with H2B mutants that cannot be O-GlcNAcylated. They should also show that H2B-S112 O-GlcNAcylation at these loci is specifically lost when TET2 is deleted or when the TET2-OGT interaction is disrupted.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation
- **Claim pointer** The manuscript claims that fumarate inhibits and vitamin C activates TET2 to modulate antibody responses, and that this reflects metabolic regulation of B cell differentiation.
- **Evidence pointer** Results sections "Fumarate inhibits B cell TET2 to impair AID and BLIMP-1 expression..." and "Vitamin C boosts B cell TET2 catalytic activity..."; Figures 6 and 7 (described in text)
- **Concern** The experiments with fumarate and vitamin C show effects on antibody responses, but the manuscript does not clearly establish that these effects are specifically mediated through TET2. Fumarate is known to have multiple cellular targets beyond TET enzymes, including succinate dehydrogenase and other 2-oxoglutarate-dependent dioxygenases. Similarly, vitamin C has antioxidant properties and can affect many cellular processes. The manuscript does not show that the effects of fumarate or vitamin C on antibody responses are absent or reduced in TET2-deficient B cells. Without this specificity control, the conclusion that these metabolic regulators act through TET2 is not fully supported.
- **Why it matters** The claim that TET2 transduces metabolic cues is a significant and interesting aspect of the manuscript. However, if the effects of fumarate and vitamin C are not specifically mediated through TET2, this conclusion is not valid. This is important for understanding the specificity of metabolic regulation of B cell differentiation and for potential therapeutic applications.
- **Resolution test** The authors should perform experiments with TET2-deficient B cells treated with fumarate or vitamin C to show that the effects of these compounds are TET2-dependent. They could also use more specific TET2 activators or inhibitors, or genetic approaches to modulate TET2 activity, to confirm the specificity of the effects.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical rigor
- **Claim pointer** The manuscript claims that AlphaFold 3.0 modeling provides evidence for the TET2-OGT-DNA interaction and the C-terminal-mediated OGT recruitment.
- **Evidence pointer** Results section "3D modeling of TET2-OGT-DNA complex at Aicda Area IV or Prdm1 Area II"; Figure 5A (described in text)
- **Concern** The AlphaFold 3.0 modeling is presented as supporting evidence for the TET2-OGT interaction, but the manuscript acknowledges that no crystallographic structure is available for validation. The ipTM scores are stated to be greater than 0.6, which is a relatively modest threshold for confidence. The manuscript does not provide details on how the DNA sequence was selected, how the complex was assembled, or whether alternative conformations were explored. The modeling is used to support the biological claims, but predictive modeling without experimental validation should be treated with caution.
- **Why it matters** The AlphaFold 3.0 modeling is used to support the claim that TET2 recruits OGT through its C-terminal end. While this is a reasonable hypothesis, the modeling alone is not sufficient to establish the interaction. Experimental validation through co-immunoprecipitation with specific mutants or cross-linking studies would strengthen this claim.
- **Resolution test** The authors should provide more details on the AlphaFold 3.0 modeling parameters and confidence metrics. They should also validate the predicted interaction experimentally, for example by testing whether the C-terminal deletion mutant fails to co-immunoprecipitate with OGT in B cells, or by using proximity ligation assays to demonstrate the interaction in situ.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Data interpretation
- **Claim pointer** The manuscript claims that TET2 expression is induced in differentiating B cells and is required for AID and BLIMP-1 expression, CSR, SHM, and plasma cell differentiation.
- **Evidence pointer** Results sections "TET1, TET2, and TET3 in mouse and human B cells" and "B cell TET2 deletion impairs maturation of the antibody response"; Figures 1 and 2 (described in text)
- **Concern** The manuscript shows that TET2 is induced upon B cell activation and that TET2 deletion impairs antibody responses. However, the rescue experiments with enforced Aicda or Prdm1 expression in TET2-deficient B cells are described but the extent of rescue is not quantified in the text. The manuscript also does not clearly show whether TET2 deletion affects the initial activation and proliferation of B cells, which could indirectly affect AID and BLIMP-1 expression. The statement that TET2 deletion does not impact GC formation or B cell proliferation is important, but the data supporting this are not shown in the text.
- **Why it matters** Understanding whether TET2 acts directly on Aicda and Prdm1 loci or indirectly through effects on B cell activation is important for the mechanistic model. The manuscript claims a direct effect, but the evidence for this is not fully presented in the text.
- **Resolution test** The authors should provide more detailed data on B cell activation and proliferation in TET2-deficient B cells, including cell division tracking and activation marker expression. They should also show the extent of rescue by enforced Aicda and Prdm1 expression more clearly, and ideally show that TET2 directly binds to Aicda and Prdm1 regulatory regions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Summary section
- **Issue** The abstract is dense and uses specialized terminology without sufficient context for a general reader. The phrase "nuclear TET2" in the title is somewhat ambiguous, as TET2 is generally considered a nuclear protein.
- **Required correction** Consider clarifying what is meant by "nuclear TET2" in the title and abstract. The abstract could benefit from a brief explanation of why TET2 O-GlcNAcylation is important for its nuclear function.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Statistical analysis
- **Evidence pointer** Quantification and statistical analysis section
- **Issue** The statistical methods are described briefly. The text states that two-tailed, unpaired Student's t-tests were used, but does not specify whether multiple testing corrections were applied when multiple comparisons were made.
- **Required correction** Specify whether multiple testing corrections were applied and, if so, which method was used. If not, justify why this was not necessary.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Inhibitor concentrations
- **Evidence pointer** Methods section "TET2 and OGT small molecule inhibitors and activator (vitamin C)"
- **Issue** The concentrations of TET-IN-C35 (4 mM) and ST 045849 (55 mM) appear very high for cell culture experiments. The text mentions that a titration was performed for ST 045849, but the final concentration used seems unusually high.
- **Required correction** Clarify whether these are stock concentrations or final working concentrations. If they are final concentrations, provide justification for why such high concentrations were needed and confirm that cell viability was maintained.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Limitations section
- **Evidence pointer** Discussion section "Limitations of the study"
- **Issue** The limitations section is brief and focuses only on the lack of quantification of H2B-S112 O-GlcNAcylation contribution. Other potential limitations, such as the specificity of the inhibitors used, the reliance on AlphaFold modeling, and the potential for compensatory mechanisms in the knockout mice, are not discussed.
- **Required correction** Expand the limitations section to address these additional potential limitations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and code availability
- **Evidence pointer** Data and code availability section
- **Issue** The data availability statement mentions that sequencing data have been deposited in NCBI SRA, but does not mention whether the AlphaFold 3.0 modeling data or scripts are available.
- **Required correction** Consider making the AlphaFold 3.0 modeling parameters and scripts available, or at least state that they are available upon request.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Multiple sections
- **Issue** The manuscript uses the term "naïve" with a diaeresis (naïve) in some places and without in others. This is inconsistent.
- **Required correction** Use a consistent spelling throughout the manuscript.

## Risk / unsupported claims
- The claim that TET2 O-GlcNAcylation specifically supports TET2 catalytic activity is not directly demonstrated; the evidence is correlative.
- The claim that H2B-S112 O-GlcNAcylation at Aicda and Prdm1 loci promotes transcription is stated but not directly tested.
- The claim that fumarate and vitamin C act specifically through TET2 to modulate antibody responses is not supported by experiments with TET2-deficient B cells treated with these compounds.
- The AlphaFold 3.0 modeling of the TET2-OGT-DNA complex is predictive and not experimentally validated; the modest ipTM threshold of 0.6 limits confidence.
- The claim that TET2 deletion does not impact GC formation or B cell proliferation is stated but the supporting data are not shown in the text.
- The extent of rescue of CSR and plasma cell differentiation by enforced Aicda or Prdm1 expression in TET2-deficient B cells is not quantified in the text.
- The manuscript states that TET2 is phosphorylated and acetylated, but the functional significance of these modifications is not explored.
- The claim that TET2 recruits OGT through its C-terminal end is supported by AlphaFold modeling and a deletion mutant, but direct biochemical evidence for the interaction is not provided.