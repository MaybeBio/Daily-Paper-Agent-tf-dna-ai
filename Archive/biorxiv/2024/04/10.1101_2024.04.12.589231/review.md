## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, data availability, funding, competing interests, contributions, acknowledgements, references)
- **Assessment boundary** Scientific content, technical soundness, structural biology quality, functional validation, rational engineering claims, and consistency with Nature-style criteria. Editorial or formatting issues are noted only where they affect scientific clarity.
- **Shared manuscript claim summary** The authors characterise the BREX phage defence system from Salmonella enterica serovar Typhimurium ST313 strain D23580, present the first X-ray crystal structures of the PglX methyltransferase (apo and bound to the phage-encoded DNA mimic Ocr), demonstrate that PglX is the sole specificity factor for both host methylation and phage defence, and show that rational engineering of PglX can broaden the recognised DNA motif and the range of targeted phages.
- **Visible evidence base** Crystal structures of PglX-SAM (3.4 Å) and PglX-SAM:Ocr (3.5 Å); EOP assays with Salmonella and coliphages; systematic gene deletion analysis in E. coli; MinION and PacBio methylation sequencing; in vitro methyltransferase assay; analytical SEC; AlphaFold modelling; sequence alignments and covariation analysis.
- **Missing materials affecting confidence** Supplementary figures and tables (Fig. S1–S12, Tables S1–S4) are referenced but not provided; PDB validation reports are not available; raw sequencing data are deposited but not accessible here; details of the covariation analysis and the full list of 23 mutants are only partially described in the main text.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and timely contribution to the understanding of BREX phage defence systems. The first crystal structures of PglX, both alone and in complex with the DNA mimic Ocr, are valuable and will be of interest to the phage defence and structural biology communities. The demonstration that PglX is the sole specificity factor, and the successful rational engineering to alter both methylation motif and phage targeting, are significant advances. However, several technical concerns must be addressed before the case is fully established, particularly regarding the resolution of the structures, the interpretation of the Ocr-bound complex, the in vitro methyltransferase assay, and the generalisability of the engineering approach.
- **Who would be interested in the results, and why** Researchers studying bacterial anti-phage defence systems, particularly BREX and related methylation-dependent systems; structural biologists interested in DNA methyltransferases and protein-DNA mimicry; microbiologists studying host-pathogen interactions and phage therapy; and synthetic biologists interested in engineering defence systems for tailored applications.
- **Major strengths** 1. First experimental structures of a BREX PglX protein, filling a key gap in the field. 2. Clear demonstration that PglX is the sole specificity factor, resolving a long-standing question. 3. Successful rational engineering of PglX to alter both methylation specificity and phage defence, with potential practical applications. 4. Comprehensive genetic and epigenomic characterisation in both native and heterologous hosts. 5. The Ocr-bound structure provides mechanistic insight into how a DNA mimic can inhibit BREX.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (structure resolution and refinement), R1-M2 (Ocr complex interpretation), R1-M3 (in vitro methyltransferase assay), R1-M4 (engineering generalisability).
- **Assessment against Nature-style criteria**  
  *Originality*: High. The structures are novel and the engineering approach is innovative.  
  *Scientific importance*: High. BREX is a widespread and poorly understood defence system; this work provides mechanistic clarity and a path to applications.  
  *Interdisciplinary readership*: Moderate to high. The topic bridges microbiology, structural biology, and synthetic biology, but the presentation is somewhat specialised.  
  *Technical soundness*: Moderate. The genetic and epigenomic data are solid, but structural and biochemical concerns (see R1-M1 to R1-M3) need resolution.  
  *Readability for nonspecialists*: Moderate. The abstract and introduction are accessible, but the results section assumes significant background knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved. The core claims are likely correct, but the current evidence does not fully establish them, particularly regarding the structural interpretations and the in vitro activity.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to present the first X-ray crystal structures of PglX, including a PglX-SAM complex at 3.4 Å and a PglX-SAM:Ocr complex at 3.5 Å, and use these to propose modes of DNA binding.
