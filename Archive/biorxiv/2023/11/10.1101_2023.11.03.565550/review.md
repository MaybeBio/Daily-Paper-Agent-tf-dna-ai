## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, supplemental figure/table legends)
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness as presented in the provided text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors propose that GLABRA2 (GL2), a class IV HD-Zip transcription factor, contains a conserved monopartite NLS overlapping its homeodomain, which is necessary and sufficient for nuclear localization, and that Importin α isoforms mediate this process in an IMPα-dependent manner, with tissue-specific redundancy.
- **Visible evidence base** Results sections describing bioinformatic predictions, fluorescent reporter localization, alanine mutagenesis, yeast two-hybrid assays, co-immunoprecipitation, molecular docking, and phenotypic analyses in Arabidopsis. Supplemental figure/table legends referenced but not fully provided.
- **Missing materials affecting confidence** Full supplemental figures and tables (S1–S8, T1–T3), raw proteomics data, detailed statistical analyses, representative microscopy images with quantification methods, and complete experimental replicates are not available in the provided text. This limits independent verification of several key claims.

## Reviewer
- **Overall assessment** This manuscript addresses a relevant and understudied question in plant developmental biology: the nuclear import mechanism of HD-Zip IV transcription factors. The authors provide a multi-pronged approach combining bioinformatics, cell biology, biochemistry, and genetics. The identification of a functional monopartite NLS in GL2 and its interaction with IMPα isoforms is a valuable contribution. However, several claims, particularly regarding tissue-specific redundancy and the sufficiency of the NLS, require stronger experimental support and clearer data presentation. The manuscript is technically sound in many aspects but would benefit from additional controls and quantitative rigor.
- **Who would be interested in the results, and why** Plant developmental biologists studying epidermal cell differentiation, transcription factor regulation, and nuclear transport. Researchers interested in the evolution of HD-Zip transcription factors and their nuclear localization signals. The work may also appeal to those studying Importin α function in plants and its role in tissue-specific protein trafficking.
- **Major strengths** 1) The study addresses a clear gap in knowledge regarding HD-Zip IV nuclear localization. 2) The combination of in silico, in vitro, and in vivo approaches is comprehensive. 3) The use of native promoters and stable transgenic lines strengthens the physiological relevance. 4) The demonstration that NLS function is separable from DNA binding is conceptually important. 5) The evolutionary analysis across plant species adds a useful dimension.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The claim that "IMPα triple mutants (impα-1,2,3) exhibit defects in EYFP:GL2 nuclear localization in trichomes but not in roots, consistent with tissue-specific and redundant functions of IMPα isoforms."
  - **Evidence pointer** Results section "The impα-1,2,3 mutant exhibits impaired GL2 nuclear localization in trichomes"; Figure 6
  - **Concern** The data presented for the impα-1,2,3 mutant phenotype are descriptive and lack quantitative rigor. The text states that approximately 16% of trichomes displayed non-nuclear localization and 18% exhibited both nuclear and cytoplasmic localization, but no statistical analysis, sample sizes, or comparison to control lines are provided. Furthermore, the claim of tissue-specific redundancy is inferred from the absence of a root phenotype, but the expression and functional redundancy of other IMPα isoforms in roots is not experimentally addressed.
  - **Why it matters** The tissue-specific phenotype is a central piece of evidence supporting the model of IMPα-dependent nuclear import. Without robust quantification and statistical support, the conclusion that IMPα isoforms function redundantly in a tissue-specific manner is not firmly established.
  - **Resolution test** Provide quantitative data with statistical analysis (e.g., percentage of cells with nuclear vs. cytoplasmic localization across multiple biological replicates) for both trichomes and roots in wild-type and mutant backgrounds. Include appropriate controls and demonstrate that the observed defects are not due to developmental or pleiotropic effects.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that "Fusing the predicted NLS (GTNKRKRKKYHRH) to EYFP is sufficient for its nuclear localization in roots and trichomes."
  - **Evidence pointer** Results section "Conserved monopartite NLS from HD-Zip IV TFs is sufficient for nuclear localization of EYFP"; Figure 1E-F
  - **Concern** The sufficiency experiments rely on qualitative visual inspection of fluorescence distribution. While the authors mention quantitative analysis of nuclear-to-cytoplasmic ratios, the methodology for this quantification is not described in the provided text. It is unclear how many independent transgenic lines were examined, how many cells were quantified per line, and whether the analysis was blinded. Additionally, the negative control (proGL2:EYFP) is mentioned, but the data are not shown or described in sufficient detail.
  - **Why it matters** Sufficiency is a key criterion for defining a functional NLS. Without rigorous quantitative evidence, the conclusion that the 13-residue motif alone drives nuclear import is not fully supported.
  - **Resolution test** Provide a detailed description of the quantification method, including sample sizes, statistical tests, and representative images. Show data for all constructs tested, including the negative control, and demonstrate that the observed nuclear localization is statistically significant and specific to the NLS-containing constructs.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation
  - **Claim pointer** The claim that "The functional NLS is evolutionarily conserved in a distinct subset of HD-Zip IV members including PROTODERMAL FACTOR2 (PDF2)."
  - **Evidence pointer** Results section "Monopartite NLS is conserved in a subset of HD-Zip IV TFs in Arabidopsis and across the plants"; Figure 1B-C; Supplemental Figure S2
  - **Concern** The evolutionary analysis is based on sequence conservation and prediction algorithms, but the functional significance of the NLS in other family members (e.g., PDF2) is only tested for PDF2. The claim of conservation implies functional relevance across the subset, but this is not experimentally demonstrated for all members. Additionally, the distinction between the "conserved" NLS in the subset and the "non-functional" NLS in FWA, HDG8, HDG9, and HDG10 is based on the reporter assay, but the physiological relevance of these differences is not discussed.
  - **Why it matters** Overstating the functional conservation based on sequence alone could mislead readers about the regulatory mechanisms of other HD-Zip IV members.
  - **Resolution test** Clarify that the functional testing was performed only for GL2 and PDF2, and temper the claim of conservation to reflect sequence-level conservation with functional validation in select members. Alternatively, provide additional functional data for other family members.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract and Introduction
  - **Evidence pointer** Abstract; Introduction
  - **Issue** The abstract states that "IMPα triple mutants (impα-1,2,3) exhibit defects in EYFP:GL2 nuclear localization in trichomes but not in roots," but the introduction does not provide sufficient background on the IMPα gene family in Arabidopsis and the specific functions of the isoforms tested. This makes it difficult for non-specialist readers to understand the significance of the triple mutant.
  - **Required correction** Add a brief description of the Arabidopsis IMPα family, the isoforms included in the triple mutant, and their known or predicted functions in the Introduction.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Results section "GL2 pull-down uncovers IMPα-1, IMPα-2 and IMPα-6 as candidate interactors in Arabidopsis plants"
  - **Evidence pointer** Results; Supplemental Figure S7; Supplemental Data Set 1
  - **Issue** The pull-down experiment identifies IMPα-1, IMPα-2, and IMPα-6 as interactors, but the text states that "Details about the GL2 interactome will be provided in a separate publication." This leaves the reader without sufficient context to evaluate the specificity or significance of these interactions.
  - **Required correction** Provide at least a summary of the pull-down results, including the number of replicates, the criteria for identifying interactors, and a comparison to controls. If the full dataset is to be published elsewhere, include key validation data here.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Methodology
  - **Affected element** Materials and Methods "Co-IP of recombinant proteins"
  - **Evidence pointer** Materials and Methods
  - **Issue** The Co-IP method description is brief and lacks details on the concentrations of proteins used, the washing conditions, and the detection method. This limits reproducibility.
  - **Required correction** Expand the Co-IP protocol to include specific buffer compositions, incubation times, washing steps, and antibody dilutions.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results section "GL2 NLS mutations display epidermal defects in leaves, roots and seeds"
  - **Evidence pointer** Figure 3; Supplemental Figure S3
  - **Issue** Phenotypic quantifications (trichome branching, root hair density, mucilage production) are described but no statistical methods or error bars are mentioned in the text.
  - **Required correction** Include statistical analysis details (e.g., number of samples, tests used, significance thresholds) in the figure legends or methods.
