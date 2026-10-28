## Review setup
- **Input scope** Full manuscript text, including abstract, results, materials and methods, and supplementary figure/table references
- **Assessment boundary** Structural and functional characterization of meiotic Rec114-Mei4 and Mer2 complexes; evolutionary conservation claims; DNA-binding and condensation properties
- **Shared manuscript claim summary** The authors report that Rec114-Mei4 forms a 2:1 heterotrimeric complex with a conserved architecture, that Mer2 forms parallel homotetrameric coiled coils, and that both complexes bind preferentially to branched DNA structures through multivalent interactions that drive condensation. They further claim these structural and functional properties are evolutionarily conserved across eukaryotes.
- **Visible evidence base** AlphaFold structural predictions; NMR spectroscopy (chemical shift assignments, NOEs); thermal shift assays; SEC-MALS; SEC-SAXS; gel shift assays; filter binding assays; AFM imaging; pull-down assays; yeast genetics (spore viability)
- **Missing materials affecting confidence** Supplementary figures and tables referenced throughout (S1-S18) were not provided; full NMR assignment statistics and validation metrics not shown; AlphaFold confidence metrics (pLDDT, PAE) not shown in main text; raw gel shift and AFM images not shown; SAXS fitting statistics only partially reported

## Reviewer

- **Overall assessment** This manuscript presents a substantial body of work combining computational prediction with multiple biophysical and biochemical approaches to characterize the architecture of meiotic DSB proteins. The combination of AlphaFold with experimental validation via NMR, SAXS, mutagenesis, and functional assays is commendable and generally well executed. The finding that Rec114-Mei4 and Mer2 preferentially bind branched DNA structures is interesting and potentially significant for understanding meiotic DSB formation. However, several concerns temper my enthusiasm: the evolutionary conservation claims rest heavily on AlphaFold predictions with limited experimental validation for non-yeast orthologs; the functional significance of the DNA-binding properties remains correlative; and some conclusions regarding the in vivo relevance of the observed condensation behavior are not directly tested. The manuscript would be strengthened by addressing these gaps.

- **Who would be interested in the results, and why** Researchers studying meiosis, particularly the initiation of meiotic recombination and DSB formation; structural biologists interested in the application of AlphaFold to challenging protein complexes with disordered regions; biochemists studying protein-DNA interactions and phase separation/condensation phenomena. The evolutionary conservation aspect will interest comparative biologists studying meiosis across eukaryotes.

- **Major strengths**
  1. The combination of AlphaFold prediction with multiple orthogonal experimental techniques (NMR, SAXS, SEC-MALS, mutagenesis) provides a robust approach to structural characterization of challenging protein complexes.
  2. The identification of branched DNA preference for both Rec114-Mei4 and Mer2 is a novel finding that may have mechanistic implications.
  3. The use of multiple species orthologs strengthens the evolutionary conservation claims.
  4. The authors honestly address discrepancies with their previous work (e.g., the parallel vs antiparallel Mer4 coiled-coil configuration).
  5. The functional validation through yeast genetics (spore viability) connects biochemical observations to biological relevance.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "The architectures of Rec114-Mei4 and Mer2, and their multivalent binding to branched DNA, are evolutionarily conserved"
