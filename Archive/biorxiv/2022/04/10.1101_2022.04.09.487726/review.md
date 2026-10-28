## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as presented in the abstract and significance statement
- **Shared manuscript claim summary** The authors report a cryo-EM structure of a C-terminally truncated Redβ annealase (residues 1-177) bound to two complementary 27mer oligonucleotides, at 3.3 Å resolution. They state this structure validates prior biochemical observations, defines subunit interaction surfaces, explains DNA binding and oligomerization, and reveals a hydrogen bonding network positioning DNA strands for base pairing. They further report that residues 133-138 form a flexible loop, modeled by molecular dynamics simulations, proposed to retain DNA strands in the binding groove during homology searching. A detailed mechanism for Redβ action is proposed.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, cryo-EM maps and models, validation statistics, molecular dynamics simulation details, experimental methods, and any supporting biochemical data

## Reviewer
- **Overall assessment** The abstract presents a potentially significant structural result, namely the first cryo-EM structure of a Redβ annealing intermediate, which could substantially advance understanding of single-strand annealing recombination. However, the evidence base available for this review is limited to the abstract, and several claims, particularly those regarding the flexible loop's functional role and the proposed mechanism, are not assessable without the full manuscript and supporting data. The work is likely of interest to the DNA repair and recombination community, but the strength of the conclusions cannot be fully evaluated from the supplied material.
- **Who would be interested in the results, and why** Researchers studying homologous recombination, DNA repair, and bacteriophage biology would be interested. The Redβ/λExo system is widely used for genetic engineering, so laboratories employing recombineering would value mechanistic insights. The proposed relevance to annealase superfamilies extends interest to those studying related proteins in eukaryotic systems.
- **Major strengths** The abstract reports a first structure of a functionally important annealing intermediate, which addresses a long-standing gap. The resolution of 3.3 Å is adequate for defining protein-DNA interactions and subunit interfaces. The combination of structural and computational approaches is appropriate for generating mechanistic hypotheses. The work has clear potential to rationalize decades of biochemical data.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 (validation of the flexible loop claim), R1-M2 (support for the proposed mechanism), R1-M3 (generalizability to full-length Redβ and other annealases)
- **Assessment against Nature-style criteria** Originality is high, as this appears to be the first structure of a Redβ annealing intermediate. Scientific importance is substantial given the widespread use of the λ Red system and the conserved nature of single-strand annealing. Interdisciplinary readership is plausible, spanning structural biology, biochemistry, and molecular genetics. Technical soundness cannot be fully assessed from the abstract alone, but the reported resolution and methods are plausible. Readability for nonspecialists is adequate, though the abstract assumes familiarity with recombination terminology. Overall, the work has strong potential but requires full validation.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the flexible loop functional claim and the proposed mechanism, which require the full manuscript and simulation details.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The abstract states that molecular dynamics simulations suggested the flexible loop (residues 133-138) has a crucial role in keeping DNA strands in the DNA-binding groove long enough to allow homology searching.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The claim that the flexible loop has a "crucial role" in retaining DNA strands is based on molecular dynamics simulations, but no details of the simulation methodology, force fields, simulation timescales, or convergence criteria are provided. The abstract does not indicate whether the simulations were performed on the cryo-EM structure, a modeled loop, or multiple conformations. Without these details, the functional significance attributed to the loop cannot be evaluated.
- **Why it matters** This claim is central to the proposed mechanism of Redβ action. If the simulation evidence is insufficient or overinterpreted, the mechanistic conclusion would be unsupported, weakening the overall contribution.
- **Resolution test** Provide full simulation methods, including system setup, force field parameters, simulation length, and analysis of loop dynamics. Show that the loop's motion is reproducibly sampled and that its removal or restriction measurably affects DNA retention in the model. Ideally, support the simulation with mutagenesis or biochemical experiments.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for conclusions
- **Claim pointer** The abstract states that the combination of structural and computational observations allowed the authors to propose a detailed mechanism for the action of Redβ.
- **Evidence pointer** Abstract text; location not provided
- **Concern** A "detailed mechanism" is claimed, but the abstract provides only a brief outline involving DNA positioning and loop-mediated retention. The mechanistic steps, such as the order of strand binding, the role of subunit interfaces in coordinating annealing, and the transition from the annealing intermediate to a complete duplex, are not described. The evidence supporting each mechanistic step is not presented.
- **Why it matters** A detailed mechanism is a major claim that goes beyond the static structure. Without a stepwise model and supporting data, the mechanism remains speculative, and the abstract overstates the strength of the conclusions.
- **Resolution test** In the full manuscript, present a clear stepwise mechanism with each step linked to specific structural features, simulation results, or biochemical experiments. Distinguish between directly observed features and inferred steps, and avoid overclaiming in the abstract.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The abstract states that the structure sheds light on other proteins within the annealase superfamilies.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The structure is of a C-terminally truncated Redβ (residues 1-177), and the abstract does not clarify whether the truncated region affects the annealing mechanism or the relevance of the structure to full-length Redβ. The claim of broader relevance to annealase superfamilies is plausible but not substantiated by sequence or structural comparisons in the abstract.
- **Why it matters** The significance statement emphasizes the conserved nature of single-strand annealing, so the generalizability claim is important for the broader impact. Without evidence of conservation of the key structural features, the claim is speculative.
- **Resolution test** Provide a comparison of the Redβ structure with other annealase structures or models, and discuss the conservation of the DNA-binding groove, subunit interfaces, and the flexible loop. If such comparisons are not possible, temper the claim in the abstract.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract text; location not provided
- **Issue** The phrase "annealase protein" is used without defining the term for nonspecialist readers, and the abstract assumes familiarity with the λ Red recombination system.
- **Required correction** Briefly define "annealase" and the single-strand annealing process in the abstract or significance statement to improve accessibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Structural validation
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract reports a 3.3 Å resolution but does not mention map quality metrics, such as Fourier shell correlation, or model validation statistics, such as MolProbity scores or Ramachandran outliers.
- **Required correction** Include key validation metrics in the abstract or ensure they are prominently presented in the full manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Historical context
- **Affected element** Claim of validation
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract states the structure "validates and rationalizes decades of experimental observations," but does not specify which observations are validated or how.
- **Required correction** Provide specific examples of prior biochemical findings that are explained by the structure, either in the abstract or in the introduction of the full manuscript.

## Risk / unsupported claims
- The claim that the flexible loop has a "crucial role" in DNA retention is unsupported without simulation details and experimental validation.
- The "detailed mechanism" of Redβ action is not supported by the abstract alone and requires the full manuscript.
- The generalizability to other annealase superfamilies is not substantiated in the abstract.
- The statement that the structure "validates and rationalizes decades of experimental observations" is not verifiable from the abstract, as specific observations are not cited.