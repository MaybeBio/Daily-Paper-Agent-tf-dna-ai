## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, materials and methods, results, discussion, and supplementary figure/table legends as referenced.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided manuscript text. No external validation of methods or data was performed.
- **Shared manuscript claim summary** The authors report that targeted engineering of the intrinsically disordered linker (IDL) of *E. coli* SSB can selectively modulate its condensation properties, including propensity, stability, and partner enrichment, without affecting ssDNA or protein partner binding. They further use AlphaFold 3 predictions to propose structural mechanisms linking IDL conformational dynamics to condensation behavior.
- **Visible evidence base** Figures 1–9 (as described in text), Supplementary Tables S1–S4, Supplementary Figures S1–S3, and Supplementary Data Files S1–S2. Specific numerical values and statistical analyses are not fully reported in the provided text.
- **Missing materials affecting confidence** Full figure panels with quantitative data, exact numerical values for Kd, turbidity measurements, statistical analyses, and complete methods for computational predictions. Supplementary figures and tables are referenced but not provided in full.

## Reviewer
- **Overall assessment** This manuscript presents a systematic and thoughtful engineering approach to dissect the role of the IDL in SSB condensation. The work is timely and relevant, given the growing interest in bacterial phase separation. The authors provide a clear rationale, a well-designed panel of mutants, and a combination of experimental and computational approaches. However, several claims regarding the selectivity and mechanism of the engineered effects require stronger quantitative support and clearer presentation of the data. The link between AF3 predictions and experimental observations is suggestive but not fully validated. Overall, the study has potential but needs revision to fully establish its conclusions.

- **Who would be interested in the results, and why** Researchers in the fields of bacterial cell biology, DNA replication and repair, and phase separation. The work provides tools (engineered SSB variants) that could be used to probe the physiological roles of SSB condensation. It also contributes to the understanding of how IDL sequence features govern condensation, which is relevant to the broader IDP/LLPS community.

- **Major strengths**
  1. The study addresses a significant and under-explored question: the specific role of the IDL in SSB condensation, moving beyond simple deletion analysis.
  2. The panel of engineered variants is well-designed, allowing for a systematic dissection of sequence features (glycine-rich regions, aromatic/cationic residues).
  3. The combination of functional assays (binding, condensation, co-condensation, stability) with structural predictions (AF3) provides a multi-faceted view.
  4. The demonstration that condensation can be selectively engineered without affecting other SSB functions is a key and potentially useful finding.
  5. The comparative analysis of LLPS prediction algorithms using the experimental dataset is a valuable contribution to the field.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Data support
