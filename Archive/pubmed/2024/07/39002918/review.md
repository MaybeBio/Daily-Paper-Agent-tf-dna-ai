## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no access to methods, figures, or supplementary data
- **Shared manuscript claim summary** The authors propose that the STAG2-RAD21 complex acts as a unidirectional DNA ratchet during loop extrusion, based on computational simulations showing that STAG2's V-shape permits DNA sliding in one direction but blocks the opposite direction, and that RAD21 binding narrows the STAG2 V-shape opening to control flexibility.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or numerical results provided
- **Missing materials affecting confidence** Full methods, simulation parameters, force fields, structural models, validation data, quantitative results, and any comparison with experimental data

## Reviewer
- **Overall assessment** The abstract presents an interesting and potentially significant hypothesis regarding the mechanistic role of STAG2-RAD21 in loop extrusion. However, the evidence base is limited to a summary of computational findings without any quantitative detail or methodological transparency. The central claims of unidirectional ratcheting and RAD21-dependent conformational control cannot be adequately evaluated from the supplied material. The work may be of interest to the chromatin biology and structural biology communities, but the current abstract does not establish the case with sufficient rigor.
- **Who would be interested in the results, and why** Researchers studying chromatin architecture, loop extrusion mechanisms, cohesin complex function, and the molecular basis of chromatin-related diseases such as Cornelia de Lange syndrome and cancers with STAG2 mutations. The proposed ratchet mechanism could inform both basic mechanistic understanding and therapeutic targeting strategies.
- **Major strengths** The hypothesis is mechanistically plausible and addresses a key open question in the field. The proposed dual role of STAG2 as both anchor and ratchet component is conceptually novel. The abstract clearly states the proposed mechanism and its potential implications.
- **Major Concerns** The abstract lacks any quantitative results, simulation details, or validation against experimental data. The claim that STAG2 enforces unidirectional DNA motion is presented without supporting metrics such as free energy profiles, force measurements, or statistical significance. The claim that RAD21 binding narrows the V-shape opening is not supported by any structural or dynamic data in the abstract. The relationship between the computational model and biological reality is not established.
- **Minor Comments** The abstract would benefit from specifying the simulation method used. The phrase "linear ratchet mechanism" is not defined. The abstract does not state whether the simulations were validated against known experimental structures or dynamics.
- **Technical failings that need to be addressed before the case is established** No quantitative evidence is provided for the directional selectivity claim. No evidence is provided for the RAD21-induced conformational change. No validation of the computational model against experimental data is described.
- **Assessment against Nature-style criteria** Originality: The proposed ratchet mechanism for STAG2 is novel and could be of high interest. Scientific importance: If established, the findings would significantly advance understanding of loop extrusion and cohesin function. Interdisciplinary readership: The topic bridges structural biology, biophysics, and chromatin biology, with potential appeal across these fields. Technical soundness: Cannot be assessed from the abstract alone; no methods or quantitative results are provided. Readability for nonspecialists: The abstract is generally clear but uses specialized terminology without sufficient context for a broad audience.

## Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "The results reveal that STAG2 V-shape allows DNA sliding in one direction, but blocks opposite DNA movement via a linear ratchet mechanism."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The central claim of unidirectional DNA sliding is presented without any quantitative data. No free energy values, force measurements, or statistical analyses are reported. The abstract does not describe how directionality was measured or what threshold defined "blocking."
- **Why it matters** Directional selectivity is the core mechanistic claim. Without quantitative evidence, the claim cannot be distinguished from a qualitative observation or an artifact of the simulation setup.
- **Resolution test** Provide quantitative metrics such as free energy profiles along the DNA sliding coordinate, force-displacement curves, or statistical comparison of forward versus reverse translocation probabilities, with appropriate error estimates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "RAD21 binding to STAG2 controls its flexibility by narrowing the opening of its V-shape, which otherwise remains widely open in absence of RAD21."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The claim that RAD21 binding narrows the STAG2 V-shape opening is stated without any supporting data. No structural ensembles, root-mean-square deviation values, or conformational sampling results are provided.
- **Why it matters** This conformational control is proposed as the mechanism by which RAD21 modulates ratchet function. Without evidence, the link between RAD21 binding and directional selectivity is speculative.
- **Resolution test** Provide quantitative comparison of STAG2 V-shape opening angles or conformational distributions in the presence and absence of RAD21, with statistical significance and simulation convergence checks.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation
- **Claim pointer** "a computational simulation framework was constructed to evaluate whether STAG2 could enforce such unidirectional displacement of a DNA double helix"
- **Evidence pointer** Abstract only; location not provided
- **Concern** No information is provided about the simulation method, force field, system setup, or timescales. The abstract does not state whether the model was validated against experimental structures or known biochemical data on STAG2-DNA interactions.
- **Why it matters** Computational predictions of molecular mechanisms are only credible if the model is appropriately constructed and validated. Without this information, the results could be artifacts of the chosen parameters or initial conditions.
- **Resolution test** Describe the simulation methodology in detail, including force field parameters, system size, simulation length, and any validation against experimental structures or binding data. Provide convergence and robustness analyses.

## Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract; location not provided
- **Issue** The term "linear ratchet mechanism" is introduced without definition or context.
- **Required correction** Define what is meant by "linear ratchet" and how it differs from other ratchet mechanisms in the loop extrusion literature.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods description
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not specify the type of computational simulation used, such as molecular dynamics, Brownian dynamics, or coarse-grained modeling.
- **Required correction** State the simulation method explicitly in the abstract or provide a clear reference to the methods section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Context
- **Affected element** Related work
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not discuss how the proposed mechanism relates to or differs from existing ratchet models of loop extrusion.
- **Required correction** Add a brief statement situating the proposed mechanism within the existing literature on loop extrusion ratchets.

## Risk / unsupported claims
- The claim of unidirectional DNA sliding by STAG2 is unsupported by quantitative evidence in the abstract.
- The claim that RAD21 binding narrows the STAG2 V-shape opening is unsupported by any data in the abstract.
- The biological relevance of the proposed mechanism to loop extrusion in vivo is not established from the computational results alone.
- The relationship between the proposed ratchet mechanism and chromatin-related diseases is stated as an implication but is not substantiated.