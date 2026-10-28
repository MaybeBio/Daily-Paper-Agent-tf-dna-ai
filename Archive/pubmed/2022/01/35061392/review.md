## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract; no methods, figures, tables, or supplementary material were provided for evaluation
- **Shared manuscript claim summary** The authors propose that the sequence binding specificity of the transcription factor PU.1 arises primarily through a nonspecific electrostatically driven DNA mechanism, in which PU.1 binding alters the elastic properties of DNA. They report that nonspecific electrostatic binding stiffens DNA and promotes protein sliding in a search mode, whereas binding at the specific site softens DNA locally, enabling configurational entropy-driven locking. They suggest this constitutes a generic mechanism for indirect readout.
- **Visible evidence base** Abstract text only; no quantitative data, simulation details, model parameters, or statistical analyses are available
- **Missing materials affecting confidence** Full manuscript, methods section, simulation protocols, model validation, quantitative results, figures, tables, and any supporting information

## Reviewer
- **Overall assessment** The abstract presents an interesting and potentially significant hypothesis regarding the role of DNA mechanical property changes in transcription factor binding specificity. The proposed mechanism, in which electrostatic interactions modulate DNA stiffness and thereby influence protein sliding and binding, is conceptually appealing and could have broad implications for understanding indirect readout. However, the abstract alone provides insufficient evidence to evaluate the validity of the central claims. Key quantitative results, model details, and validation are absent. The connection between simulated DNA stiffness changes and experimentally observed binding specificity is asserted rather than demonstrated. The claim of a "generic mechanism" is extrapolated from a single protein system and requires substantially more evidence.
- **Who would be interested in the results, and why** Researchers in the fields of gene regulation, transcription factor biology, biophysics of protein-DNA interactions, and computational biology would find these results relevant. The proposed mechanism could inform understanding of how transcription factors achieve specificity beyond direct base contacts, which is relevant for predicting binding sites in genomics and for engineering proteins with desired DNA binding properties.
- **Major strengths** The conceptual framework is clear and addresses an important unresolved question in the field. The idea that DNA mechanical properties, modulated by electrostatic interactions, could serve as a generic readout mechanism is novel and testable. The distinction between search mode and recognition mode, linked to changes in DNA stiffness, provides a physically intuitive picture.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  Originality: The proposed mechanism, linking electrostatic modulation of DNA stiffness to indirect readout, appears conceptually novel. However, the abstract does not clearly situate this work against prior theoretical or experimental studies on DNA shape readout or protein-induced DNA bending.  
  Scientific importance: If validated, the mechanism could have broad implications for understanding transcription factor binding specificity across many systems. The importance is high, but the evidence presented is insufficient to establish the claim.  
  Interdisciplinary readership: The topic bridges molecular biology, biophysics, and computational chemistry. The abstract is written in a way that is largely accessible, though some terms such as "second-order mechanical effect" and "configurational entropy effects" may require more explanation for nonspecialists.  
  Technical soundness: Cannot be assessed from the abstract alone. No simulation details, convergence criteria, force field parameters, or validation against experimental data are provided.  
  Readability for nonspecialists: The abstract is generally readable, but the mechanistic description is compressed. A clearer explanation of how DNA stiffness changes translate to binding specificity would improve accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is interesting and worth pursuing, but the abstract alone does not provide sufficient quantitative or methodological support for the central claims. A full manuscript with detailed methods, validation, and quantitative results would be required to assess whether the case is made.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors claim that "the binding specificity of PU.1 is achieved primarily via a nonspecific electrostatically driven DNA mechanism involving the change in the elastic properties of the DNA."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract provides no quantitative data linking simulated DNA stiffness changes to experimentally observed binding specificity. No binding free energies, specificity ratios, or comparisons across the series of DNA sequences are presented. The word "primarily" implies a dominant contribution, but no decomposition of energetic or entropic contributions is shown.  
