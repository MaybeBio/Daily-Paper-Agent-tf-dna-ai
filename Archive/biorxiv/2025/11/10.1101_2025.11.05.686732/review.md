## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, and supplementary figure legends
- **Assessment boundary** Scientific claims, experimental evidence, technical soundness, and alignment with stated conclusions
- **Shared manuscript claim summary** The authors propose that the plant transcription factor MpARF2 forms nanoscopic clusters (nanoclusters) at physiological concentrations, which exhibit high-affinity, switch-like, and sequence-specific DNA binding, distinct from both monomeric/dimeric binding and phase-separated condensates
- **Visible evidence base** In vivo confocal imaging, in vitro dynamic light scattering, centrifugation assays, EMSA, single-molecule TIRF microscopy, single-particle tracking, domain deletion experiments, AlphaFold-Multimer predictions
- **Missing materials affecting confidence** Supplementary figures (S1-S16) and tables (S1-S4) referenced but not provided; movies S1-S3 referenced but not provided; raw data and analysis code repository not accessible for verification

## Reviewer

### Overall assessment
This manuscript presents an intriguing and potentially significant finding regarding the DNA-binding behavior of a plant transcription factor. The authors propose a third scenario for TF-DNA interactions, namely nanoclustering, which bridges the gap between weak monomeric binding and nonspecific condensate formation. The combination of in vivo and in vitro approaches is commendable, and the single-molecule imaging methodology appears well-designed to address the limitations of conventional EMSA. However, several technical concerns and missing details prevent full assessment of the claims. The switch-like binding transition and the proposed micellar structure require stronger quantitative support. The physiological relevance of the measured concentrations and the generalizability to other ARFs or TFs remain open questions.

### Who would be interested in the results, and why
Plant biologists studying auxin signaling and ARF function would find this directly relevant. More broadly, researchers in transcription factor biology, gene regulation, and the emerging field of biomolecular condensates would be interested in the proposed nanoclustering mechanism as an alternative to LLPS. Physical chemists and biophysicists studying protein self-assembly and multivalent interactions would also find the micelle-like model appealing. The work challenges the current dichotomy between monomeric and condensate models of TF function, which has implications for understanding transcriptional regulation in diverse organisms.

