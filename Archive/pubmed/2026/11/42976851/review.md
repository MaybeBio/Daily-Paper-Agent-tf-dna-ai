## Review setup
- **Input scope** Full manuscript text including Summary, Introduction, Results, Discussion, STAR Methods, and Supplementary Figure legends (figures themselves not provided)
- **Assessment boundary** Scientific content, experimental design, data interpretation, methodological rigor, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors propose that age-associated oxidative stress remodels mitochondrial nucleoid architecture via species-specific redox modifications of TFAM (cysteine oxidation in human, methionine oxidation in mouse), leading to reduced mtDNA transcript abundance and bioenergetic decline in aging neurons, and that expression of oxidation-resistant TFAM variants can restore nucleoid compaction, transcription, and ATP production
- **Visible evidence base** Text descriptions of results from confocal microscopy, MINFLUX nanoscopy, smFISH, live-cell ATP and redox biosensors, Seahorse analysis, in vitro phase separation assays, EMSA, LC-MS/MS, immunoblotting, machine learning segmentation, and electrophysiology; figure legends referenced but figures not directly viewable
- **Missing materials affecting confidence** Actual figures and supplementary figures (images, graphs, statistical plots) not provided; numerical data with effect sizes and variance not fully reported in text; details of MINFLUX data processing and quality control; full statistical outputs; raw mass spectrometry data; details of machine learning training and validation metrics beyond summary statements

## Reviewer
- **Overall assessment** This manuscript addresses a fundamental question in neurobiology with a sophisticated multi-technique approach. The central hypothesis, that redox-dependent remodeling of mitochondrial nucleoids contributes to bioenergetic decline in aging neurons, is timely and mechanistically plausible. The combination of super-resolution imaging, single-molecule transcript mapping, biochemical reconstitution, and functional rescue experiments is impressive in scope. However, several critical issues need to be addressed. The causal link between TFAM oxidation and bioenergetic decline is not fully established, as the rescue experiments show partial effects and the specificity of the oxidation-resistant variant requires further validation. The species-specific mechanism, while intriguing, raises questions about the generalizability of the findings. The manuscript would benefit from clearer presentation of quantitative data and effect sizes, and from additional controls to rule out off-target effects of the TFAM variants.

- **Who would be interested in the results, and why** Researchers in mitochondrial biology, aging research, neurobiology, and neurodegeneration would find these results highly relevant. The study provides a mechanistic link between oxidative stress and mitochondrial genome organization, which has implications for understanding age-related bioenergetic decline and potentially for therapeutic strategies targeting TFAM. The methodological advances in applying MINFLUX to mitochondrial nucleoid analysis would also interest the super-resolution microscopy community. The species-specific redox mechanism is of evolutionary and comparative interest.

