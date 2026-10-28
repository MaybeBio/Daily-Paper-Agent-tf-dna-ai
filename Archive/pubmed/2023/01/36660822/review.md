## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and data availability statements
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency of the presented evidence
- **Shared manuscript claim summary** The authors propose that the N-terminal region of ZNF410, specifically a hairpin loop rich in acidic residues, acts as a DNA-mimicking domain that auto-inhibits DNA binding by the ZF array via a cis-acting allosteric mechanism, as supported by SAXS, mutagenesis, and binding assays
- **Visible evidence base** SAXS data (deposited in SASBDB), fluorescence polarization binding assays, EMSA, mutagenesis experiments, AlphaFold predictions, ChIP-seq reanalysis, SEC-MALS
- **Missing materials affecting confidence** Raw SAXS curves and fit residuals are not shown in the manuscript; no crystallographic or NMR structure of the full-length protein; no direct binding data between the isolated NT domain and the ZF domain; no phosphorylation data; no quantitative error analysis for KD values beyond two replicates

## Reviewer

- **Overall assessment** This manuscript presents an interesting and potentially significant hypothesis regarding auto-regulation of a transcription factor by an intramolecular DNA-mimicking domain. The combination of AlphaFold predictions with SAXS and mutagenesis is a modern and appropriate approach. However, the central claim of DNA mimicry by the hairpin loop rests on indirect evidence, and several key controls and quantitative analyses are missing. The manuscript would be strengthened by direct demonstration of the proposed intramolecular interaction, more rigorous SAXS model validation, and additional biophysical characterization of the loop-ZF interaction.

- **Who would be interested in the results, and why** Researchers studying transcription factor regulation, zinc finger proteins, DNA mimicry mechanisms, and the application of AlphaFold in structural biology. The work also has relevance to those interested in erythroid development and hemoglobin switching, given the role of ZNF410 in CHD4 regulation.

