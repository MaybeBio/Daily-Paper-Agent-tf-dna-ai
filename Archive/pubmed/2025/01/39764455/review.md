## Review setup
- **Input scope** Full manuscript text (Introduction, Methods, Results, Discussion, Supplementary figure legends referenced but not provided in full)
- **Assessment boundary** Scientific content, methodological rigor, and support of claims based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors propose that WhiA in Mycoplasma gallisepticum acts as a transcriptional repressor of the rpsJ operon, binds a conserved DNA motif (GAYACRCY core plus auxiliary motif), senses ATP via its HEN domain, and thereby provides a feedback loop between translation and energy production in a genome-reduced bacterium.
- **Visible evidence base** EMSA, MST, FRET, AFM, molecular dynamics simulations, CRISPRi knockdown, overexpression, RT-qPCR, proteomics, growth assays
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S20), full proteomics dataset, raw MD trajectories, reporter construct details, statistical analysis details for proteomics

## Reviewer
- **Overall assessment** The manuscript presents a plausible and potentially important model for WhiA function in a genome-reduced bacterium, integrating biochemical, biophysical, and in vivo approaches. The central claim that WhiA represses the rpsJ operon and that ATP modulates this repression is supported by multiple lines of evidence. However, several technical concerns, particularly regarding the interpretation of binding data, the physiological relevance of the ATP concentrations used, and the indirect nature of some in vivo observations, need to be addressed before the case is fully established.
- **Who would be interested in the results, and why** Researchers studying transcriptional regulation in minimal bacteria, particularly Mycoplasma species; those interested in the evolution of regulatory networks in genome-reduced organisms; and the broader community studying the link between metabolism and gene expression. The work also has relevance for synthetic biology efforts aimed at engineering minimal cells.
- **Major strengths** 1) The study addresses a conserved but poorly understood transcription factor in a biologically important group of bacteria. 2) The combination of in vitro biophysics (EMSA, MST, FRET, AFM) with in vivo functional assays (CRISPRi, reporter constructs, proteomics) is comprehensive. 3) The proposed model, linking ATP sensing to ribosomal protein production, is conceptually novel and testable. 4) The identification of a conserved DNA motif across multiple bacterial clades adds evolutionary context.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (ATP binding specificity), R1-M2 (quantitative binding data), R1-M3 (in vivo relevance of ATP sensing), R1-M4 (proteomics causal inference)
- **Assessment against Nature-style criteria** **Originality:** High. The proposed ATP-dependent regulatory mechanism for WhiA is novel and not previously described. **Scientific importance:** Moderate to high. The work advances understanding of minimal regulatory networks, but the broader impact beyond Mycoplasma biology may be limited. **Interdisciplinary readership:** Moderate. The topic will appeal to microbiologists, biochemists, and systems biologists, but may not attract a wide readership outside these fields. **Technical soundness:** Generally sound, but with notable gaps in quantitative rigor and physiological validation (see Major Concerns). **Readability for nonspecialists:** The manuscript is clearly written and the model is well explained, though some sections (e.g., MD methods) are dense.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly those related to ATP binding specificity, quantitative binding analysis, and physiological relevance of the proposed ATP sensing mechanism.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental support for ATP binding
- **Claim pointer** The authors claim that WhiA is a sensor of ATP, with ATP binding to the HEN domain modulating DNA binding.
- **Evidence pointer** Results section "WhiA is a sensor of ATP"; Supplementary Figures S6, S7
- **Concern** The evidence for ATP binding is indirect. The EMSA experiments show that ATP shifts the equilibrium between monomeric and dimeric complexes, and MST gives a Kd of 5 mM. However, no direct binding assay (e.g., isothermal titration calorimetry, surface plasmon resonance, or a competition assay with a non-hydrolyzable ATP analog) is presented. The Kd of 5 mM is at the upper end of physiological ATP concentrations in bacteria, raising questions about whether this interaction is physiologically relevant. Furthermore, the claim that ATP binds specifically to the HEN domain is not directly tested; the MD simulations suggest a binding site, but this is not validated experimentally.
- **Why it matters** The ATP sensing function is central to the proposed model. Without direct evidence of specific ATP binding to the HEN domain and a demonstration that this interaction is physiologically relevant, the model remains speculative.
- **Resolution test** Provide direct binding data (e.g., ITC or MST with a labeled ATP analog) showing specific, saturable binding to the HEN domain. Test whether a non-hydrolyzable ATP analog (e.g., AMP-PNP) has the same effect as ATP in EMSA experiments. Measure intracellular ATP concentrations in M. gallisepticum under the conditions used to demonstrate that the 5 mM Kd is within the physiological range.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative analysis of DNA binding
- **Claim pointer** The authors report Kd values for WhiA binding to DNA (700 nM for WT, >5 μM for negative control) and state that ATP does not affect the overall binding constant.
- **Evidence pointer** Results section "WhiA specifically binds conserved sequence"; Figures 3A–C; Supplementary Figure S5
- **Concern** The Kd values are derived from EMSA data, which is a semi-quantitative method. The authors do not provide details on how the fraction bound was calculated, whether the data were fit to a single-site or cooperative model, or how many independent replicates were performed. The Hill coefficient of 1.8 suggests cooperativity, but the molecular basis for this cooperativity is not explained. The statement that ATP does not affect the overall binding constant is based on a comparison of Kd values that may not be statistically robust given the method.
- **Why it matters** The quantitative binding parameters are used to support the model of WhiA function. If the Kd values are not reliable, the conclusions about the relative contributions of the core and auxiliary motifs, and the effect of ATP, are weakened.
- **Resolution test** Provide a more rigorous quantitative analysis, ideally using a solution-based method (e.g., MST or fluorescence anisotropy) with proper error analysis and statistical comparison of Kd values. Show representative binding curves and fits, and report the number of replicates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Physiological relevance of ATP sensing
- **Claim pointer** The authors propose that WhiA provides a feedback loop between translation and energy production, with ATP levels regulating rpsJ operon repression.
- **Evidence pointer** Results section "WhiA is a sensor of ATP"; Discussion section "The model of Mgal-WhiA functioning"
- **Concern** The in vivo evidence linking ATP levels to WhiA-mediated regulation is indirect. The authors show that CCCP treatment increases ATP levels and upregulates rpsJ operon genes, but this is a global stress response and the effect could be mediated by other factors. The CRISPRi knockdown data show that WhiA represses the rpsJ operon, but the connection to ATP is not directly demonstrated in vivo. The authors do not measure ATP levels in the WhiA knockdown or overexpression strains, nor do they show that the effect of CCCP on rpsJ operon expression is dependent on WhiA.
- **Why it matters** The central claim of the paper is that WhiA provides a feedback loop between translation and energy production. Without direct in vivo evidence that ATP levels modulate WhiA activity, this claim is not fully supported.
- **Resolution test** Measure ATP levels in WhiA knockdown, overexpression, and control strains. Test whether the effect of CCCP on rpsJ operon expression is abolished or reduced in the WhiA knockdown background. Alternatively, use a reporter system where the WhiA binding site is mutated to disrupt ATP sensing and show that this eliminates the response to CCCP.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Causal inference from proteomics
- **Claim pointer** The authors state that WhiA knockdown leads to upregulation of rpsJ operon proteins and that this results in "distortion of ribosomal proteins stoichiometry" and "unfolded protein stress."
- **Evidence pointer** Results section "WhiA modulation imposes direct and indirect effects"; Figure 1C; Supplementary Figure S20; Supplementary Table S5
- **Concern** The proteomics data are descriptive. The authors observe changes in protein abundance, but the causal link between WhiA knockdown, rpsJ operon upregulation, and the downstream effects (chaperone upregulation, growth defects after freezing) is inferred rather than demonstrated. The authors do not rule out off-target effects of the CRISPRi knockdown or the possibility that the observed proteomic changes are due to secondary effects of growth perturbation.
- **Why it matters** The proposed model relies on the specificity of WhiA's effect on the rpsJ operon. If the proteomic changes are non-specific, the model is weakened.
- **Resolution test** Perform a more detailed analysis of the proteomics data, including a comparison of the WhiA regulon with the observed changes. Validate the key findings (e.g., rpsJ operon upregulation, chaperone induction) by independent methods (e.g., western blotting). Use a complementation approach where WhiA is re-expressed in the knockdown strain to show that the phenotypes are rescued.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of model presentation
- **Affected element** Figure 9
- **Evidence pointer** Discussion section "The model of Mgal-WhiA functioning"
- **Issue** The model in Figure 9 is complex and the transition between the "relaxed" and "strained" conformations is not clearly explained in the text. The distinction between the in vitro and in vivo behaviors could be made more explicit.
- **Required correction** Provide a more detailed figure legend and a step-by-step description of the model in the text, clearly stating the differences between in vitro and in vivo conditions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Proteomics analysis
- **Evidence pointer** Methods section "Proteomic analysis"; Results section "WhiA modulation imposes direct and indirect effects"
- **Issue** The statistical methods for the proteomics analysis are not fully described. The authors mention "Benjamimi-Hochberg correction" but do not specify the test used, the number of replicates, or how the fold-change threshold was chosen.
- **Required correction** Provide a complete description of the statistical analysis, including the test used, the number of replicates, and the criteria for significance.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** MD simulations
- **Evidence pointer** Methods section "Docking and molecular dynamics"
- **Issue** The MD simulation methods are described in detail, but the convergence of the simulations is not discussed. The authors do not report the root-mean-square deviation (RMSD) or other metrics to demonstrate that the simulations reached equilibrium.
- **Required correction** Add a brief statement about simulation convergence, including RMSD plots or a reference to supplementary material.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of FRET data
- **Affected element** Results section "HTH domain of Mgal-WhiA specifically recognizes the core motif"
- **Evidence pointer** Figures 5C, 5D
- **Issue** The FRET experiment is described as supporting the bipartite binding model, but the quantitative interpretation is not clear. The authors do not report the FRET efficiency or the distance between the fluorophore and quencher.
- **Required correction** Provide quantitative FRET data (e.g., FRET efficiency) and a discussion of how this supports the proposed model.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Title and Abstract
- **Evidence pointer** Title; Abstract
- **Issue** The title states "feedback loop between translation and energy production," but the evidence for a true feedback loop (i.e., a closed regulatory circuit) is not fully demonstrated. The data support a one-way regulation of the rpsJ operon by ATP, but the return arm of the loop (e.g., ribosomal proteins affecting energy production) is not shown.
- **Required correction** Consider softening the title or providing explicit evidence for the feedback loop, or discuss this as a proposed model rather than an established fact.

## Risk / unsupported claims
- The claim that WhiA is a "sensor of ATP" is not directly supported by binding data; the evidence is indirect (EMSA shifts, MD simulations).
- The claim that the aux motif is crucial for transcriptional regulation is based on reporter assays, but the quantitative effect of aux mutations is not fully reported.
- The claim that WhiA knockdown leads to "unfolded protein stress" is inferred from chaperone upregulation, but direct evidence of protein misfolding is not provided.
- The proposed model of a "feedback loop" between translation and energy production is not fully supported by the data, as the return arm of the loop is not demonstrated.
- The physiological relevance of the ATP Kd (5 mM) is not established, as intracellular ATP concentrations in M. gallisepticum under the relevant conditions are not measured.