- **Technical failings that need to be addressed before the case is established** 1) Lack of quantitative data and statistical analysis for the impα-1,2,3 mutant phenotype (R1-M1). 2) Insufficient description of the fluorescence quantification methodology for sufficiency experiments (R1-M2). 3) Incomplete presentation of pull-down data and criteria for interactor identification (R1-m2). 4) Missing details in the Co-IP protocol (R1-m3).
- **Assessment against Nature-style criteria**  
  *Originality*: The study addresses a novel question regarding the nuclear import of HD-Zip IV transcription factors, which has not been previously characterized. The identification of a specific NLS and its interaction with IMPα isoforms is original.  
  *Scientific importance*: The findings have implications for understanding post-translational regulation of plant transcription factors and tissue-specific developmental control. The work is relevant to the broader field of nuclear transport.  
  *Interdisciplinary readership*: The topic is primarily of interest to plant biologists and cell biologists. The methods and concepts may not appeal to a broad interdisciplinary audience.  
  *Technical soundness*: The experimental design is generally sound, but the lack of quantitative rigor in key experiments (e.g., impα mutant phenotype, sufficiency assays) weakens the overall technical quality.  
  *Readability for nonspecialists*: The manuscript is clearly written but assumes familiarity with plant development and nuclear transport. The abstract is accessible, but the introduction could better contextualize the IMPα family for non-experts.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially significant, but the current evidence does not fully support all claims, particularly regarding tissue-specific redundancy and the quantitative sufficiency of the NLS. Addressing the major concerns with additional data and clearer methodology would strengthen the manuscript.

## Risk / unsupported claims
- The claim of tissue-specific redundancy of IMPα isoforms is not fully supported by the data presented, as the root phenotype is only described qualitatively and the expression of other isoforms is not assessed.
- The claim that the NLS is "evolutionarily conserved" in a subset of HD-Zip IV members is based on sequence analysis and functional testing in only two members (GL2 and PDF2); the functional conservation in other members is not demonstrated.
- The pull-down experiment identifies IMPα-1, IMPα-2, and IMPα-6 as interactors, but the data are not fully presented, and the specificity of these interactions is not established.
- The statement that "the NLS is required for GL2 function in epidermal development" is supported by phenotypic data, but the quantitative details and statistical analyses are not provided in the text.