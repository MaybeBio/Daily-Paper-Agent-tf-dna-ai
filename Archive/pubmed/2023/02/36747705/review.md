## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract
- **Shared manuscript claim summary** The authors report that LRH-1 nuclear receptor discriminates between active and inactive ligands via distinct allosteric signaling circuits, identified through extensive molecular dynamics simulations, and that these circuits influence coregulator recruitment and transcriptional outcomes.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or simulation details provided
- **Missing materials affecting confidence** Full manuscript, simulation parameters, analysis methods, statistical validation, structural details, and experimental validation data

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting computational study of allosteric communication in LRH-1, with claims of identifying distinct signaling circuits for active versus inactive ligands. However, the evidence base is limited to the abstract, and the claims are broad and mechanistic without sufficient detail to assess technical rigor or biological validation. The study may appeal to specialists in nuclear receptor biology and computational biophysics, but the current form does not establish the case convincingly.
- **Who would be interested in the results, and why** Researchers in nuclear receptor signaling, allosteric regulation, and computational drug discovery would be interested, as the proposed circuits could inform therapeutic targeting of LRH-1. The quantitative simulation framework may also attract methodologists studying allosteric communication in proteins.
- **Major strengths** The study addresses a significant gap in understanding ligand-to-AFS communication in nuclear receptors. The use of extensive simulations (over 100 microseconds, 69 complexes) suggests a systematic approach. The identification of distinct circuits for active and inactive ligands, and the proposed role of helix 7, offers a testable hypothesis for therapeutic development.
- **Major Concerns**  
  - **Concern ID** R1-M1  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Technical soundness  
    **Claim pointer** The abstract claims identification of distinct allosteric signaling circuits for active and inactive ligands based on molecular dynamics simulations.  
    **Evidence pointer** Abstract, "Using >100 microseconds of all-atom molecular dynamics simulations involving 69 LRH-1 complexes"  
    **Concern** The abstract provides no details on simulation convergence, force field selection, system setup, or analysis methods for defining "circuits." Without these, the reliability of the identified circuits cannot be assessed.  
    **Why it matters** The core claim rests entirely on computational methodology; inadequate technical details undermine confidence in the findings.  
    **Resolution test** Provide full methods, including convergence criteria, error analysis, and validation of circuit identification against independent metrics or experimental data.  
  - **Concern ID** R1-M2  
    **Severity** Major  
    **Blocking** Yes  
    **Axis** Scientific importance  
    **Claim pointer** The abstract claims that inactive ligands communicate via strong coordinated motions and activating ligands disrupt this circuit, with implications for therapeutic development.  
    **Evidence pointer** Abstract, "Inactive ligands communicate via strong, coordinated motions along paths through the receptor to the AFS. Activating ligands disrupt the 'inactive' circuit by inducing connectivity elsewhere."  
    **Concern** The biological relevance of these computational circuits is not validated experimentally. No functional assays, mutagenesis, or coregulator recruitment data are mentioned to support the claim that these circuits underlie differential transcriptional outcomes.  
    **Why it matters** Without experimental validation, the claim that these circuits are functionally meaningful remains speculative.  
    **Resolution test** Include experimental data, such as mutations in helix 7 residues that alter ligand response or coregulator recruitment, to corroborate the computational predictions.  
  - **Concern ID** R1-M3  
    **Severity** Major  
    **Blocking** No  
    **Axis** Interdisciplinary readership  
    **Claim pointer** The abstract states that the quantitative approach provides a framework to study allosteric signaling in other receptors.  
    **Evidence pointer** Abstract, "the quantitative approach used to analyze many simulations provides a framework to study allosteric signaling in other receptors"  
    **Concern** The abstract does not describe the quantitative approach in sufficient detail to allow others to adopt it. Terms like "signaling circuits" and "connectivity" are not defined operationally.  
    **Why it matters** The claimed framework is a key contribution, but its utility is unclear without methodological transparency.  
    **Resolution test** Provide a clear description of the analytical pipeline, including metrics for circuit identification and statistical treatment, in the full manuscript.  
- **Minor Comments**  
  - **Concern ID** R1-m1  
    **Severity** Minor  
    **Axis** Readability for nonspecialists  
    **Affected element** Abstract  
    **Evidence pointer** Abstract, "AFS" and "coregulator"  
    **Issue** Terms like AFS and coregulator are used without definition, which may hinder nonspecialist readers.  
    **Required correction** Define AFS and coregulator briefly in the abstract or provide context.  
  - **Concern ID** R1-m2  
    **Severity** Minor  
    **Axis** Technical soundness  
    **Affected element** Simulation scope  
    **Evidence pointer** Abstract, "69 LRH-1 complexes"  
    **Issue** The number of complexes is stated, but the diversity of ligands and their classification as active or inactive is not specified.  
    **Required correction** Clarify the ligand set and how activity was defined.  
  - **Concern ID** R1-m3  
    **Severity** Minor  
    **Axis** Scientific importance  
    **Affected element** Coregulator signaling claim  
    **Evidence pointer** Abstract, "localized, destabilizing fluctuations are induced by inappropriate ligand-coregulator pairings"  
    **Issue** This claim is vague and lacks detail on how "inappropriate pairings" were determined.  
    **Required correction** Specify the criteria for appropriate versus inappropriate pairings and the evidence for destabilizing fluctuations.  
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking. The lack of methodological detail and experimental validation prevents assessment of the core claims. The abstract alone does not establish the case.
- **Assessment against Nature-style criteria**  
  - Originality: The concept of distinct allosteric circuits for ligand discrimination is novel, but its novelty cannot be fully assessed without comparison to prior work.  
  - Scientific importance: Potentially high for nuclear receptor biology, but unvalidated claims reduce current impact.  
  - Interdisciplinary readership: The topic bridges computational and biological fields, but the abstract is too technical for broad appeal.  
  - Technical soundness: Not assessable from the abstract; simulation methods and analysis are not described.  
  - Readability for nonspecialists: The abstract uses jargon without explanation, limiting accessibility.  
- **Recommendation posture** Currently not established from the provided evidence. The study has potential, but the abstract lacks the technical and experimental detail needed to support the claims. Supportive if technical concerns are resolved in the full manuscript.

## Risk / unsupported claims
- The claim of distinct allosteric circuits for active versus inactive ligands is unsupported without methodological details.
- The claim that helix 7 residues mediate the switch between circuits is unsupported without mutagenesis or functional data.
- The claim that the quantitative approach provides a general framework is unsupported without a description of the method.
- The claim regarding coregulator signaling and destabilizing fluctuations is vague and not assessable from the abstract.