- **Major strengths** 1) The study addresses a significant and unresolved question in aging neurobiology with a clear hypothesis. 2) The multi-scale approach, from single-molecule imaging to functional bioenergetic measurements, is comprehensive and technically ambitious. 3) The identification of distinct redox mechanisms in human and mouse TFAM is novel and provides a cautionary note for cross-species extrapolation. 4) The rescue experiments with oxidation-resistant TFAM variants provide a proof-of-concept for therapeutic intervention. 5) The use of both peripheral and central neurons, as well as human iPSC-derived neurons, strengthens the generalizability of the findings.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** "expressing an oxidation-resistant TFAM variant restores mt-nucleoid organization, mtDNA transcript abundance, and ATP production in aged neurons"
- **Evidence pointer** Results section "Oxidation-resistant TFAM restores mt-nucleoid compaction and bioenergetics in aged neurons"; Figures 8A-8I
- **Concern** The rescue experiments show that hTFAM-C246A partially restores nucleoid compaction, COXI transcript abundance, and ATP levels. However, the text also states that wild-type hTFAM expression alone increased ATP levels, albeit to a lesser extent. This raises the question of whether the observed rescue is due to prevention of oxidation specifically, or simply to overexpression of TFAM providing more functional protein. The authors need to demonstrate that the effect of hTFAM-C246A is significantly greater than what would be expected from increased TFAM dosage alone, and that the variant does not have altered DNA-binding affinity or other properties unrelated to oxidation resistance.
- **Why it matters** The central claim of the paper is that preventing TFAM oxidation is the mechanism by which the variant rescues the aging phenotype. If the rescue is due to non-specific overexpression effects, the causal link between TFAM oxidation and bioenergetic decline is weakened.
- **Resolution test** Include a control with overexpression of a TFAM variant that is oxidation-resistant but also DNA-binding-deficient, or use a titration experiment to match expression levels of wild-type and mutant TFAM. Alternatively, show that the oxidation-resistant variant has identical DNA-binding and bending properties to wild-type TFAM under reducing conditions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic specificity
- **Claim pointer** "cysteine oxidation promotes human TFAM polymerization, whereas methionine oxidation weakens mouse TFAM-mtDNA interactions"
- **Evidence pointer** Results sections "Cysteine oxidation promotes hTFAM polymerization and disrupts mtDNA condensates" and "Methionine oxidation weakens mouse TFAM-mtDNA interactions"; Figures 6 and 7
- **Concern** The manuscript proposes two distinct redox mechanisms for human and mouse TFAM. However, the text does not provide sufficient detail on how the oxidation state of specific residues was confirmed in the cellular context. The in vitro experiments with purified proteins and H2O2 are informative, but it is unclear whether the same modifications occur endogenously in aged neurons. The authors should provide evidence that the specific cysteine and methionine residues identified are actually oxidized in aged cells, and that this oxidation correlates with nucleoid decompaction.
- **Why it matters** The species-specific mechanism is a key novel finding, but without evidence of endogenous oxidation of these specific residues, the physiological relevance of the in vitro observations remains uncertain.
- **Resolution test** Use mass spectrometry on TFAM isolated from young and aged neurons to demonstrate increased oxidation at C49/C246 (human) or M53/M128 (mouse). Alternatively, use cysteine/methionine-specific probes or antibodies to detect oxidation in situ.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor
- **Claim pointer** "Aged neurons exhibit disorganized mt-nucleoids, reduced mitochondrial respiration and ATP production, elevated oxidative stress, and reduced mtDNA transcript abundance"
- **Evidence pointer** Results sections "Aging-associated mt-nucleoid decompaction occurs in peripheral and central neurons" and "Reduced mtDNA transcript abundance in aged neurons"; Figures 1-3
- **Concern** The text describes qualitative differences between young and aged neurons but provides limited quantitative data. For example, the magnitude of the reduction in ATP levels, the percentage change in nucleoid compaction, and the effect sizes for transcript abundance are not clearly stated. The statistical approach is described in the methods, but the actual p-values and effect sizes for key comparisons are not presented in the text. This makes it difficult to assess the biological significance of the observed differences.
- **Why it matters** For a Nature-level journal, the quantitative rigor of the key findings needs to be clearly presented. The reader should be able to assess the magnitude of the aging-related changes and the strength of the statistical support.
- **Resolution test** Provide effect sizes, confidence intervals, and exact p-values for all key comparisons in the text or figure legends. Consider including a summary table of quantitative results.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical validation
- **Claim pointer** "MINFLUX imaging (~3-nm localization precision) reveals an aging-associated mt-nucleoid architecture"
- **Evidence pointer** Results section "MINFLUX nanoscopy reveals aging-associated mt-nucleoid remodeling"; Figures 2A-2H
- **Concern** MINFLUX is a relatively new and technically demanding technique. The manuscript does not provide sufficient details on the validation of the MINFLUX measurements, such as control experiments with known structures, assessment of labeling density effects on localization precision, and the criteria used to define nucleoid boundaries. The text mentions that localization traces with fewer than three points were filtered out, but the potential bias introduced by this filtering is not discussed.
- **Why it matters** The MINFLUX data are central to the claim of nucleoid remodeling. If the technique is not properly validated, the interpretation of the structural changes could be questioned.
- **Resolution test** Include control experiments demonstrating the accuracy and precision of the MINFLUX measurements, such as imaging of DNA origami structures or known protein complexes. Discuss the potential artifacts of the filtering and analysis procedures.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** "Redox-dependent remodeling of mitochondrial nucleoids contributes to bioenergetic decline during neuronal aging"
- **Evidence pointer** Throughout the manuscript
- **Concern** The study uses DRG neurons and hippocampal neurons from mice, and human iPSC-derived cortical neurons. While this is a reasonable approach, the text does not discuss whether the observed mechanism is specific to certain neuronal populations or applies broadly to all neurons. The authors also do not address whether the findings in cultured neurons accurately reflect the in vivo aging process, given the potential for culture-induced stress and the absence of the complex tissue microenvironment.
- **Why it matters** The title and abstract make a general claim about "neuronal aging." If the mechanism is only demonstrated in specific neuronal types or under specific culture conditions, the claim should be appropriately qualified.
- **Resolution test** Discuss the potential limitations of the model systems and qualify the claims accordingly. If possible, include additional data from other neuronal types or from in vivo experiments.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Summary
- **Evidence pointer** Summary section
- **Issue** The summary states that "redox-driven mt-nucleoid remodeling underlies reduced mtDNA transcript abundance and bioenergetic decline." The word "underlies" implies a causal relationship, but the evidence presented is largely correlative. The rescue experiments provide some support for causality, but the effect is partial.
- **Required correction** Consider softening the language to "contributes to" or "is associated with" to more accurately reflect the strength of the evidence.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Introduction
- **Evidence pointer** Introduction section
- **Issue** The introduction mentions that "mitochondrial dysfunction accelerates aging" and "preserving mitochondrial integrity delays functional decline," but does not provide specific citations for these claims. While these are well-established concepts, specific references would strengthen the introduction.
- **Required correction** Add appropriate citations for these statements.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** MINFLUX data analysis
- **Evidence pointer** STAR Methods, "MINFLUX data analysis" section
- **Issue** The description of the MINFLUX data analysis is brief. The text mentions "custom Python scripts" and "custom MATLAB scripts" but does not provide sufficient detail for reproducibility. The criteria for identifying and segregating localization clusters are not fully described.
- **Required correction** Provide more detailed descriptions of the analysis pipeline, including the specific algorithms and parameters used. Consider making the code available.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Quantification and statistical analysis
- **Evidence pointer** STAR Methods, "Quantification and statistical analysis" section
- **Issue** The text states that "All quantifications were conducted without blinding." This is a potential source of bias, particularly for image-based analyses. The authors should discuss why blinding was not performed and whether this could have influenced the results.
- **Required correction** Add a discussion of the potential limitations of not blinding and consider whether any analyses could be re-done with blinding.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section (not provided in full, but referenced)
- **Issue** The text mentions that "the chronic low-dose H2O2 paradigm cannot completely exclude secondary stress responses." This is an important limitation that should be discussed more thoroughly. The authors should also discuss whether the effects of H2O2 are specific to TFAM or could be mediated by other oxidative stress targets.
- **Required correction** Expand the discussion of the limitations of the H2O2 model and the potential for off-target effects.