- **Claim pointer** The claim that "specific alterations... by which a broad-range, selective modification of condensation propensity and condensate thermal and chemical stability can be achieved, while leaving the single-stranded DNA and partner protein binding functions of SSB unchanged."
- **Evidence pointer** Figures 2, 3, 6, 7; Supplementary Tables S1, S2
- **Concern** The manuscript states that binding functions are "unchanged" but does not provide quantitative comparisons or statistical tests for the binding data (Figure 2). The text describes "WT-like" affinities, but the actual Kd values and errors are not presented in the main text. Similarly, the condensation propensity data (Figure 3) and stability data (Figures 6, 7) are described qualitatively. Without quantitative values and statistical analysis, it is difficult to assess the strength of the claim that the effects are "selective" and "broad-range."
- **Why it matters** The central premise of the paper is the selective engineering of condensation. If the binding data are not rigorously quantified, the claim of selectivity is not fully supported. The reader cannot judge whether the observed differences are significant or within experimental noise.
- **Resolution test** Provide a table with quantitative values (e.g., Kd for ssDNA and RecQ binding, EC50 or threshold for condensation, Tc values) for all variants, with errors and statistical significance (e.g., p-values) compared to WT. Show the full dose-response curves for condensation and inhibition assays.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / Data support
- **Claim pointer** The claim that "AlphaFold 3-predicted structures... identify multiple possible binding sites for the conserved C-terminal tip on the tetramer core of the IDL, establishing a link between condensation propensity and restrictions in IDL conformational dynamics."
- **Evidence pointer** Figure 9; Supplementary Table S3; Supplementary Data Files S1, S2
- **Concern** The AF3 predictions are used to propose a structural mechanism. However, the manuscript does not provide a clear, quantitative analysis of the predicted models. For example, how was the "restriction in IDL conformational dynamics" assessed from the models? The pTM scores are mentioned, but the specific structural features (e.g., contact maps, RMSF, interface areas) that support the claim are not described. The link between the predicted binding modes and the experimental condensation data is largely qualitative and correlative.
- **Why it matters** The structural interpretation is a key part of the paper's narrative. Without a clear and quantitative analysis of the AF3 output, the claim of a mechanistic link is not well-supported. The reader cannot evaluate whether the predictions are robust or whether the interpretation is over-stated.
- **Resolution test** Provide a more detailed analysis of the AF3 models, such as: (1) a comparison of the predicted C-terminal tip binding affinity/interface area across variants, (2) an analysis of IDL conformational ensemble (e.g., radius of gyration, secondary structure propensity) from the models, and (3) a direct comparison of these features with the experimental condensation propensity. If possible, validate key predictions with a biophysical experiment (e.g., limited proteolysis, FRET, or cross-linking).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance / Interdisciplinary readership
- **Claim pointer** The claim that "these results pave the way for the definition of in vivo roles of EcSSB condensation via genetic engineering and delineate ways for further development of liquid–liquid phase separation prediction algorithms."
- **Evidence pointer** Discussion section
- **Concern** While the engineered variants are potentially useful, the manuscript does not demonstrate their utility in vivo. The discussion speculates on future applications but does not provide any data showing that the variants behave as expected in cells or that they can be used to dissect function. The claim about improving prediction algorithms is based on a single comparative analysis, which is a good start but is not a fully developed new algorithm or a comprehensive benchmark.
- **Why it matters** The broader impact of the work depends on the generalizability and utility of the findings. The current manuscript is primarily a biochemical and biophysical characterization. The claims about paving the way for in vivo studies and algorithm development are forward-looking but not yet substantiated by data.
- **Resolution test** Either temper the claims in the discussion to be more clearly speculative, or add a preliminary experiment demonstrating the use of a variant in a cellular context (e.g., complementation of an SSB knockout strain and assessment of fitness or focus formation). For the prediction algorithms, a more extensive benchmark against a larger dataset would strengthen the claim.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 1
- **Issue** The introduction could be slightly more accessible to a general reader. The concept of LLPS and its relevance to bacteria is introduced, but the specific terminology (e.g., "cation-pi interactions") is used without a brief explanation.
- **Required correction** Add a brief explanation of key terms like "cation-pi interactions" and "intrinsically disordered linker" in the introduction to make the paper more accessible to a broader audience.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods
- **Evidence pointer** Materials and Methods, "Computational predictions" section
- **Issue** The methods for the LLPS prediction algorithms are not described. The names of the servers are listed, but the specific parameters and versions are not given.
- **Required correction** Provide a brief description of the prediction methods used, including the version and any relevant parameters, to ensure reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data support
- **Affected element** Results, "IDL-engineered EcSSB constructs retain the capacity for binding ssDNA and RecQ helicase"
- **Evidence pointer** Figure 2
- **Issue** The text states that "the interaction of EcSSB with these ssDNA ligands was unaffected by IDL modifications" but does not show the binding curves or provide a statistical comparison.
- **Required correction** Include the binding curves in the main figure or supplementary, and provide a statistical analysis (e.g., a t-test comparing Kd values) to support the claim of "unaffected."

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data support
- **Affected element** Results, "The stability of condensates..."
- **Evidence pointer** Figure 7
- **Issue** The temperature profiles are described, but the definition of Tc is not explicitly stated in the main text. It is mentioned in the methods, but a brief definition in the results would be helpful.
- **Required correction** Define Tc in the results section when it is first used.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph 2
- **Issue** The discussion of the AF3 predictions is somewhat technical and may be difficult for a non-structural biologist to follow.
- **Required correction** Consider adding a schematic figure or a more accessible explanation of the predicted binding modes and their implications for condensation.

## Risk / unsupported claims
- The claim that the engineered variants leave "single-stranded DNA and partner protein binding functions of SSB unchanged" is not fully supported by the quantitative data presented.
- The claim of a "link between condensation propensity and restrictions in IDL conformational dynamics" is based on qualitative interpretation of AF3 models and is not rigorously established.
- The claim that the results "pave the way for the definition of in vivo roles" is speculative and not supported by any in vivo data in this manuscript.
- The claim that the data "delineate ways for further development of liquid–liquid phase separation prediction algorithms" is based on a limited comparative analysis and is overstated.