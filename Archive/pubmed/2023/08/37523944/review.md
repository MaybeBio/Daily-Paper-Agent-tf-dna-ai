## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the supplied abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors use all-atom molecular dynamics simulations to examine the stability of Hoogsteen (HG) base pairs in duplex DNA, both in the absence and presence of proteins. They report that proteins stabilize and organize HG base pairs and the entire DNA duplex, and they identify sugar-phosphate, sugar-base, and sugar-pucker torsion angles as key contributors to this stabilization and ordering.
- **Visible evidence base** Abstract text only; no quantitative results, simulation details, or methodological descriptions are available
- **Missing materials affecting confidence** Full manuscript, simulation protocols, force field parameters, system setup, convergence criteria, error analysis, all figures and tables, and any statistical or thermodynamic data

## Reviewer
- **Overall assessment** The abstract addresses a mechanistically important question in nucleic acid biophysics, namely how protein binding stabilizes Hoogsteen base pairs in duplex DNA. The use of conformational thermodynamics within an all-atom molecular dynamics framework is a reasonable and potentially informative approach. However, the abstract provides insufficient methodological detail and no quantitative results to support the central claims. The conclusion that specific torsion angles play key roles is presented without supporting data. The work may be of interest to the nucleic acid biophysics community, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers studying DNA structural dynamics, base pair polymorphism, protein-DNA recognition, and the role of Hoogsteen base pairs in biological processes such as transcription and replication. The findings could also interest computational biophysicists developing or applying conformational thermodynamics methods to nucleic acid systems.
- **Major strengths** The question is biologically and biophysically relevant, as the mechanism of protein-induced HG base pair stabilization is not well understood. The use of conformational thermodynamics to dissect entropic and enthalpic contributions is a sophisticated and appropriate approach. The focus on specific torsion angle families provides a concrete mechanistic hypothesis that is testable.
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
  Originality: The question is not entirely novel, as experimental studies have already established protein-induced HG stabilization, but the molecular mechanism is underexplored. The conformational thermodynamics approach adds a potentially original angle.  
  Scientific importance: Moderate to high for the nucleic acid biophysics community, but the broader biological significance is not articulated in the abstract.  
  Interdisciplinary readership: The abstract is likely to appeal primarily to biophysicists and computational chemists; the broader readership would require clearer biological context.  
  Technical soundness: Cannot be assessed from the abstract alone. No simulation details, convergence checks, or error estimates are provided.  
  Readability for nonspecialists: The abstract is concise and generally clear, but terms such as "conformational thermodynamics" and specific torsion angle names may be opaque to nonspecialists without additional context.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially valuable study, but the absence of quantitative results and methodological detail prevents any assessment of validity. A full manuscript review would be required to determine whether the claims are supported.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors claim that "the presence of proteins stabilizes and organizes the HG bp and the entire DNA duplex."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract provides no quantitative data, such as free energy differences, entropy changes, or structural order parameters, to support the claim of stabilization and organization. No comparison between the naked DNA and protein-bound DNA systems is shown.  
- **Why it matters** The central conclusion of the manuscript rests on this claim. Without numerical evidence, the reader cannot evaluate the magnitude or statistical significance of the reported effect.  
- **Resolution test** Provide quantitative values for conformational free energy and entropy changes in both systems, with appropriate error estimates and statistical tests demonstrating a significant difference.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological transparency  
- **Claim pointer** The authors state that they used "all-atom molecular dynamics simulation" and "conformational thermodynamics" to investigate HG bp stability.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** No simulation details are given, including force field, water model, salt conditions, simulation length, number of replicas, equilibration protocol, or the method used to compute conformational free energies and entropies. Without this information, the reliability and reproducibility of the results cannot be assessed.  
- **Why it matters** Molecular dynamics results are highly sensitive to force field parameters and sampling protocols. The absence of these details prevents any evaluation of technical soundness.  
- **Resolution test** Provide a complete description of the simulation and analysis methods in the full manuscript, including validation of convergence and force field suitability.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim support  
- **Claim pointer** The authors claim that "sugar-phosphate, sugar-base, and sugar-pucker torsion angles play key roles in stabilizing and ordering the HG bp in the protein-bound DNA complex."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract identifies specific torsion angle families as mechanistically important but provides no data linking these angles to the observed stabilization. No correlation analysis, free energy decomposition, or mutational analysis is presented.  
- **Why it matters** This is a mechanistic claim that goes beyond the observation of stabilization. Without evidence connecting specific torsion angles to the thermodynamic outcome, the claim is speculative.  
- **Resolution test** Show quantitative correlations between torsion angle distributions or transitions and the computed free energy or entropy changes, or provide free energy decomposition by torsion angle type.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Terminology  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "conformational thermodynamics" is used without definition or context.  
- **Required correction** Briefly define the approach or cite the relevant methodological reference in the abstract.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Biological context  
- **Affected element** Significance statement  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not explain why protein-induced HG bp stabilization is biologically important.  
- **Required correction** Add one or two sentences on the potential biological roles of HG base pairs in protein-DNA recognition or gene regulation.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Scope  
- **Affected element** System description  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not specify which protein or DNA sequence was studied, nor whether multiple systems were examined.  
- **Required correction** State the specific protein-DNA system(s) used and whether the findings are general or system-specific.

## Risk / unsupported claims
- The claim that proteins stabilize and organize HG base pairs and the entire DNA duplex is unsupported by quantitative evidence in the abstract.
- The claim that specific torsion angle families play key roles in stabilization is unsupported by any data in the abstract.
- The generalizability of the findings beyond the specific system studied cannot be assessed from the supplied material.
- The methodological validity of the simulation and thermodynamic analysis is not assessable from the abstract alone.