- **Evidence pointer** Figures 6-7; Supplemental Figures S8-S18
- **Concern** The evolutionary conservation claim is primarily supported by AlphaFold predictions for non-yeast orthologs, with experimental validation limited to pull-down assays for complex formation and gel shift assays for DNA binding. For M. musculus, A. thaliana, S. pombe, and Z. mays, the authors do not provide structural validation (e.g., SAXS or NMR) of the predicted architectures. The DNA-binding experiments for orthologs appear limited to a subset (IHO1, Rec15, PHS1-PRD2), and the quantitative comparison across species is incomplete. The claim of "conserved" architecture and function requires more direct experimental evidence across species.
- **Why it matters** The evolutionary conservation claim is a central conclusion of the paper and is stated in the title. If the evidence is primarily computational with limited experimental support, the claim is overstated and could mislead the field.
- **Resolution test** Provide experimental validation (e.g., SAXS or cross-linking) for at least one or two non-yeast ortholog complexes to confirm the predicted architectures. Alternatively, temper the conservation claim to reflect the level of evidence actually provided.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional significance
- **Claim pointer** "The two DNA-binding surfaces of Rec114-Mei4 drive condensation" and "condensation activity that drives the assembly of the DSB machinery"
- **Evidence pointer** Figures 3I-K; Discussion section
- **Concern** The condensation experiments use a fusion construct with two Rec114 subunits linked by a flexible linker, which is an artificial system. The authors show that mutating one DNA-binding surface abolishes condensation in this fusion context, but the relevance to the native complex is unclear. Furthermore, the claim that condensation "drives the assembly of the DSB machinery" is not directly tested; no experiments link condensation to DSB formation or recruitment of other DSB proteins. The in vivo data (spore viability) show that DNA-binding mutations affect viability, but the connection to condensation specifically is not established.
- **Why it matters** The functional model proposed (condensation as a driver of DSB machinery assembly) is a key conceptual advance claimed by the paper. Without direct evidence linking condensation to DSB formation, this remains speculative.
- **Resolution test** Provide experiments that directly test whether condensation is required for DSB formation, e.g., using mutants that separate DNA-binding from condensation, or imaging DSB protein foci in cells expressing condensation-defective mutants.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical rigor
- **Claim pointer** "NMR data strongly support the AlphaFold models"
- **Evidence pointer** Figure 1D-E; Supplemental Figures S1-S2; Supplemental Table S1
- **Concern** The NMR validation is described as supporting the AlphaFold model, but the extent of assignment completeness is not reported. Only 13 unambiguous NOEs were detected, which is a relatively small number for validating a protein-protein interface. The chemical shift perturbations upon complex formation are mentioned but not quantified. The authors state that NMR "did not allow us to determine the structure de novo," which raises questions about the quality of the NMR data and the strength of the validation claim.
- **Why it matters** The NMR data are presented as key experimental validation of the AlphaFold model. If the NMR data are limited in scope, the strength of the validation is correspondingly limited.
- **Resolution test** Report assignment completeness statistics, provide a quantitative comparison between predicted and observed chemical shifts, and clearly state the limitations of the NMR validation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of results
- **Claim pointer** "Mutations of the KKTK motif did not affect DNA binding" (contradicting previous work)
- **Evidence pointer** Supplemental Figure S7A; Discussion section
- **Concern** The authors report that mutating the KKTK motif in Mer2 did not affect DNA binding, contradicting a previous study (Tsai et al. 2020). The authors attribute this discrepancy to differences in experimental conditions or protein constructs, but do not provide a rigorous explanation. This is an important discrepancy that could affect the interpretation of the functional role of this motif.
- **Why it matters** The KKTK motif was previously implicated in DNA binding, and the current study challenges this. If the discrepancy is not resolved, it creates uncertainty about the functional relevance of this motif and the reliability of the DNA-binding assays.
- **Resolution test** Provide a more detailed comparison of experimental conditions between the two studies, or perform additional experiments (e.g., different salt conditions, longer DNA substrates) to determine whether the KKTK motif contributes to DNA binding under specific conditions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative analysis
- **Claim pointer** "Rec114-Mei4 binds to an HJ substrate with >20-fold higher affinity than to duplex DNA"
- **Evidence pointer** Figure 3A-E; Figure 6C; Supplemental Figure S12
- **Concern** The quantitative comparison of DNA-binding affinities across different substrates and species is based on gel shift assays, which are semi-quantitative at best. The authors report fold-differences in affinity but do not provide binding constants (Kd values) or statistical analysis. The comparison between yeast and mouse complexes is particularly limited, as only one concentration point is shown for some experiments.
- **Why it matters** The claim of preferential binding to branched DNA is a key finding, and the quantitative aspect (10-20 fold) is used to support the model. Without rigorous quantitative analysis, the strength of this claim is uncertain.
- **Resolution test** Provide binding constants from quantitative assays (e.g., fluorescence anisotropy, ITC) for at least the yeast complex with different DNA substrates, and include statistical analysis of replicate experiments.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1B
- **Evidence pointer** Figure 1B
- **Issue** The thermal shift assay data show melting temperatures of 74.5°C and 81.5°C for Rec114 and Rec114-Mei4, respectively, but the units and error bars are not clearly described in the figure legend.
- **Required correction** Clarify the units and provide error bars and number of replicates in the figure legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section
- **Evidence pointer** Materials and Methods
- **Issue** The NMR assignment procedure is described briefly, but the completeness of backbone and side chain assignments is not reported. The authors should state what fraction of residues were assigned.
- **Required correction** Add a paragraph in the NMR methods section reporting assignment statistics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The discussion of the KKTK motif discrepancy with Tsai et al. (2020) is brief and does not fully explore possible explanations.
- **Required correction** Expand the discussion of this discrepancy, including potential differences in protein constructs, buffer conditions, or DNA substrate design.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 6A
- **Evidence pointer** Figure 6A
- **Issue** The AlphaFold models for different species are shown as cartoons, but the confidence levels (pLDDT) are not color-coded or indicated, making it difficult to assess which regions are predicted with high confidence.
- **Required correction** Color-code the models by pLDDT score or provide a separate panel showing confidence metrics.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Spore viability assays
- **Evidence pointer** Supplemental Figure S4E, S7B
- **Issue** The spore viability data are presented as percentages, but the number of tetrads dissected and the statistical significance of differences between strains are not reported.
- **Required correction** Report the number of tetrads analyzed and perform statistical tests to support claims of differences between strains.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the architectures are "evolutionarily conserved" but does not specify the species range examined or the level of evidence.
- **Required correction** Qualify the conservation claim in the abstract to reflect the evidence level (e.g., "predicted to be conserved based on AlphaFold modeling and supported by biochemical experiments for select orthologs").

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** SAXS analysis
- **Evidence pointer** Figure 4D-E; Supplemental Figure S17
- **Issue** The SAXS data are described as being in "excellent agreement" with models, but the specific goodness-of-fit parameters (e.g., chi-squared values) are not reported in the main text.
- **Required correction** Report the chi-squared values or other fit statistics for the SAXS model comparisons.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Completeness
- **Affected element** AFM analysis
- **Evidence pointer** Figure 5F; Figure 7D-E
- **Issue** The AFM images are qualitative; no quantitative analysis of particle sizes or DNA-bridging frequencies is provided.
- **Required correction** Provide quantitative analysis of AFM data (e.g., particle height distributions, bridging frequency) to support the conclusions.