- **Technical failings that need to be addressed before the case is established** 1) The rescue experiments need to control for TFAM overexpression effects (R1-M1). 2) Evidence for endogenous oxidation of specific TFAM residues in aged neurons is lacking (R1-M2). 3) Quantitative data with effect sizes and statistical details need to be presented more clearly (R1-M3). 4) Validation of MINFLUX measurements and analysis procedures is insufficient (R1-M4).

## Risk / unsupported claims
- The claim that "redox-driven mt-nucleoid remodeling underlies reduced mtDNA transcript abundance and bioenergetic decline" is partially supported but the causal link is not fully established, given the partial rescue and potential for off-target effects.
- The claim of a "conserved mechanism" across species is weakened by the finding of distinct redox mechanisms in human and mouse TFAM. The text acknowledges this but the title and abstract may overstate the conservation.
- The claim that "expression of a redox-resistant, mtDNA-packaging-competent TFAM variant restores mt-nucleoid organization, mtDNA transcript abundance, and ATP production in aged neurons" is supported by the data, but the magnitude of the effect and its physiological significance need to be clarified.
- The statement that "the chronic low-dose H2O2 paradigm is expected to generate intracellular H2O2 concentrations within the physiological nanomolar range" is based on an estimation and should be verified experimentally or with more detailed calculations.
- The generalizability of the findings to all neuronal types and to the in vivo aging process is not fully established, given the use of specific neuronal populations and culture conditions.