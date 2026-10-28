## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and data availability statements
- **Assessment boundary** Structural and functional characterization of NPR1 in plant immunity, including cryo-EM and crystal structures, biochemical assays, and genetic validation
- **Shared manuscript claim summary** The authors report cryo-EM and crystal structures of Arabidopsis NPR1 and its complex with transcription factor TGA3, revealing a bird-shaped homodimer architecture, a unique zinc-finger motif, SA-induced folding and docking of the SBD onto ankyrin repeats, and an enhanceosome model in which dimeric NPR1 bridges two TGA3 dimers to activate transcription
- **Visible evidence base** Cryo-EM structures of apo NPR1 (3.8 Å), NPR1–SA complex, NPR12–TGA32 and TGA32–NPR12–TGA32 complexes (3.6 Å), crystal structures of NPR1(ΔSBD) (3.06 Å) and TGA3 NID (1.5 Å), SAXS data, EMSA, mutagenesis, transient expression assays in N. benthamiana, stable transgenic Arabidopsis lines, pathogen infection assays, and qPCR gene expression analyses
- **Missing materials affecting confidence** Extended Data figures and tables referenced but not provided in the submitted text; Supplementary Table 1 (primers) not provided; specific resolution values for the NPR1–SA complex not stated; detailed cryo-EM validation metrics (FSC curves, model statistics) not included in the visible text; source data not accessible

## Reviewer

- **Overall assessment** This manuscript presents a substantial structural and functional characterization of NPR1, a central regulator of plant immunity. The work addresses a long-standing gap in the field by providing the first high-resolution structures of NPR1 and its complex with TGA3. The architectural findings, including the bird-shaped homodimer, the unique zinc-finger motif, and the SA-induced SBD docking mechanism, are novel and potentially transformative. The proposed enhanceosome model for NPR1 function is well supported by the combination of structural, biochemical, and genetic data. However, several technical aspects require clarification, particularly regarding the SA-bound state, the functional significance of the palmitic acid binding, and the quantitative support for the enhanceosome model. The genetic evidence for the dimerization requirement is compelling but would benefit from additional controls and discussion of potential off-target effects.

- **Who would be interested in the results, and why** Plant biologists studying innate immunity and salicylic acid signaling will find this work of immediate relevance. Structural biologists interested in BTB domain proteins, transcriptional coactivators, and enhanceosome assembly will also be engaged. The findings have broader implications for understanding how immune signaling integrates with transcriptional reprogramming, which could interest researchers working on plant-microbe interactions, crop disease resistance, and the evolution of immune regulatory mechanisms. The unexpected observation of palmitic acid binding to TGA3 may attract interest from lipid signaling researchers.