- **Major strengths** The study addresses a novel and biologically important question regarding how a transcription factor with a single target gene achieves specificity. The use of multiple complementary techniques (SAXS, FP, EMSA, mutagenesis, AlphaFold) is commendable. The observation that full-length ZNF410 binds DNA more weakly than the isolated ZF domain is clear and well-supported. The evolutionary conservation analysis adds weight to the proposed mechanism.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for central claim
- **Claim pointer** The authors claim that the hairpin loop "mimics the structure and electrostatics of DNA" and provides an allosteric regulatory mechanism by occupying the ZF DNA binding surface
- **Evidence pointer** Figures 1F, 6B-E; Results section "An auto-inhibitory model of the N-terminal helix of ZNF410 in the absence of DNA"
- **Concern** The central claim of DNA mimicry by the hairpin loop is supported primarily by AlphaFold predictions and indirect mutagenesis data. No direct experimental evidence demonstrates that the loop physically occupies the ZF DNA binding surface in solution. The SAXS data are consistent with the model but do not uniquely prove it, as multiple conformational models could fit the scattering profiles. The mutagenesis data show that altering loop charges affects DNA binding, but this could be explained by long-range electrostatic effects rather than direct competition for the binding site.
- **Why it matters** The proposed mechanism is the central novelty of the paper. Without direct evidence for the intramolecular interaction, the conclusion remains speculative and the mechanistic claim is not established.
- **Resolution test** Provide direct evidence of the loop-ZF interaction, for example: (1) NMR chemical shift perturbations or HSQC titrations of the ZF domain with the NT peptide; (2) crosslinking or hydrogen-deuterium exchange mass spectrometry; (3) a mutant ZF domain with disrupted positive charges on the DNA binding surface that shows loss of auto-inhibition; (4) FRET or other solution-based distance measurements that report on the loop-ZF proximity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** SAXS model validation
- **Claim pointer** The authors state that the single best-fit model for the experimental SAXS profile is the AlphaFold model with the NT loop occupying the ZF surface, with chi-squared values of 1.02-1.45
- **Evidence pointer** Figure 5C-F; Results section "An auto-inhibitory model of the N-terminal helix of ZNF410 in the absence of DNA"
- **Concern** The manuscript does not show the actual SAXS fit curves or residuals for the models presented. Chi-squared values alone are insufficient to judge model quality, especially for flexible systems where multiple models may fit similarly. The authors do not report whether alternative models (e.g., with the loop displaced but other conformations) were tested and rejected. The BILBOMD sampling and MultiFoXS selection procedure is described but the ensemble analysis is not shown in sufficient detail.
- **Why it matters** The structural interpretation of the SAXS data is a key pillar of the paper. Without transparent model validation and comparison to alternative models, the reader cannot assess whether the proposed conformation is uniquely supported.
- **Resolution test** Show overlay plots of experimental and calculated scattering curves with residuals for all models. Report chi-squared values for alternative models (e.g., AlphaFold model without loop-ZF contact, models with loop in different positions). Provide the ensemble composition and weights for the multistate models. Consider reporting the SAXS data quality metrics (e.g., resolution, I(0) values, quality of Guinier fits).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative binding analysis
- **Claim pointer** The authors report KD values of approximately 50-80 nM for the ZF domain and ZF-CT, and 0.4-0.5 micromolar for NT-ZF and FL, representing a 5-8 fold reduction in affinity
- **Evidence pointer** Figure 2B; Results section "The N-terminal region of ZNF410 reduces the ZF DNA binding affinity"
- **Concern** The KD values are derived from only two replicated experiments, and no error bars or statistical analysis are shown in Figure 2B. The manuscript does not report whether the binding curves reached saturation, whether the data were fit with a single-site model, or whether cooperativity was considered. The difference between ZF-CT and NT-ZF/FL is the key observation, but the quantitative reliability of this difference is unclear.
- **Why it matters** The quantitative difference in binding affinity is the primary biochemical evidence for auto-inhibition. If the KD measurements are not robust, the conclusion is weakened.
- **Resolution test** Report KD values with standard deviations from at least three independent experiments. Show representative binding curves with fits. Perform statistical testing (e.g., one-way ANOVA with multiple comparison correction) to establish significance of differences. Consider reporting the Hill coefficient to assess cooperativity.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of ChIP-seq data
- **Claim pointer** The authors state that the isolated ZF domain binds more strongly than full-length ZNF410 in cells, based on ChIP-seq peak analysis
- **Evidence pointer** Figure 2C-D; Results section "The N-terminal region of ZNF410 reduces the ZF DNA binding affinity"
- **Concern** The ChIP-seq analysis compares overexpressed HA-ZF1-5 with overexpressed HA-ZNF410 FL. The authors do not report expression levels of the two constructs, which could differ substantially and confound the comparison. The number of peaks (25 vs 95) is used to infer binding strength, but peak number is not a direct measure of affinity. The analysis of H3K27ac association is interesting but the interpretation that FL is recruited to open chromatin by non-ZF interactions is speculative.
- **Why it matters** The in-cell data are used to support the in vitro findings. If the ChIP-seq comparison is confounded by expression differences or other factors, the in-cell claim is not established.
- **Resolution test** Report protein expression levels of HA-ZF1-5 and HA-ZNF410 FL (e.g., by western blot). Normalize peak calling accordingly. Consider performing quantitative ChIP-qPCR at known ZNF410 binding sites to directly compare occupancy. Report the number of biological replicates for the ChIP-seq experiments.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Conservation analysis
- **Claim pointer** The authors claim that the hairpin loop and its acidic residues are conserved across vertebrates, supporting functional significance
- **Evidence pointer** Figure 6F; Results section "Release of auto-inhibitory loop upon DNA binding"
- **Concern** The conservation analysis is presented briefly and the alignment is not shown in detail. The statement that "seven are present in the corresponding but shorter loop of the L. oculatus ortholog" suggests the fish loop is shorter, which may affect the structural interpretation. The conservation of the interacting residues is stated but the statistical significance of this conservation is not assessed.
- **Why it matters** Evolutionary conservation is used to support the biological relevance of the proposed mechanism. If the analysis is not rigorous, this support is weakened.
- **Resolution test** Show the full sequence alignment with the loop region highlighted. Perform a statistical test for conservation (e.g., comparing to background conservation rates). Discuss the implications of the shorter fish loop for the proposed mechanism.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of nomenclature
- **Affected element** Figure 1 and text
- **Evidence pointer** Figure 1F; Results section "ZNF410 is predicted to contain three ordered regions"
- **Issue** The naming of the loop as "Loop-4B" and the helix as "alphaB" is not standard and may confuse readers. The relationship between these names and the secondary structure elements is not clearly explained.
- **Required correction** Define the naming convention clearly or use standard nomenclature. Consider providing a schematic diagram that labels all structural elements.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** SAXS data collection
- **Evidence pointer** Materials and Methods section "SEC-SAXS data collection and processing"
- **Issue** The manuscript states that SAXS data were collected at the SIBYLS beamline but does not report the beamline configuration, exposure times, number of frames collected, or data reduction procedures in sufficient detail for reproduction.
- **Required correction** Provide additional experimental details including beamline parameters, data collection strategy, and reduction software used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Binding assays
- **Evidence pointer** Figure 2B
- **Issue** The figure does not show individual data points, error bars, or statistical significance indicators.
- **Required correction** Add error bars and individual data points to the figure. Report the number of replicates and statistical test used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of alternative models
- **Affected element** Discussion section
- **Evidence pointer** Discussion section "Structure and apparent auto-inhibition of ZNF410"
- **Issue** The authors do not discuss alternative explanations for the reduced DNA binding of full-length ZNF410, such as the NT domain causing steric hindrance without specific DNA mimicry, or the NT domain inducing a conformational change in the ZF array that reduces affinity.
- **Required correction** Add a paragraph discussing alternative models and why the DNA mimicry model is preferred.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 4
- **Evidence pointer** Figure 4D-F
- **Issue** The Kratky plots are described in the text but the figure quality is not sufficient to clearly see the differences between samples described. The red dashed lines mentioned in the text are not clearly visible.
- **Required correction** Improve figure resolution and ensure all annotations mentioned in the text are clearly visible.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Data availability section
- **Issue** The SASBDB accession codes are provided but the manuscript does not state which specific data files correspond to which figure panels.
- **Required correction** Add a table or statement linking each SASBDB accession to the corresponding figure and sample.