### Major Strengths
1. The study addresses a fundamental question in TF biology with a well-defined hypothesis and a multi-technique approach
2. The single-molecule TIRF imaging method is innovative and addresses real limitations of bulk assays
3. The domain deletion experiments provide mechanistic insight into the roles of MR, PB1, and DBD domains
4. The measurement of native nuclear concentration (7 ± 2 nM) grounds the study in physiological relevance
5. The distinction between nanoclusters and condensates is clearly articulated and experimentally supported

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that nanoclusters exhibit "high-affinity, switch-like, and sequence-specific" DNA binding at physiological concentrations (1-10 nM)
- **Evidence point** Figure 4D, single-molecule imaging data
- **Concern** The switch-like binding transition is described as "only 2 nM wide," but the quantitative analysis supporting this claim is not fully described. The authors report DNA coverage (ϕ) as a function of protein concentration, but the number of independent experiments, error bars, and statistical analysis are not provided in the main text. Furthermore, the claim of "high-affinity" binding is not supported by a quantitative Kd measurement. The authors state that binding is observed at 1 nM, but this does not constitute a rigorous affinity determination. A more detailed binding isotherm with proper error analysis and replicates is needed to support the switch-like and high-affinity claims.
- **Why it matters** The central thesis of the manuscript rests on the quantitative nature of nanocluster-DNA binding. Without rigorous binding curves and statistical analysis, the switch-like and high-affinity claims cannot be evaluated. This is the core evidence for the proposed third scenario of TF-DNA interaction.
- **Resolution test** Provide full binding isotherms with multiple replicates, error bars, and fitted parameters. Report a quantitative apparent Kd for nanocluster binding to specific versus nonspecific DNA. Include statistical comparison between specific and nonspecific binding curves.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that nanoclusters are "a thermodynamic state distinct from phase-separated condensates" and that they exhibit "a size-limiting mechanism similar to micelles"
- **Evidence point** Figure 2E-F, Figure S3-S9, centrifugation assays, DLS data
- **Concern** The distinction between nanoclusters and condensates relies on the centrifugation assay showing c_sat ≈ 28 nM and the observation that nanoclusters remain in the supernatant below this concentration. However, the molecular composition and structure of the nanoclusters are not characterized. The claim of a micellar structure is inferred from domain deletion experiments and AlphaFold predictions, but no direct structural evidence (e.g., cryo-EM, SAXS, or super-resolution microscopy) is provided. The size distribution of nanoclusters (∼150 nm by DLS) seems large for a micelle-like structure containing "tens to hundreds" of proteins. The relationship between the observed nanoclusters and the condensates formed above c_sat is not mechanistically explained.
- **Why it matters** The proposed micellar model is a key conceptual contribution of the paper. If the structural basis of nanocluster formation is not established, the mechanistic claims are speculative. The distinction between nanoclusters and condensates is central to the paper's novelty.
- **Resolution test** Provide direct structural characterization of nanoclusters (e.g., cryo-EM, negative stain EM, or SAXS). Quantify the number of proteins per nanocluster. Demonstrate that the size-limiting mechanism is indeed due to DBD-mediated growth arrest, for example by showing that DBD deletion leads to uncontrolled growth.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "at physiological concentrations, MpARF2 monomers and dimers may not bind DNA, and condensates do not exist, but that micelle-like nanoclusters are the relevant regulatory entity"
- **Evidence point** Figure 1D, Figure 3D, Figure 4D-E
- **Concern** The physiological relevance of the nanocluster model is based on the measurement of 7 ± 2 nM nuclear MpARF2 concentration in gemmae. However, this measurement is from a single cell type (rhizoid precursor cells) at a single developmental stage. The authors acknowledge that expression levels vary across tissues and developmental stages, but the implications of this variability for the nanocluster model are not discussed. If MpARF2 concentrations exceed c_sat (28 nM) in some cell types, condensates would form, potentially with different functional consequences. The claim that nanoclusters are "the relevant regulatory entity" may be an overgeneralization.
- **Why it matters** The physiological relevance of the findings is a key selling point of the paper. If the concentration range where nanoclusters are the dominant species is narrow or cell-type-specific, the broader significance of the model is diminished.
- **Resolution test** Measure MpARF2 concentrations in multiple cell types and developmental stages. Discuss the range of concentrations where nanoclusters would be the dominant species and where condensates would form. Address how the model accommodates cell-type-specific variability.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "nanoclusters, that feature a size-limiting mechanism similar to micelles, turn the gradual and low-affinity binding of monomeric ARFs into a high-affinity switch-like binding transition"
- **Evidence point** Figure 3B, Figure 3D, Figure S10-S13
- **Concern** The EMSA experiments comparing MpARF2-DBD and full-length MpARF2 on short (19 bp) and long (1500 bp) DNA templates are central to the claim that clustering enhances affinity. However, the EMSA analysis appears to include fluorescence from wells, which the authors acknowledge may contain clustered material. The authors state that "fluorescence signals coming from the wells, representing a clustered bound fraction, were included in the analysis," but the rationale for including this signal and its potential to bias the results is not fully explained. Additionally, the effective Kd values are reported as "effective" but the fitting procedure and error estimates are not described in the main text.
- **Why it matters** The comparison between DBD-only and full-length protein binding is used to demonstrate the effect of clustering on affinity. If the EMSA analysis is biased or the Kd values are not rigorously determined, the conclusion that clustering enhances affinity is weakened.
- **Resolution test** Provide a detailed description of the EMSA quantification, including how well fluorescence was integrated and why this is appropriate. Report fitted Kd values with confidence intervals. Consider alternative assays (e.g., fluorescence anisotropy or surface plasmon resonance) to corroborate the affinity enhancement.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence point** Abstract, Teaser
- **Issue** The abstract states that nanoclusters "combine DNA-binding features that cannot be accessed by the other two scenarios," but the specific features are not enumerated. The teaser mentions a "trade-off" but does not define it clearly.
- **Required correction** Briefly specify the features (e.g., high affinity, switch-like, sequence-specific) in the abstract and clarify the trade-off in the teaser.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, single-molecule imaging
- **Evidence point** Methods section, "Single-molecule imaging"
- **Issue** The methods describe the imaging setup and data analysis but do not specify the number of independent biological replicates or the criteria for selecting fields of view. The statement "Fields of view (FOVs) were manually marked" suggests potential selection bias.
- **Required correction** Specify the number of independent experiments and FOVs analyzed. Describe any blinding or randomization procedures. Provide criteria for FOV selection.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, speculation on regulation
- **Evidence point** Discussion, final paragraph
- **Issue** The speculation about PB1-mediated regulation by Aux/IAA competition is interesting but is presented without experimental support. The authors acknowledge this is speculative, but the discussion could be more clearly framed as a hypothesis.
- **Required correction** Clearly label this section as speculative and suggest specific experiments that could test the hypothesis.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Supplementary information
- **Evidence point** Figures S1-S16, Tables S1-S4, Movies S1-S3
- **Issue** The supplementary figures and tables are referenced throughout but were not provided for review. This limits the ability to assess the full evidence base.
- **Required correction** Ensure all supplementary materials are available for review and clearly referenced in the main text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, DLS
- **Evidence point** Methods, "Dynamic Light Scattering"
- **Issue** The DLS data are presented as intensity-weighted size distributions, which the authors acknowledge are biased toward larger objects. The estimated number ratio of 10^8:1 between monomers and nanoclusters is based on this biased data and should be treated with caution.
- **Required correction** Provide number-weighted distributions where possible, or clearly state the limitations of the intensity-weighted data for estimating number ratios.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Discussion
- **Evidence point** Discussion, final paragraph
- **Issue** The authors suggest that nanoclustering may be a "conserved and universal mechanism" for DNA- and RNA-binding proteins, citing references 62-67. However, the evidence for this claim is not discussed in detail.
- **Required correction** Briefly summarize the evidence from the cited references and discuss any limitations or alternative interpretations.