- **Why it matters** The central claim of the paper is that electrostatic modulation of DNA mechanics is the primary driver of PU.1 binding specificity. Without quantitative evidence, such as a comparison of predicted versus measured binding affinities or a demonstration that the mechanism accounts for the majority of the specificity, this claim remains unsupported.  
- **Resolution test** Provide quantitative results showing that the model reproduces experimentally measured binding specificities across the tested DNA sequences, and that the electrostatic mechanical mechanism accounts for the dominant fraction of the binding free energy difference between specific and nonspecific sites.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Model validity  
- **Claim pointer** The authors state that "we use a coarse-grained protein-DNA model to investigate the origin of the sequence specificity of the protein PU.1."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** No details of the coarse-grained model are provided. It is unclear what level of resolution is used, how the protein and DNA are represented, what force field or interaction potentials are employed, and whether the model has been validated against experimental data or atomistic simulations. The reliability of the predicted stiffness changes depends critically on these details.  
- **Why it matters** Coarse-grained models involve significant approximations. Without validation, the reader cannot assess whether the predicted DNA mechanical changes are artifacts of the model or genuine physical effects. The claim of a "generic mechanism" requires confidence that the model captures the essential physics.  
- **Resolution test** Describe the model in sufficient detail, including parameterization and validation against experimental or atomistic simulation data. Show that the model reproduces known DNA mechanical properties and protein-DNA binding behavior.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim scope  
- **Claim pointer** The authors suggest that the proposed mechanism "is a generic mechanism for indirect readout."  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The study examines a single transcription factor, PU.1, and a series of its binding sites. Generalizing from one protein to a "generic mechanism" for indirect readout across all transcription factors is a substantial extrapolation. No evidence is presented that other proteins exhibit similar behavior or that the mechanism applies beyond the PU.1 system.  
- **Why it matters** The claim of generality significantly increases the scientific importance of the work. However, if the mechanism is specific to PU.1 or to proteins with similar electrostatic properties, the broader conclusion would be overstated. The abstract does not provide comparative data or theoretical arguments supporting universality.  
- **Resolution test** Provide evidence from additional protein systems or a theoretical framework demonstrating that the mechanism is expected to apply broadly. Alternatively, temper the claim to reflect the scope of the current study.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Mechanistic clarity  
- **Claim pointer** The authors state that "PU.1 influences the DNA dynamics through a second-order mechanical effect" and that "the DNA becomes stiffer" during search mode and "softer" at the specific site.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The physical origin of the stiffness change is not explained. It is unclear how electrostatic binding leads to stiffening in one context and softening in another. The term "second-order mechanical effect" is not defined. The connection between stiffness changes and configurational entropy effects is stated but not elaborated.  
- **Why it matters** The mechanistic narrative is central to the paper's contribution. Without a clear physical explanation of how electrostatic interactions alter DNA mechanics differently in search versus recognition modes, the proposed mechanism remains descriptive rather than explanatory.  
- **Resolution test** Provide a detailed mechanistic explanation, supported by simulation data, of how electrostatic interactions lead to the observed stiffness changes. Clarify the meaning of "second-order mechanical effect" and show how configurational entropy changes arise from the local softening.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Terminology clarity  
- **Affected element** "second-order mechanical effect"  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term is used without definition or context. It is unclear whether this refers to a perturbative expansion, a nonlinear response, or something else.  
- **Required correction** Define the term explicitly or rephrase to avoid ambiguity.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology consistency  
- **Affected element** "base readout" and "shape readout"  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract uses "base readout" and "shape readout" as synonyms for "direct readout" and "indirect readout." This dual terminology may confuse readers unfamiliar with the field.  
- **Required correction** Use one consistent set of terms throughout, or explicitly state that the terms are used interchangeably.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Experimental context  
- **Affected element** Comparison with experimental data  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not mention any comparison with experimental binding data for PU.1. Such comparison would strengthen the claim that the model captures real biology.  
- **Required correction** Include a statement in the abstract or full manuscript indicating whether the model predictions are consistent with available experimental measurements.

## Risk / unsupported claims
- The claim that binding specificity is achieved "primarily" through the electrostatic mechanical mechanism is unsupported without quantitative decomposition of energetic contributions.
- The claim that the mechanism is "generic" for indirect readout is unsupported by evidence from a single protein system.
- The assertion that DNA becomes "stiffer" in search mode and "softer" at the specific site is not backed by quantitative data in the abstract.
- The connection between configurational entropy effects and local DNA softening is stated but not demonstrated.
- The validity of the coarse-grained model and its ability to capture relevant physics cannot be assessed from the abstract alone.