- **Technical failings that need to be addressed before the case is established** R1-M1 (direct evidence for loop-ZF interaction), R1-M2 (SAXS model validation and alternative model testing), R1-M3 (quantitative robustness of KD measurements)

- **Assessment against Nature-style criteria** 
  - Originality: The concept of an intramolecular DNA-mimicking domain providing cis-acting auto-regulation is novel and would be of interest to a broad readership. However, the concept of DNA mimicry by proteins is established, and the novelty lies in the intramolecular and cis-acting nature, which is not fully established by the data.
  - Scientific importance: The work addresses an important question in transcription factor biology, specifically how a factor with a single target gene achieves specificity. The potential implications for understanding ZNF410 regulation in erythroid development and hemoglobin switching are significant.
  - Interdisciplinary readership: The combination of structural biology (SAXS), biochemistry, bioinformatics, and AI-based structure prediction would appeal to readers across multiple disciplines. The biological context (hemoglobin switching) broadens the appeal.
  - Technical soundness: The experimental design is generally sound, but the central claim lacks direct evidence. The SAXS modeling requires more rigorous validation. The binding assays need more replicates and statistical analysis.
  - Readability for nonspecialists: The manuscript is generally well-written and accessible. The figures are informative, though some could be improved. The abstract clearly states the main findings and implications.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents an interesting hypothesis with promising preliminary data, but the central claim of DNA mimicry by the hairpin loop requires direct experimental evidence. The SAXS modeling needs more rigorous validation, and the binding data need more robust statistical treatment. If these concerns are addressed, the manuscript would make a valuable contribution to the field.

## Risk / unsupported claims
- The claim that the hairpin loop "mimics the structure and electrostatics of DNA" is not directly supported by experimental evidence; it is inferred from AlphaFold predictions and mutagenesis data
- The claim that the NT domain "occupies the ZF DNA binding surface" in solution is not directly demonstrated; SAXS data are consistent but not unique
- The claim that phosphorylation of the hairpin loop could regulate DNA binding is purely speculative with no experimental support
- The statement that "the single best-fit model for the experimental SAXS profile is the original AlphaFold model" is not verifiable without seeing the fit quality and comparison to alternative models
- The ChIP-seq comparison between HA-ZF1-5 and HA-ZNF410 FL may be confounded by differences in expression levels, which are not reported
- The claim that the CT region "becomes ordered and folds back onto the rest of the protein" upon DNA binding is speculative and not directly supported by the data