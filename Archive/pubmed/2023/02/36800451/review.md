## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no figures, tables, methods, or supplementary material provided
- **Shared manuscript claim summary** The authors propose a systematic coarse-graining scheme based on the rigid base-pair model, combined with all-atom molecular dynamics simulations, to connect microscopic DNA mechanical parameters to the persistence length. They claim to identify relevant couplings between degrees of freedom at each coarse-graining step and to clarify the scale dependence of elastic moduli, including previously unnoticed off-site couplings between deformations of different parity.
- **Visible evidence base** Abstract text only; no quantitative results, simulation details, or methodological derivations are available
- **Missing materials affecting confidence** Full manuscript, all figures, tables, methods section, simulation protocols, parameter values, and any quantitative comparisons with experimental data

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting approach to bridging base-pair scale mechanics and mesoscopic persistence length in double-stranded DNA. The idea of systematically tracking couplings between deformation modes across coarse-graining steps, particularly parity-related off-site couplings, is potentially novel and could be of interest to the biophysics community. However, the abstract alone provides insufficient quantitative detail to evaluate the validity, robustness, or significance of the claims. The connection between the proposed scheme and the persistence length is stated but not demonstrated, and the role of the identified couplings is asserted without supporting evidence. The manuscript may have merit, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in computational biophysics, DNA mechanics, and polymer physics would be interested. Those studying DNA-protein interactions, nucleosome positioning, and chromatin organization would also find the connection between local mechanical properties and mesoscopic behavior relevant. The methodological aspect of systematic coarse-graining with parity-resolved couplings could appeal to theorists developing multiscale models of biomolecules.
- **Major strengths** The abstract addresses a genuine gap in connecting base-pair scale mechanics to persistence length. The proposed systematic coarse-graining framework, with attention to previously unnoticed off-site couplings, suggests a potentially fresh perspective. The combination of rigid base-pair modeling with all-atom simulations is a reasonable and modern approach.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** 
  - Originality: The abstract hints at a novel treatment of parity-related off-site couplings in coarse-graining DNA elasticity. This could be original, but the abstract does not provide enough context to distinguish it clearly from prior coarse-graining studies. 
  - Scientific importance: The connection between base-pair scale mechanics and persistence length is important for understanding DNA-protein interactions and nucleosome dynamics. However, the abstract does not demonstrate how the findings change current understanding or resolve existing discrepancies. 
  - Interdisciplinary readership: The topic bridges molecular biophysics, statistical mechanics, and polymer physics. The abstract is written in a way that is accessible to specialists in these fields, but the significance for a broader readership is not articulated. 
  - Technical soundness: Cannot be assessed from the abstract alone. No quantitative results, error estimates, or validation against experimental data are provided. 
  - Readability for nonspecialists: The abstract is concise and uses standard terminology, but the lack of context and quantitative framing limits accessibility for readers outside the immediate field.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible framework, but the core claims require full manuscript evaluation. A supportive posture would require demonstration of quantitative agreement with known persistence length values, validation of the coarse-graining scheme, and evidence that the identified couplings materially affect the predicted persistence length.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that the scheme "connects its microscopic parameters to the persistence length" and "clarifies how the scale dependence of the elastic moduli is determined."
