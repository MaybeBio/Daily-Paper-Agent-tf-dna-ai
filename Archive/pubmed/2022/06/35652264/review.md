## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, experimental section, and supplementary figure/table legends as referenced.
- **Assessment boundary** Scientific validity, technical soundness, and support for claims based solely on the provided manuscript text. No external data, replication, or verification of raw data was performed.
- **Shared manuscript claim summary** The authors report the identification of a novel organic selenium compound, CU27, from a focused library of 365 compounds, which inhibits liver cancer stem cells (CSCs) in vitro and in vivo. They propose a mechanism involving direct binding to the c-Myc bHLH/LZ domain, inhibition of c-Myc-Max complex formation, and reduced occupancy of c-Myc on target gene promoters, leading to suppressed CSC self-renewal, metastasis, and sorafenib resistance.
- **Visible evidence base** Figures 1–8 (as described in text), Supplementary Figures S1–S13, Supplementary Tables S1–S6, and the Experimental Section.
- **Missing materials affecting confidence** Raw microarray data (GEO accession provided but not accessed), full uncropped Western blot images, detailed gating strategies for flow cytometry, statistical details for in vivo experiments (e.g., number of mice per group for survival analysis), and validation data for the specificity of CU27 binding to c-Myc versus other bHLH/LZ proteins.

## Reviewer
- **Overall assessment** The manuscript presents a potentially interesting compound and a plausible mechanism of action. The screening strategy is logical, and the combination of in vitro and in vivo data is commendable. However, several technical concerns, particularly regarding the direct binding mechanism, the specificity of CU27 for c-Myc, and the interpretation of some in vivo results, need to be addressed to fully support the central claims. The claim that CU27 is a "new" compound and the first selenium-based CSC inhibitor is not fully substantiated by a novelty search within the manuscript.
- **Who would be interested in the results, and why** Researchers in the fields of cancer stem cell biology, drug discovery, medicinal chemistry (specifically organoselenium compounds), and liver cancer therapeutics. The potential to overcome sorafenib resistance is of high clinical relevance.
- **Major strengths**
    1.  The step-by-step functional screening strategy is well-designed and logical, moving from 2D viability to 3D spheroid and CSC population analysis.
    2.  The study combines a wide range of techniques (microarray, GSEA, molecular docking, SPR, IP, ChIP, in vivo models) to investigate the mechanism of action.
    3.  The in vivo data demonstrating synergy with sorafenib and reduced metastasis are clinically significant and potentially impactful.
    4.  The identification of a novel small molecule that may directly target the c-Myc bHLH/LZ domain is of significant interest, as c-Myc is a well-validated but challenging therapeutic target.
- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness / Evidence for direct binding
    - **Claim pointer** The manuscript claims that CU27 "binds c-Myc bHLH/LZ domains" and that this is the primary mechanism of action.
    - **Evidence pointer** Figure 5A-C, Table S3, Experimental Section (Molecular Docking, SPR)
    - **Concern** The evidence for direct binding is not conclusive. The molecular docking is purely computational and requires experimental validation. The SPR assay uses a truncated c-Myc protein (a.a. 354-437), but the manuscript does not provide a negative control protein (e.g., a different bHLH/LZ domain-containing protein or a mutated c-Myc) to demonstrate binding specificity. The reported KD values (5.62E-4 µM and 1.32E-4 µM) are extremely low (sub-nanomolar) and seem implausible for a small molecule binding to a large, relatively featureless protein surface like that of c-Myc. This raises concerns about the accuracy of the SPR measurements or the calculation method.
    - **Why it matters** The central mechanistic claim of the paper rests on this direct interaction. If the binding is not specific or is an artifact, the entire proposed mechanism is invalidated.
    - **Resolution test** The authors must provide SPR data with a negative control protein and a mutated c-Myc construct to show specific binding. They should also validate the KD values with an orthogonal method, such as isothermal titration calorimetry (ITC). If the KD is truly in the sub-nanomolar range, this needs a more rigorous justification and discussion.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical soundness / Specificity of compound
    - **Claim pointer** The manuscript implies that CU27's effects are specifically mediated by c-Myc inhibition, as it was selected for its CSC-inhibitory properties.
    - **Evidence pointer** Figures 1, 4, 6, and Discussion
    - **Concern** The manuscript does not rule out off-target effects. CU27 is a reactive organic selenium compound, which could have pleiotropic effects on cells, including general redox modulation or non-specific protein modification. The fact that it inhibits c-Myc transcriptional activity does not prove that this is the sole or even primary mechanism for its anti-CSC effects. The comparison with 10058-F4 and 10074-G5 is useful, but these are also known to have off-target effects. A more direct approach, such as overexpressing c-Myc or a c-Myc mutant resistant to CU27 binding, is needed to demonstrate on-target specificity.
    - **Why it matters** If the anti-CSC effects are due to off-target effects, the proposed mechanism is incomplete and the compound's value as a specific c-Myc inhibitor is overstated.
    - **Resolution test** The authors should perform a rescue experiment by overexpressing c-Myc in CU27-treated cells to see if the anti-CSC effects are reversed. Alternatively, they could use a cellular thermal shift assay (CETSA) to demonstrate target engagement in cells.

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Scientific importance / Novelty
    - **Claim pointer** The manuscript claims to have identified a "new" organic selenium compound and implies it is the first of its kind to target CSCs.
    - **Evidence pointer** Abstract, Introduction, Discussion
    - **Concern** The novelty of the compound is not established. The manuscript does not include a search of chemical databases or a discussion of prior art on organoselenium compounds with anti-cancer or anti-CSC activity. The claim that it is the "first time to synthesize a selenium-containing small molecule with CSC inhibition potential" is a strong claim that requires a more thorough literature review to support.
    - **Why it matters** The scientific importance of the work is diminished if the compound is not truly novel or if other selenium compounds have already been shown to have similar effects.
    - **Resolution test** The authors should include a statement on the novelty of CU27, referencing a search of relevant databases (e.g., SciFinder, Reaxys) and discussing the closest prior art.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Technical soundness / In vivo data interpretation
    - **Claim pointer** The manuscript claims that CU27 "significantly sensitizes sorafenib-resistant tumor to sorafenib" and "decreases the primary tumor size and its metastatic capacity in mouse model."
    - **Evidence pointer** Figure 7, Figure S8-S12, Experimental Section (Animal Studies)
    - **Concern** The in vivo data, while promising, are not fully described. The number of mice per group for the survival study (Figure S9) is not stated. The method for quantifying metastatic foci (Figure 7J,K) is not described in detail. The statement that CU27 alone did not reduce primary tumor size (Figure 7A,B) is interesting but not discussed in the context of its anti-metastatic effect. The mechanism by which CU27 reduces metastasis without affecting primary tumor growth needs further clarification.
    - **Why it matters** The clinical potential of CU27 is based on these in vivo results. Incomplete reporting of experimental details makes it difficult to assess the robustness of the findings.
    - **Resolution test** The authors should provide the exact number of mice per group for all in vivo experiments, a detailed description of the metastasis quantification method, and a discussion of the differential effect on primary tumor growth vs. metastasis.