- **Evidence pointer** Results section "Structure of PglX shows SAM binding for methyltransferase activity"; Table 1; Fig. 4; Fig. 5
- **Concern** The resolution of both structures (3.4 Å and 3.5 Å) is modest, and the manuscript does not provide key quality indicators such as R-free/R-work, Ramachandran statistics, B-factor distributions, or electron density maps. At this resolution, the precise positioning of side chains, particularly those proposed to be involved in motif recognition and Ocr binding, is uncertain. The authors state that two loop regions could not be modelled due to absent density, but do not discuss how this affects the interpretation of the SAM-binding pocket or the Ocr interface. Furthermore, the manuscript does not describe how the structures were validated (e.g., simulated annealing omit maps, cross-validation) or whether the AlphaFold model used for molecular replacement was appropriately trimmed or modified.
- **Why it matters** The structural claims are central to the paper's conclusions about PglX function and mechanism. Without robust validation, the proposed DNA-binding modes and the interpretation of the Ocr complex remain speculative, undermining the mechanistic narrative.
- **Resolution test** Provide full refinement and validation statistics (R-free, R-work, Ramachandran, MolProbity score, etc.) for both structures. Show representative electron density for key regions, especially the SAM-binding pocket, the Ocr interface, and the unmodelled loops. Discuss how the resolution limits the interpretation of side-chain interactions. If possible, provide higher-resolution structures or complementary biophysical validation (e.g., mutagenesis coupled with binding assays).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of structural data
- **Claim pointer** The authors conclude that Ocr binds to the C-terminal domain of PglX and acts as a DNA mimic, sequestering PglX and preventing DNA recognition.
- **Evidence pointer** Results section "PglX forms a heterotetrameric complex with inhibitor Ocr"; Fig. 5; Fig. 6
- **Concern** The PglX-SAM:Ocr structure is solved at 3.5 Å, and the authors infer a heterotetrameric complex (two PglX monomers and one Ocr dimer) based on crystallographic symmetry. However, the manuscript does not provide direct biochemical evidence for the stoichiometry in solution (e.g., multi-angle light scattering, analytical ultracentrifugation, or native mass spectrometry). The analytical SEC data show a peak at approximately 379 kDa, but the interpretation relies on a calculated hydrodynamic radius from an AlphaFold model, which may not accurately reflect the solution state. Additionally, the authors do not demonstrate that Ocr binding is competitive with DNA binding, which is central to the proposed mechanism of inhibition.
- **Why it matters** The proposed mechanism of BREX inhibition by Ocr is a key finding. If the stoichiometry or the competitive binding model is incorrect, the mechanistic conclusions are weakened, and the utility of the structure for understanding BREX function is reduced.
- **Resolution test** Provide direct evidence of the solution stoichiometry of the PglX-Ocr complex (e.g., SEC-MALS, AUC, or native MS). Perform binding assays (e.g., electrophoretic mobility shift assay, surface plasmon resonance, or isothermal titration calorimetry) to demonstrate that Ocr competes with DNA for binding to PglX. If possible, mutate key residues at the PglX-Ocr interface and test the effect on inhibition.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation
- **Claim pointer** The authors state that PglX is the sole specificity factor for BREX methylation and phage defence, and that rational engineering of PglX can broaden the recognised motif and targeted phages.
- **Evidence pointer** Results section "PglX can be rationally engineered to alter phage target and methylation motif"; Fig. 7
- **Concern** The in vitro methyltransferase assay (Fig. S6) showed no detectable activity for PglX alone, and the authors hypothesise that larger BREX complexes are required. This is a reasonable hypothesis, but it means that the direct biochemical activity of PglX as a methyltransferase is not demonstrated. The engineering claims rely on in vivo methylation data (PacBio) and EOP assays, which are convincing but do not directly show that the engineered PglX variants are responsible for the observed changes in methylation specificity. The manuscript does not rule out the possibility that other BREX components contribute to motif recognition or that the observed broadening is due to off-target effects.
- **Why it matters** The claim that PglX is the sole specificity factor is a central conclusion. If other components contribute to specificity, the engineering approach may not be as generalisable as claimed. The lack of in vitro activity also leaves a gap in the mechanistic understanding.
- **Resolution test** Provide direct evidence that purified PglX (or a PglX-containing complex) can methylate DNA in vitro with the predicted specificity. If the complex is required, reconstitute it with purified components. For the engineered variants, demonstrate that the purified mutant proteins have altered DNA-binding or methylation specificity in vitro. Alternatively, provide genetic evidence (e.g., complementation with mutant pglX in a clean background) that the engineered PglX is solely responsible for the observed phenotype.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalisability of engineering approach
- **Claim pointer** The authors claim that rational engineering of PglX can broaden the range of targeted phages and methylation motifs, suggesting a general strategy for reprogramming BREX specificity.
- **Evidence pointer** Results section "PglX can be rationally engineered to alter phage target and methylation motif"; Fig. 7
- **Concern** The engineering was based on sequence covariation and structural alignment with MmeI, but only one successful mutant (mutant 3, T802A and S838N) is described in detail. The other 22 mutants were largely inactive, and the authors do not provide a systematic analysis of why these failed. The success of mutant 3 may be idiosyncratic, and it is unclear whether the approach can be generalised to other motifs or BREX systems. The manuscript does not discuss the potential for off-target effects or the stability of the engineered variants.
- **Why it matters** The claim of "rational engineering" implies a general strategy. If the approach only works in this specific case, the broader significance is reduced. A more systematic analysis would strengthen the claim and provide guidance for future engineering efforts.
- **Resolution test** Provide a more detailed analysis of the 23 mutants, including structural rationale for the failures. Test the engineering approach on additional motifs or in a different BREX system to demonstrate generalisability. If possible, determine the structure of an engineered PglX variant bound to its new cognate motif to validate the design principles.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract; Introduction
- **Issue** The abstract and introduction use several abbreviations (e.g., BREX, PglX, Ocr, N6mA) without defining them at first use. This may hinder readability for nonspecialists.
- **Required correction** Define all abbreviations at first use in the abstract and introduction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Fig. 3
- **Evidence pointer** Fig. 3
- **Issue** The methylation data in Fig. 3b are presented as percentages, but the number of sites analysed and the statistical significance of differences between strains are not reported. This makes it difficult to assess the robustness of the conclusions.
- **Required correction** Provide the number of sites analysed, confidence intervals, and statistical tests for the methylation comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Materials and Methods, "Protein crystallization and structure determination"
- **Evidence pointer** Materials and Methods
- **Issue** The manuscript states that the AlphaFold model was used for molecular replacement but does not describe how the model was prepared (e.g., trimming of low-confidence regions, domain separation). This is important for reproducibility.
- **Required correction** Describe the preparation of the search model, including any modifications made to the AlphaFold prediction.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion speculates about the role of BrxL in modulating BREX activity, but this is not directly tested. The speculation is reasonable but should be clearly labelled as such.
- **Required correction** Clearly distinguish between conclusions supported by data and speculative interpretations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability section
- **Evidence pointer** Data Availability
- **Issue** The authors state that "all other data needed to evaluate the conclusions" are in the paper or supplementary, but the supplementary materials are not provided with this submission. This makes it impossible to fully evaluate the claims.
- **Required correction** Ensure that all supplementary data are made available with the manuscript for review.

## Risk / unsupported claims
- The claim that PglX is the sole specificity factor for BREX is supported by genetic data but not by direct biochemical evidence, as the in vitro methyltransferase assay showed no activity.
- The proposed DNA-binding modes based on structural alignment with MmeI and the Ocr complex are speculative and not validated by direct DNA-binding experiments.
- The generalisability of the rational engineering approach is not established, as only one successful mutant is described in detail.
- The stoichiometry of the PglX-Ocr complex in solution is inferred from crystallographic symmetry and analytical SEC but is not directly confirmed.
- The role of BrxL in modulating BREX activity is speculative and not directly tested.