- **Technical failings that need to be addressed before the case is established**
  1. R1-M1: Insufficient experimental validation of evolutionary conservation claims for non-yeast orthologs
  2. R1-M2: Lack of direct evidence linking condensation to DSB formation in vivo
  3. R1-M3: Limited NMR data quality metrics; small number of NOEs used for validation
  4. R1-M5: Semi-quantitative DNA-binding analysis without binding constants or statistics

- **Assessment against Nature-style criteria**
  - **Originality**: The work is original in its application of AlphaFold to these specific meiotic proteins and in the identification of branched DNA preference. However, the general concept of using AlphaFold for structural prediction of protein complexes is not novel, and the finding of DNA-binding activity for these proteins was previously reported.
  - **Scientific importance**: The meiotic DSB machinery is of fundamental importance for understanding reproduction and genome stability. Structural information on Rec114-Mei4 and Mer2 complexes is valuable. However, the functional significance of the specific DNA-binding properties remains incompletely defined, limiting the immediate impact.
  - **Interdisciplinary readership**: The work will primarily interest meiosis researchers and structural biologists. The evolutionary conservation aspect may attract broader interest, but the specialized nature of the system limits cross-disciplinary appeal.
  - **Technical soundness**: The combination of techniques is generally sound, but several technical concerns (limited NMR validation, semi-quantitative binding assays, lack of statistical analysis) reduce confidence in some conclusions.
  - **Readability for nonspecialists**: The manuscript is clearly written and the logic is generally easy to follow. However, some sections assume familiarity with meiosis-specific terminology and techniques. The abstract is accessible, but the results section may be challenging for nonspecialists.

- **Recommendation posture** Supportive if technical concerns are resolved. The core findings regarding the structure of Rec114-Mei4 and Mer2 complexes and their preference for branched DNA are interesting and potentially significant. However, the evolutionary conservation claim needs to be tempered or better supported experimentally, and the functional link between condensation and DSB formation needs to be strengthened. The manuscript would be suitable for publication after addressing the major concerns, particularly R1-M1 and R1-M2.

## Risk / unsupported claims
- The claim that the architectures of Rec114-Mei4 and Mer2 are "evolutionarily conserved" across eukaryotes is not fully supported by the experimental evidence, which is limited to pull-down assays and DNA-binding experiments for a subset of orthologs.
- The claim that "condensation activity drives the assembly of the DSB machinery" is not directly tested and remains speculative.
- The statement that the KKTK motif is not involved in DNA binding contradicts previous work, and the discrepancy is not fully resolved.
- The claim of ">20-fold higher affinity" for HJ substrates over duplex DNA is based on semi-quantitative gel shift assays without statistical analysis.
- The assertion that the NMR data "strongly support" the AlphaFold models is not fully quantified; the number of NOEs (13) is limited, and assignment completeness is not reported.