- **Major strengths**
  1. First structural characterization of full-length NPR1, filling a critical gap in the field
  2. Multi-technique approach combining cryo-EM, X-ray crystallography, SAXS, and functional assays
  3. The SA-induced SBD folding and docking mechanism provides a direct structural explanation for SA-dependent NPR1 activation
  4. The enhanceosome model is supported by multiple lines of evidence including structure, EMSA, and genetic data
  5. The identification of a unique zinc-finger motif in the BTB domain adds new insight into NPR1 regulation
  6. The dimerization-deficient mutant provides strong genetic evidence for the functional importance of the NPR1 dimer

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "after stimulation, salicylic-acid-induced folding and docking of the salicylic-acid-binding domain onto ankyrin repeats is required for the transcriptional cofactor activity of NPR1"
- **Evidence pointer** Figure 1e–g, Extended Data Fig. 4, Extended Data Table 1; specific resolution of the NPR1–SA complex not stated in the visible text
- **Concern** The NPR1–SA complex structure is central to the main mechanistic claim, yet the resolution of this map is not reported in the visible text. The authors note that "the limited resolution in this region prevented detailed structural modelling" for the SBD, which raises questions about the confidence in the SA-induced conformational change. The modelling approach using SWISS-MODEL and docking into low-resolution density needs more rigorous validation. Additionally, the SA concentration used (0.2 mM) during refolding is not justified, and no binding affinity data are presented to support that this concentration is physiologically relevant or sufficient for saturation.
- **Why it matters** The SA-induced SBD docking mechanism is the central mechanistic finding of the paper. If the structural evidence for this conformational change is not robust, the main conclusion is weakened. The field has debated whether SA binds NPR1 directly and how this regulates its activity; this paper claims to resolve this, but the structural evidence must be definitive.
- **Resolution test** Provide the resolution of the NPR1–SA map, FSC curves, and local resolution estimates. Show clear density for the SBD in the SA-bound state that is absent in the apo state. Include SA binding affinity measurements (e.g., ITC or MST) and demonstrate that the conformational change is SA-specific using a structurally related but inactive SA analogue as a negative control.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors state "our structure of the TGA32–NPR12–TGA32 complex, DNA-binding assay and genetic data show that dimeric NPR1 activates transcription by bridging two fatty-acid-bound TGA3 dimers to form an enhanceosome"
- **Evidence pointer** Figure 3a–g, Extended Data Fig. 5–7, Extended Data Table 1
- **Concern** The enhanceosome model is a significant conceptual advance, but the evidence for the stoichiometry and the functional requirement for bridging two TGA3 dimers is not fully quantitative. The EMSA data show shifted bands but do not clearly demonstrate the stoichiometry of the complex. The genetic data with npr1(dim) show loss of function but do not directly prove that the defect is specifically due to inability to bridge two TGA3 dimers rather than other dimerization-dependent functions. The claim that the complex forms an enhanceosome requires demonstration that the DNA-bound complex contains the full TGA32–NPR12–TGA32 assembly on a single DNA molecule.
- **Why it matters** The enhanceosome model has implications for how NPR1 regulates diverse target genes and how it might interact with other transcription factors. If the stoichiometry is incorrect or the bridging mechanism is not essential, the model needs revision. This is a key conceptual contribution that should be rigorously supported.
- **Resolution test** Perform quantitative EMSA or analytical ultracentrifugation to determine the stoichiometry of the NPR1–TGA3–DNA complex. Use single-molecule imaging or Förster resonance energy transfer to demonstrate that both TGA3 dimers bind the same DNA molecule in the enhanceosome. Generate NPR1 mutants that can dimerize but cannot bridge two TGA3 dimers to test the functional requirement for bridging specifically.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state "the removal of the BACK helix bundle does not abolish the CUL3A interaction" and use this to support the functional relevance of the BHB
- **Evidence pointer** Extended Data Fig. 2a; location of the CUL3A interaction assay not fully described in the visible text
- **Concern** The CUL3A interaction data are presented as a single extended data figure with limited methodological detail. The authors do not report whether the interaction is direct or mediated by other factors, nor do they provide quantitative binding data. The claim that the BHB is not required for CUL3A interaction is based on a deletion mutant, but the authors do not test whether the BHB contributes to the affinity or stability of the interaction. Additionally, the functional significance of the CUL3A interaction for NPR1 function is not tested in this study.
- **Why it matters** The CUL3A interaction is relevant to NPR1 function as a potential ubiquitin ligase substrate adaptor. If the BHB is not required for this interaction, its role in NPR1 function needs clarification. The structural similarity to SPOP's 3-box suggests a potential functional link that is not experimentally addressed.
- **Resolution test** Provide a detailed description of the CUL3A interaction assay, including purification tags, concentrations, and detection methods. Perform quantitative binding assays (e.g., pull-down with purified proteins, ITC, or BLI) to determine the affinity of the NPR1–CUL3A interaction and whether the BHB contributes to it. Test the functional significance of the CUL3A interaction for NPR1-dependent gene expression using mutants that disrupt the interaction.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state "the npr1(dim) mutant not only failed to self-interact, but also eluted off the size-exclusion column at a later volume than WT NPR1" and use this mutant to establish the functional requirement for dimerization
- **Evidence pointer** Figure 4b–h, Extended Data Fig. 8
- **Concern** The npr1(dim) mutant carries four mutations (L49D/F53D/V56D/V83K) at the dimer interface. While the authors show loss of self-interaction and altered elution volume, they do not demonstrate that the mutant protein is properly folded. The low-resolution cryo-EM map of npr1(dim) shows a "single-wing shape," but the resolution is not stated and the interpretation that this represents a monomer is not rigorously validated. The mutant also shows increased nuclear accumulation, which complicates interpretation of the transcriptional defects, as the subcellular localization difference could contribute to the phenotype independently of dimerization.
- **Why it matters** The npr1(dim) mutant is the key genetic tool supporting the functional importance of dimerization. If the mutant is misfolded or mislocalized, the conclusions about dimerization being required for function are weakened. The field needs confidence that the observed phenotypes are specifically due to loss of dimerization.
- **Resolution test** Provide biophysical characterization of the npr1(dim) protein (e.g., circular dichroism, thermal stability, or analytical ultracentrifugation) to demonstrate proper folding. State the resolution of the npr1(dim) cryo-EM map and provide validation metrics. Generate additional dimerization mutants at different interface residues to confirm the phenotype is due to loss of dimerization rather than a specific mutation effect. Address the nuclear accumulation difference by examining whether the transcriptional defect persists when nuclear localization is equalized.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract uses "defence transcriptome" without explaining what this means for readers outside plant immunity. The term "enhanceosome" is introduced without definition.
- **Required correction** Briefly define "defence transcriptome" as the set of genes activated during immune responses, and add a brief parenthetical explanation of "enhanceosome" as a multi-protein complex that enhances transcription.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Cryo-EM data processing
- **Evidence pointer** Methods section, Cryo-EM data processing and model building
- **Issue** The methods describe data processing steps but do not report key validation metrics such as gold-standard FSC curves, model-to-map fit (CCmask), or MolProbity scores for the final models. These are standard requirements for structural papers.
- **Required correction** Add a supplementary table or extended data figure reporting resolution estimates, FSC curves, model statistics (Ramachandran, rotamer outliers, clash score), and model-to-map correlation coefficients for all deposited structures.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Statistics and reproducibility
- **Evidence pointer** Methods, Statistics and reproducibility section
- **Issue** The statistics section states that "asterisks and lowercase letters indicate statistical significance tested either by Student's t-tests (two groups) or ANOVA (multiple groups) at a significance threshold of P < 0.05" but does not specify which test was used for which figure panel, nor whether corrections for multiple comparisons were applied.
- **Required correction** Specify the statistical test used for each figure panel in the figure legends, and state whether multiple comparison corrections were applied for ANOVA analyses.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion of palmitic acid
- **Evidence pointer** Figure 3d, Extended Data Fig. 6, Methods, Lipid extraction
- **Issue** The palmitic acid bound to TGA3 NID is presented as an unexpected finding, but the authors do not discuss its potential functional significance or whether it is a crystallization artifact. No functional experiments are performed to test the role of palmitic acid binding.
- **Required correction** Add a brief discussion of whether palmitic acid binding is likely to be physiologically relevant, and acknowledge that its functional significance remains to be tested. If possible, include a control experiment with a lipid-free TGA3 NID to confirm the binding is specific.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Figure 1
- **Evidence pointer** Figure 1a–g
- **Issue** The bird-shaped dimer description is memorable but the figure labels and legend may not clearly guide readers through the domain architecture, especially for those unfamiliar with NPR1 domain organization.
- **Required correction** Add a domain schematic in Figure 1a or as a separate panel that clearly labels the BTB domain, BACK helix bundle, ankyrin repeats, and SBD, with color coding matching the structural representations.

