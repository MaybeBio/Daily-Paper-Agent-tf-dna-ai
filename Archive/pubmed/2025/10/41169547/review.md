## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific content, methodological soundness, claim-evidence alignment, and presentation quality of the reported computational study
- **Shared manuscript claim summary** The authors use coarse-grained molecular dynamics simulations to show that repulsive (steric) and attractive (interaction-based) crowding agents distinctly regulate TDP-43 CTD phase separation, with repulsive crowders promoting condensation via entropic exclusion and attractive crowders suppressing it via competitive enthalpic interactions, while revealing region-specific internal architecture and dynamics characterized by strong but short-lived helix-helix contacts and weaker but persistent IDR-IDR contacts
- **Visible evidence base** Main text figures (Figures 1-4 referenced), supplementary figures (S1-S24), methods descriptions, and simulation parameter tables (S1, S2)
- **Missing materials affecting confidence** Actual figure images and data values not visible; supplementary figures S1-S24 not provided; simulation parameter tables S1 and S2 not provided; no experimental validation data

## Reviewer
- **Overall assessment** This manuscript presents a systematic computational investigation of how crowding agent chemistry modulates TDP-43 CTD phase separation. The study is well-designed, with clear contrasts between repulsive and attractive crowding regimes, and the region-specific analysis of internal condensate architecture is a valuable contribution. The central claims are largely supported by the described simulation results, though several important limitations and unaddressed questions temper the overall impact. The work is technically sound within the chosen coarse-grained framework, but the biological relevance claims require more careful qualification given the simplified model system.

- **Who would be interested in the results, and why** Researchers studying biomolecular phase separation, particularly those focused on TDP-43 biology and neurodegeneration, will find this work relevant. The distinction between entropic and enthalpic crowding effects on condensate properties is of broad interest to the phase separation community. Computational biophysicists developing and applying coarse-grained models to IDP condensation will also be interested. The region-specific structure-dynamics decoupling concept may inform experimental design for validating condensate internal architecture predictions.

- **Major strengths** The systematic comparison of repulsive versus attractive crowding is a clear and well-motivated design. The multi-scale analysis from single-chain to dimer to condensate provides a coherent picture. The region-specific orientation and dynamics analysis is novel and provides testable predictions. The authors appropriately acknowledge model limitations and discuss connections to experimental literature.

- **Major Concerns** The following concerns are detailed below.

- **Minor Comments** The following minor comments are detailed below.

- **Technical failings that need to be addressed before the case is established** R1-M1 (experimental validation), R1-M2 (rigid helix approximation), R1-M3 (crowder model realism)

- **Assessment against Nature-style criteria** 
  - **Originality**: Moderate. The distinction between repulsive and attractive crowding effects on phase separation is not entirely new, but the region-specific structural dynamics analysis within condensates under different crowding regimes offers a fresh perspective.
  - **Scientific importance**: Moderate. The findings advance understanding of how crowding chemistry modulates condensate properties, which is relevant to interpreting in vitro and in vivo phase separation data. However, the biological implications remain speculative given the simplified model.
  - **Interdisciplinary readership**: Moderate. The work bridges biophysics, computational chemistry, and cell biology, but the technical nature of the methods may limit accessibility to a broad readership.
  - **Technical soundness**: Generally sound within the coarse-grained framework, but several approximations (rigid helix, static crowders, no crowder-crowder attractions) limit the robustness of conclusions.
  - **Readability for nonspecialists**: The manuscript is clearly written but assumes familiarity with phase separation concepts and coarse-grained simulation methodology. Some sections, particularly the methods, are dense.

- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding experimental validation of key predictions and justification of model approximations.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The authors claim that "repulsive crowders promote condensation via excluded-volume entropic stabilization, whereas attractive crowders modulate assembly through competitive enthalpic interactions" and that these effects are "physiologically relevant."
- **Evidence pointer** Abstract; Discussion section; location not provided
- **Concern** The manuscript presents purely computational results with no experimental validation of the central predictions. While the authors discuss connections to experimental literature (e.g., Conicella et al. on helix mutations), no direct experimental test of the crowding-dependent region-specific reorganization is provided. The claim of physiological relevance is therefore not directly supported.
- **Why it matters** The biological significance of the findings depends on whether the predicted crowding-dependent reorganization of TDP-43 condensates is experimentally observable. Without validation, the physiological relevance claims remain speculative.
- **Resolution test** Provide experimental validation of at least one key prediction, such as fluorescence recovery after photobleaching (FRAP) measurements of TDP-43 condensates in the presence of repulsive versus attractive crowding agents, or structural analysis confirming helix enrichment in condensate cores under different crowding conditions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model approximation
- **Claim pointer** The authors state that "the conserved TDP-43 CTD helix is modeled as a rigid segment with native helicity" and use this to draw conclusions about helix-helix contact dynamics.
- **Evidence pointer** Materials and Methods, CG MD Simulations section; Discussion section; location not provided
- **Concern** The rigid-helix approximation is a significant simplification that may bias the results. Real helices in TDP-43 CTD can partially unfold, and this conformational flexibility could affect contact dynamics and crowding responses. The authors acknowledge this limitation but do not test its impact on their conclusions.
- **Why it matters** If helix flexibility is important for the observed crowding-dependent reorganization, the rigid-helix model may produce qualitatively incorrect predictions about helix-helix contact lifetimes and spatial distributions.
- **Resolution test** Perform additional simulations with a flexible helix model (e.g., using a more detailed CG representation or all-atom simulations for selected conditions) to test whether the key conclusions about helix-helix contact dynamics and spatial organization are robust to this approximation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Crowder model realism
- **Claim pointer** The authors model crowding agents as "CG beads, each assigned a mass of 1500 amu and a radius of r c = 0.8 nm, mimicking the mass and effective size of PEG1500 analogs."
- **Evidence pointer** Materials and Methods, Crowding Interactions section; location not provided
- **Concern** The crowder model is highly simplified, representing all crowders as identical spherical beads with either purely repulsive or attractive interactions. Real cellular crowding involves a heterogeneous mixture of macromolecules with diverse sizes, shapes, and interaction specificities. The authors acknowledge this but do not test whether their conclusions are robust to crowder size, shape, or polydispersity.
- **Why it matters** The distinction between repulsive and attractive crowding effects may depend on crowder size relative to the protein, and the conclusions may not generalize to realistic cellular crowding conditions.
- **Resolution test** Perform additional simulations with different crowder sizes (e.g., smaller and larger than the current 0.8 nm radius) and with polydisperse crowder mixtures to test whether the qualitative conclusions about repulsive versus attractive crowding effects are robust.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** Main text figures
- **Evidence pointer** Figures 1-4; location not provided
- **Issue** The figure images are not visible in the provided manuscript text, making it difficult to fully assess the quantitative support for the claims. The figure captions are referenced but not shown.
- **Required correction** Ensure all figures are included in the manuscript submission and that they clearly display the data supporting the key claims, including error bars or statistical significance where appropriate.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Parameter justification
- **Affected element** Simulation parameters
- **Evidence pointer** Tables S1 and S2; location not provided
- **Issue** The simulation parameters are referenced to supplementary tables that are not provided. Key parameters such as the exact interaction strengths for attractive crowders, the number of independent simulations, and the equilibration criteria are not visible.
- **Required correction** Include the supplementary tables in the submission and provide a brief justification for key parameter choices in the main text or methods.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical analysis
- **Affected element** Quantitative comparisons
- **Evidence pointer** Figures 1-4; location not provided
- **Issue** The manuscript reports trends in quantities such as density, contact numbers, and diffusion coefficients, but it is unclear whether these are based on single simulations or multiple independent replicates with associated uncertainties.
- **Required correction** Report the number of independent simulations performed and provide error estimates or confidence intervals for key quantitative results.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology clarity
- **Affected element** "Structure-dynamics decoupling"
- **Evidence pointer** Title; Abstract; Results section; location not provided
- **Issue** The term "structure-dynamics decoupling" is used to describe the observation that helix-helix contacts are strong but short-lived while IDR-IDR contacts are weaker but longer-lived. This terminology may be confusing, as "decoupling" typically implies independence, whereas the authors describe complementary roles.
- **Required correction** Consider using a more precise term such as "differential structure-dynamics relationships" or "domain-specific dynamic partitioning" to avoid potential misinterpretation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Generalizability
- **Affected element** Discussion of broader applicability
- **Evidence pointer** Discussion section; location not provided
- **Issue** The authors claim the principles uncovered "have broad applicability to diverse phase-separating proteins," but the study focuses exclusively on TDP-43 CTD. The generalizability of the findings to other IDPs with different sequence features is not tested.
- **Required correction** Either temper the generalizability claim or provide a brief discussion of how the findings might apply to other systems based on sequence features.

## Risk / unsupported claims
- The claim that repulsive and attractive crowding effects are "physiologically relevant" is not directly supported by experimental evidence.
- The claim that helix-helix contacts are "strong but short-lived" while IDR-IDR contacts are "weaker but more persistent" is based on the specific CG model and rigid-helix approximation, and may not hold for the real protein.
- The prediction that "RNA as a multivalent coscaffold with biphasic control" and "ATP as a hydrotrope" modulate TDP-43 condensates in the manner described is speculative and not tested in this study.
- The generalizability claim to "diverse phase-separating proteins" is not supported by evidence from other systems.
- The quantitative values of contact lifetimes (τ) are stated to be within the "order-of-magnitude range observed for microscopic contact lifetimes in dense phases," but the comparison to experimental data is indirect and the exact values are not provided in the visible text.