### Technical failings that need to be addressed before the case is established
1. Quantitative binding analysis (R1-M1): The switch-like binding transition and high-affinity claims require rigorous statistical analysis and fitted parameters
2. Structural characterization of nanoclusters (R1-M2): The micellar model needs direct structural evidence
3. Physiological relevance across cell types (R1-M3): The concentration measurements are from a single cell type and may not represent the full range of physiological conditions
4. EMSA quantification (R1-M4): The inclusion of well fluorescence and the fitting procedure need clarification

### Assessment against Nature-style criteria
- **Originality** High. The concept of nanoclustering as a distinct mechanism for TF-DNA binding, separate from both monomeric binding and LLPS condensates, is novel and challenges the current dichotomy in the field.
- **Scientific importance** Moderate to high. If the findings are robust, they could change how researchers think about TF function and regulation. However, the generalizability to other TFs and the physiological relevance across cell types need to be established.
- **Interdisciplinary readership** Moderate. The work bridges plant biology, biophysics, and physical chemistry. The single-molecule imaging approach and the micellar model may appeal to biophysicists, while the auxin signaling context will attract plant biologists.
- **Technical soundness** Currently insufficient. The core claims of high-affinity, switch-like binding and micellar structure are not fully supported by the presented quantitative analysis. The missing supplementary materials further limit assessment.
- **Readability for nonspecialists** Good. The manuscript is generally well-written and the concepts are explained clearly. The figures appear well-designed, though the supplementary figures were not available for review.

### Recommendation posture
Supportive if technical concerns are resolved. The central hypothesis is interesting and the experimental approach is innovative, but the quantitative support for the key claims needs to be strengthened. The authors should provide more rigorous binding analysis, structural characterization of nanoclusters, and a more thorough discussion of physiological relevance across cell types. The manuscript has the potential to be a significant contribution to the field, but the current evidence does not fully establish the case.

## Risk / unsupported claims
1. The claim that nanoclusters are "the relevant regulatory entity" for MpARF2 function is not fully supported, as the concentration range where nanoclusters dominate may be cell-type-specific
2. The claim of a "size-limiting mechanism similar to micelles" is inferred but not directly demonstrated
3. The speculation about Aux/IAA-mediated regulation of nanocluster formation through PB1 competition is presented without experimental support
4. The claim that nanoclustering is a "conserved and universal mechanism" for DNA- and RNA-binding proteins is not substantiated by the data presented
5. The quantitative values for binding affinity and switch-like behavior are not rigorously established from the provided evidence