## Risk / unsupported claims
1. The claim that SA induces SBD folding and docking is based on a low-resolution NPR1–SA map where the SBD could not be modelled in detail. The resolution of this map is not stated in the visible text, making the structural evidence difficult to evaluate.
2. The enhanceosome model is supported by structural and biochemical data, but the stoichiometry of the complex is not rigorously established. The claim that NPR1 "bridges" two TGA3 dimers implies a specific architecture that is not directly demonstrated.
3. The statement that the BACK helix bundle is "much shorter than BACK (4 versus 8 helices)" and the naming of this domain as "BHB" is a new nomenclature that may not be universally accepted. The authors should clarify whether this is a novel domain or a variant of known BACK domains.
4. The functional significance of the palmitic acid binding to TGA3 NID is not tested, and the claim that this "further implicates lipid metabolism in regulating plant immunity" is speculative without functional validation.
5. The claim that npr1(dim) is "deficient in oligomer formation" is based on in vitro and cell-based assays, but the authors do not directly demonstrate that the mutant protein is properly folded and functional as a monomer.
6. The statement that "the lack of a direct contact between SBD and TGA suggests that the SBD–ANK-docking conformation may enable post-translational modification" is speculative and not directly tested in this study.
7. The resolution of the npr1(dim) cryo-EM map is not stated, and the interpretation of the "single-wing shape" as a monomer is not rigorously validated with quantitative fitting or comparison to the dimer structure.