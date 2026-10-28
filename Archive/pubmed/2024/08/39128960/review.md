## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims presented in the abstract, including identification of a ZAD domain in Drosophila protein Z4, demonstration of dimerization by biochemical methods, and structural modeling by AlphaFold2 with validation by SAXS
- **Shared manuscript claim summary** The authors report that the Drosophila transcription factor Z4 contains a ZAD domain at its N terminus, that this domain dimerizes as shown by biochemical assays, and that an AlphaFold2-derived dimer model is consistent with SAXS data and exhibits a typical ZAD fold
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, experimental protocols, raw biochemical data, AlphaFold2 model coordinates, SAXS curves and fitting statistics, and any statistical analyses

## Reviewer
- **Overall assessment** The abstract presents a focused and plausible finding that Z4 contains a ZAD domain capable of dimerization, with structural support from AlphaFold2 and SAXS. However, the evidence base is limited to the abstract, and several key technical details are absent. The claim of dimerization is central and appears supported in principle, but the strength of the SAXS validation and the biochemical demonstration cannot be fully assessed from the supplied material. The work is likely of interest to specialists in Drosophila chromatin biology and ZAD domain structure, but its broader significance is modest and incremental.
- **Who would be interested in the results, and why** Researchers studying Drosophila chromatin organization, particularly those focused on boundary elements and insulator proteins, would find the identification of a ZAD domain in Z4 relevant. Structural biologists interested in ZAD domain dimerization and the application of AlphaFold2 with SAXS validation may also take note. The results could inform models of Z4 function in chromatin domain boundaries, but the audience is likely limited to these specialized communities.
- **Major strengths** The study addresses a specific and testable question about Z4 domain architecture. The combination of biochemical dimerization assays with AlphaFold2 prediction and SAXS validation is a reasonable and modern approach. The finding that Z4 contains a ZAD domain is consistent with its known protein interaction partners and could have functional implications.
- **Major Concerns** 
  - R1-M1
  - R1-M2
- **Minor Comments** 
  - R1-m1
  - R1-m2
- **Technical failings that need to be addressed before the case is established** The abstract does not provide quantitative details on the biochemical dimerization assay, such as affinity measurements or controls. The SAXS validation is mentioned but without any fit parameters, resolution, or comparison to the AlphaFold2 model. These omissions prevent full verification of the central claims.
- **Assessment against Nature-style criteria** Originality is moderate; the identification of a ZAD domain in Z4 is novel but incremental given the known family of ZAD-containing proteins. Scientific importance is limited to a specialized audience and does not suggest a broad conceptual advance. Interdisciplinary readership is low, as the topic is niche. Technical soundness cannot be fully evaluated from the abstract alone, but the described methods are appropriate. Readability for nonspecialists is adequate, though the abstract assumes familiarity with Drosophila chromatin biology and ZAD domains.
- **Recommendation posture** Supportive if technical concerns are resolved, but currently not established from the provided evidence due to missing quantitative and structural validation details.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract states that "the capability of dimerization was confirmed for the domain by biochemical methods" and that "the model structure was confirmed using small-angle X-ray scattering (SAXS)."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract provides no experimental details for the biochemical dimerization assay, such as the method used (e.g., size-exclusion chromatography, crosslinking, or analytical ultracentrifugation), the protein construct boundaries, or any quantitative results. Similarly, the SAXS validation is stated without reporting key parameters such as the radius of gyration, maximum particle dimension, goodness-of-fit (e.g., chi-squared) between the SAXS profile and the AlphaFold2 model, or the resolution of the SAXS data.
- **Why it matters** The central claims of the study rest on the demonstration of dimerization and the structural validation. Without these details, a reader cannot assess whether the dimerization is robust or whether the SAXS data genuinely support the AlphaFold2 model over alternative conformations or monomeric states.
- **Resolution test** Provide the full methods and results for the biochemical assay, including a representative dataset and controls, and report SAXS-derived parameters and fitting statistics that quantitatively compare the experimental scattering profile to the AlphaFold2 dimer model.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract claims that "a zinc finger-associated domain (ZAD) domain was identified in Z4" and that "the dimer structure shows a fold typical of ZAD domains."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract does not specify how the ZAD domain was identified, such as by sequence homology, domain prediction tools, or structural comparison. The statement that the dimer structure shows a typical ZAD fold is based on the AlphaFold2 model, but the abstract does not indicate the confidence of the prediction (e.g., pLDDT scores) or whether the SAXS data independently support the fold assignment or merely the overall shape.
- **Why it matters** The identification of the domain and the fold assignment are foundational to the study. If the ZAD domain identification is based solely on sequence prediction without experimental validation, or if the AlphaFold2 model has low confidence in key regions, the structural conclusions could be overstated.
- **Resolution test** Describe the bioinformatic or experimental approach used to identify the ZAD domain, report AlphaFold2 confidence metrics, and clarify whether the SAXS data can distinguish the proposed ZAD fold from other possible dimeric arrangements.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Domain nomenclature
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract uses "ZAD" without defining the full term or explaining its relevance to Z4 function, which may confuse readers unfamiliar with the domain family.
- **Required correction** Define "zinc finger-associated domain" at first use and briefly state its known functional role in dimerization or chromatin binding.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Functional implications
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract does not discuss how the ZAD domain dimerization relates to Z4's known interactions with Chromator and BEAF-32 or its role at chromatin domain boundaries.
- **Required correction** Add a sentence in the abstract or discussion connecting the dimerization finding to the protein's known functions, to enhance the biological relevance of the structural result.

## Risk / unsupported claims
- The claim that dimerization was "confirmed" by biochemical methods is unsupported without quantitative data or assay details.
- The claim that the SAXS data "confirmed" the AlphaFold2 model is unsupported without reporting fitting statistics or model comparison.
- The identification of the ZAD domain is not verifiable from the abstract alone, as no sequence or prediction method is described.
- The statement that the dimer structure shows a "fold typical of ZAD domains" is not independently verifiable without structural coordinates or comparison data.