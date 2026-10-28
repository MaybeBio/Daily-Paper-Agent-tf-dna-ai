## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the supplied abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose that a single point mutation F33Y in H-CDR1 of an anti-DNA autoantibody abolishes ssDNA binding primarily by disrupting pi-pi stacking interactions, rather than electrostatic forces, and that H-CDR2 contributes more to binding than H-CDR1. They support this with computational analyses and experimental validation using ELISA on expressed mutants.
- **Visible evidence base** Abstract text only; no experimental details, numerical data, statistical analyses, or methodological descriptions are available
- **Missing materials affecting confidence** Full manuscript, all figures and tables, experimental protocols, computational methods, raw data, statistical analyses, and any supplementary information

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting mechanistic hypothesis regarding the role of pi-pi stacking in antibody-antigen interactions, with a clear logical progression from computational prediction to experimental validation. However, the current evidence base is insufficient to evaluate the rigor of the methods, the robustness of the results, or the validity of the conclusions. Several claims are made without supporting quantitative data, and the abstract contains internal inconsistencies and undefined terms that undermine clarity.
- **Who would be interested in the results, and why** Researchers in antibody engineering, autoimmune disease mechanisms, and molecular recognition would find these results relevant. The proposed importance of pi-pi stacking over electrostatic forces in anti-DNA antibody binding could inform therapeutic antibody design and our understanding of autoantibody specificity.
- **Major strengths** The study addresses a mechanistically important question with potential translational relevance. The combination of computational prediction and experimental validation is a commendable approach. The identification of specific residues (F33(H), W98(H), Y95(L)) involved in pi-pi stacking provides a testable model.
- **Major Concerns** The abstract lacks quantitative data to support key claims, contains an internal inconsistency regarding the role of H-CDR1, and does not provide sufficient methodological detail to assess the validity of the computational or experimental approaches.
- **Minor Comments** Several typographical errors and undefined terms are present, and the abstract would benefit from clearer articulation of the relationship between computational and experimental findings.
- **Technical failings that need to be addressed before the case is established** The absence of any numerical results, statistical analyses, or methodological descriptions means that the core claims cannot be independently evaluated from the supplied material.
- **Assessment against Nature-style criteria** Originality: moderate, as the concept of pi-pi stacking in antibody-antigen interactions is not entirely novel, though the specific system may offer new insights. Scientific importance: potentially significant for antibody engineering, but the current evidence does not establish broad impact. Interdisciplinary readership: limited, as the abstract is highly specialized. Technical soundness: not assessable from the abstract alone. Readability for nonspecialists: poor, due to undefined jargon and incomplete explanations.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a plausible mechanism, but the lack of supporting data and methodological transparency prevents a definitive assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "the electrostatic force was not the primary driving force for the interaction between anti-DNA antibodies and the antigen single strand DNA (ssDNA)" and that "the H-CDR2 largely contributed to the binding of antigen ssDNA, even larger than H-CDR1."
- **Evidence pointer** Abstract text; location not provided
- **Concern** No quantitative data, experimental measurements, or computational results are presented to support these claims. The abstract does not describe how electrostatic forces were assessed, what metrics were used to compare CDR contributions, or what statistical significance was achieved.
- **Why it matters** These claims form the foundation of the mechanistic argument. Without supporting evidence, the reader cannot determine whether the conclusions are robust or based on limited or biased analyses.
- **Resolution test** Provide quantitative data (e.g., binding affinities, free energy calculations, mutagenesis results) with appropriate statistical analyses that directly compare electrostatic contributions and CDR contributions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency
- **Claim pointer** The authors state that "the H-F33Y mutation could increase the hydrogen-bond interaction but impair the pi-pi stacking interaction" and later that "Y33 in mutant could not form the parallel sandwich pi-pi stacking interaction with the ssDNA." However, they also claim that "H-CDR1" contributes less than H-CDR2, yet the mutation is in H-CDR1 and is presented as the key determinant of binding loss.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract implies that H-CDR1 is not the primary contributor to binding, yet the entire study focuses on a mutation in H-CDR1 that abolishes binding. This apparent contradiction is not resolved. If H-CDR2 is more important, why does a single H-CDR1 mutation cause complete loss of binding?
- **Why it matters** The logical coherence of the mechanistic model is central to the paper's contribution. An unresolved contradiction undermines the credibility of the interpretation.
- **Resolution test** Clarify the relative contributions of H-CDR1 and H-CDR2, and explain how a mutation in a less important region can have such a dramatic effect. Provide data that reconciles these observations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The authors state that "the wildtype antibody and the mutants (F33Y(H), F33A(H), W98A(H) and Y95A(L)) were experimentally expressed in CHO cells and purified, and the results from ELISA clearly showed that all the mutants lost the ssDNA binding ability."
- **Evidence pointer** Abstract text; location not provided
- **Concern** No experimental details are provided, including expression levels, purification yields, protein quality controls, ELISA protocols, concentrations used, or replicates. The term "clearly showed" is not supported by any numerical data or statistical analysis.
- **Why it matters** Without methodological rigor, the experimental validation cannot be assessed. The claim that all mutants lost binding ability requires quantitative evidence to rule out trivial explanations such as poor protein expression or misfolding.
- **Resolution test** Provide full experimental methods, including expression and purification details, ELISA conditions, dose-response curves, and statistical analyses demonstrating significant differences between wildtype and mutants.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term "wiletype" is a typographical error for "wildtype."
- **Required correction** Correct the spelling to "wildtype."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The phrase "broad implications in the field of antibody engineer" is grammatically incomplete and vague.
- **Required correction** Revise to "broad implications for the field of antibody engineering" and specify the nature of these implications.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term "parallel sandwich pi-pi stacking interaction" is not standard and is not defined.
- **Required correction** Define the term or use standard nomenclature for pi-pi stacking geometries (e.g., parallel-displaced, T-shaped).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract does not specify the computational methods used to predict hydrogen-bond and pi-pi stacking interactions.
- **Required correction** Briefly mention the computational approach (e.g., molecular dynamics, docking, quantum mechanics) in the abstract or refer to methods in the full text.

## Risk / unsupported claims
- The claim that electrostatic forces are not the primary driving force is unsupported without quantitative data.
- The claim that H-CDR2 contributes more than H-CDR1 to binding is unsupported without comparative measurements.
- The claim that the F33Y mutation increases hydrogen-bond interactions is unsupported without energetic or structural data.
- The claim that all mutants lost ssDNA binding ability is unsupported without ELISA data, controls, and statistical analysis.
- The claim that pi-pi stacking is the critical interaction for binding is not fully established, as other factors (e.g., conformational changes, solvation effects) are not discussed.