- **Evidence pointer** Abstract only; no quantitative results or comparisons provided
- **Concern** The abstract states that the scheme connects microscopic parameters to the persistence length, but no numerical values, predicted persistence lengths, or comparisons with experimental measurements are presented. The claim that the scale dependence of elastic moduli is clarified is made without showing any derived expressions, scaling laws, or simulation results.
- **Why it matters** The central scientific contribution of the work appears to be this connection. Without quantitative demonstration, the reader cannot assess whether the scheme produces correct predictions, whether the identified couplings are significant in magnitude, or whether the approach improves upon existing models.
- **Resolution test** The full manuscript must provide quantitative predictions for the persistence length of double-stranded DNA under relevant conditions, compared with experimental values and with predictions from existing models. The scale dependence of elastic moduli should be shown explicitly, with clear demonstration of how the parity-related couplings affect the results.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The abstract claims that "our scheme identifies relevant couplings between different degrees of freedom at each coarse-graining step."
- **Evidence pointer** Abstract only; no methodological details provided
- **Concern** The abstract does not describe the coarse-graining procedure, the criteria for identifying "relevant" couplings, the number of coarse-graining steps, or how the rigid base-pair model parameters are obtained from all-atom simulations. The term "systematic way" is used, but the procedure is not outlined.
- **Why it matters** Reproducibility and assessment of the approach require understanding the coarse-graining protocol. Without this, the reader cannot judge whether the identified couplings are an artifact of the procedure or a genuine physical feature. The claim of novelty for the off-site parity couplings cannot be evaluated without knowing how the search for couplings was conducted.
- **Resolution test** The full manuscript must provide a detailed description of the coarse-graining procedure, including the mapping from all-atom trajectories to rigid base-pair parameters, the renormalization or integration steps, the criteria for retaining couplings, and the convergence of the scheme with respect to the number of steps.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim substantiation
- **Claim pointer** The abstract claims that the work clarifies "the role of previously unnoticed off-site couplings between deformations with different parity."
- **Evidence pointer** Abstract only; no demonstration of the role or its significance
- **Concern** The abstract asserts that off-site couplings between deformations of different parity play a role, but does not specify what that role is, how it manifests in the persistence length, or why it was previously unnoticed. No physical interpretation or quantitative impact is given.
- **Why it matters** This appears to be a key novel claim of the work. If the role of these couplings is not demonstrated with clear physical consequences, the claim remains an assertion. The significance for DNA mechanics and for understanding protein-DNA interactions depends on the magnitude and nature of this effect.
- **Resolution test** The full manuscript must show explicitly how the parity-related off-site couplings influence the persistence length, for example by comparing predictions with and without these couplings, and by providing a physical interpretation of the mechanism.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Contextual framing
- **Affected element** Introduction and motivation
- **Evidence pointer** Abstract opening sentences
- **Issue** The abstract states that less is known about the relation between mesoscopic behavior and base-pair scale mechanics, but does not specify what specific gaps or unresolved questions are addressed beyond the general statement.
- **Required correction** The full manuscript should clearly articulate the specific open questions or limitations of existing approaches that motivate this work, to help readers understand the incremental contribution.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology clarity
- **Affected element** Use of "off-site couplings"
- **Evidence pointer** Abstract, last sentence
- **Issue** The term "off-site couplings" is not defined in the abstract. It is unclear whether this refers to couplings between base pairs at different positions along the chain, couplings between different deformation modes at the same site, or something else.
- **Required correction** The full manuscript should define this term precisely in the context of the rigid base-pair model and the coarse-graining procedure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scope of validation
- **Affected element** Claims of applicability
- **Evidence pointer** Abstract, overall
- **Issue** The abstract does not mention any comparison with experimental data or with alternative theoretical models for the persistence length, such as the worm-like chain or other base-pair level models.
- **Required correction** The full manuscript should include validation against experimental persistence length measurements and, where possible, comparisons with predictions from other models to establish the accuracy and added value of the proposed scheme.

## Risk / unsupported claims
- The claim that the scheme "connects its microscopic parameters to the persistence length" is unsupported in the abstract, as no quantitative connection is shown.
- The claim that the scheme "clarifies how the scale dependence of the elastic moduli is determined" is unsupported, as no scale-dependent results are presented.
- The claim regarding "previously unnoticed off-site couplings between deformations with different parity" is unsupported, as no evidence of their existence, magnitude, or role is provided.
- The relevance to "DNA-protein interactions and the nucleosome diffusion mechanism" is stated as motivation but is not substantiated by any results in the abstract.