- **Minor Comments**

    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Readability for nonspecialists
    - **Affected element** Abstract and Introduction
    - **Evidence pointer** Abstract, Introduction
    - **Issue** The abstract and introduction are dense and assume significant background knowledge. The significance of targeting c-Myc in CSCs could be explained more clearly for a broader audience.
    - **Required correction** Briefly explain what c-Myc is and why its inhibition in CSCs is a promising therapeutic strategy in the introduction.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Technical soundness / Data presentation
    - **Affected element** Figure 1
    - **Evidence pointer** Figure 1A-F
    - **Issue** The screening criteria for the "relative cell viability-based screening" are not clearly defined. The figure legend mentions a "step-by-step strategy" but the specific cut-off values for each step are not stated in the main text.
    - **Required correction** Clearly state the selection criteria for each step of the screening process in the Results section or figure legend.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Technical soundness / Data presentation
    - **Affected element** Figure 4
    - **Evidence pointer** Figure 4A
    - **Issue** The IPA results are presented as a list of transcription factors, but the criteria for selecting the "top six" are not stated. The figure legend mentions "activation Z-score," but the threshold is not given.
    - **Required correction** State the threshold for the activation Z-score used to select the top transcription factors.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Technical soundness / Data presentation
    - **Affected element** Figure 5
    - **Evidence pointer** Figure 5A, Table S3
    - **Issue** The molecular docking figure is not described in the text. It is unclear what is being shown and how the "binding energy" was calculated.
    - **Required correction** Add a description of the docking results in the text and explain the units and meaning of the binding energy values in the figure legend.

    - **Concern ID** R1-m5
    - **Severity** Minor
    - **Axis** Technical soundness / Data presentation
    - **Affected element** Figure 7
    - **Evidence pointer** Figure 7A-K
    - **Issue** The in vivo data are presented as representative images and summary graphs. The number of biological replicates (mice) for each experiment is not stated in the figure legend.
    - **Required correction** Add the number of mice used in each group to the figure legend.

- **Technical failings that need to be addressed before the case is established**
    - R1-M1: Lack of conclusive evidence for specific, direct binding of CU27 to c-Myc.
    - R1-M2: Lack of evidence ruling out off-target effects for CU27's anti-CSC activity.
    - R1-M3: Unsubstantiated claims of novelty for the compound and its mechanism.
    - R1-M4: Incomplete reporting of in vivo experimental details.

- **Assessment against Nature-style criteria**
    - **Originality:** The concept of targeting c-Myc in CSCs is not new, but the identification of a novel small molecule from a focused library is a standard approach. The claim of a new selenium compound is potentially original, but the novelty is not rigorously established.
    - **Scientific importance:** The potential to overcome sorafenib resistance in HCC is clinically important. However, the significance is tempered by the lack of definitive mechanistic proof and the potential for off-target effects.
    - **Interdisciplinary readership:** The work is primarily of interest to cancer biologists, medicinal chemists, and hepatologists. The broad significance for a general scientific audience is not immediately apparent.
    - **Technical soundness:** The study uses a wide range of techniques, but the interpretation of key experiments (SPR, in vivo) is not fully supported by the data presented. The lack of a negative control in the SPR experiment is a significant technical flaw.
    - **Readability for nonspecialists:** The manuscript is written for a specialist audience and is not easily accessible to nonspecialists. The abstract and introduction are dense and assume significant background knowledge.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a potentially interesting compound and a plausible mechanism, but the central claims of direct binding and on-target specificity are not yet established from the provided evidence. The authors must address the major concerns, particularly R1-M1 and R1-M2, with additional experiments and a more rigorous presentation of their data.

## Risk / unsupported claims
- The claim that CU27 directly binds to the c-Myc bHLH/LZ domain is unsupported due to the lack of a negative control in the SPR experiment and the implausibly low KD values.
- The claim that CU27's anti-CSC effects are specifically mediated by c-Myc inhibition is unsupported due to the lack of experiments ruling out off-target effects.
- The claim that CU27 is the "first time to synthesize a selenium-containing small molecule with CSC inhibition potential" is unsupported without a thorough novelty search.
- The claim that CU27 "significantly sensitizes sorafenib-resistant tumor to sorafenib" is not fully supported due to incomplete reporting of the in vivo experimental design and statistical analysis.