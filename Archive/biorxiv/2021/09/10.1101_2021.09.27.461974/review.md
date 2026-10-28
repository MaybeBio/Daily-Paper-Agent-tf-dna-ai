## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors present a new computational method, PPI-GaMD, which selectively boosts interaction potential energy between protein partners to accelerate dissociation while applying a second boost to the remaining system potential to model flexibility and rebinding. The method is demonstrated on the barnase-barstar model system, with six independent 2 μs simulations capturing repetitive dissociation and rebinding events. The authors claim that calculated binding free energies and kinetic rate constants agree well with experimental data, and that simulations provide mechanistic insights involving long-range electrostatic interactions and multiple binding pathways.
- **Visible evidence base** Abstract text only; no quantitative results, methodological details, or experimental comparisons are provided
- **Missing materials affecting confidence** Full manuscript, methods section, simulation parameters, convergence criteria, error estimates, comparison data with experimental values, and any figures or tables

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable methodological advance for simulating protein-protein interactions, addressing a real challenge in the field. However, the evidence provided in the abstract is insufficient to evaluate the technical soundness of the method or the validity of the claimed agreement with experimental data. The core claims regarding binding free energies, kinetic rate constants, and mechanistic insights are stated without quantitative support. The method's novelty relative to existing GaMD variants is not clearly established from the abstract alone.
- **Who would be interested in the results, and why** Computational biophysicists and structural biologists interested in protein-protein interactions, binding free energy calculations, and molecular dynamics methodology. Researchers developing enhanced sampling techniques would also find the approach relevant, as would experimentalists studying protein binding kinetics who seek computational complementarity.
- **Major strengths** The method addresses a significant and well-recognized challenge in simulating repetitive protein association and dissociation events. The selective boosting strategy is conceptually appealing and potentially generalizable. The choice of barnase-barstar as a model system is appropriate given the availability of experimental data for validation. The claim of simultaneous calculation of thermodynamics and kinetics from a single set of simulations is ambitious and, if validated, would be a notable advance.
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
  Originality: The selective boosting of interaction potential energy is a plausible extension of GaMD, but the abstract does not clearly differentiate this from prior GaMD applications or other enhanced sampling methods targeting protein-protein interactions. The novelty claim is therefore only weakly supported.  
  Scientific importance: Protein-protein interactions are central to many biological processes, and reliable methods for calculating binding thermodynamics and kinetics would be broadly useful. The potential importance is high, but the abstract does not demonstrate that the method achieves this reliably.  
  Interdisciplinary readership: The topic bridges computational chemistry, biophysics, and structural biology. The abstract is written in a way that is accessible to these communities, though specialists in enhanced sampling would require more detail.  
  Technical soundness: Not assessable from the abstract. No convergence criteria, error analysis, force field parameters, or comparison statistics are provided. The claim of agreement with experimental data cannot be evaluated without quantitative values.  
  Readability for nonspecialists: The abstract is clear and concise, with technical terms defined in context. The writing is accessible to a broad scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising idea, but the core quantitative claims require full manuscript evaluation. A supportive posture would be contingent on verification of the technical details and validation data.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract claims that "calculated binding free energies and kinetic rate constants agree well with the experimental data."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** No quantitative values for binding free energies or kinetic rate constants are provided, nor are the corresponding experimental values. The degree of agreement is not specified, and no error estimates or statistical measures are given.  
- **Why it matters** The central validation of the method rests on this comparison. Without quantitative data, the claim of agreement is unverifiable and the method's utility cannot be assessed.  
- **Resolution test** Provide a table or figure comparing calculated and experimental binding free energies and rate constants, including uncertainties and the statistical method used to assess agreement.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The abstract states that "six independent 2 μs PPI-GaMD simulations have captured repetitive barstar dissociation and rebinding events."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not report how many dissociation and rebinding events were observed, the duration of bound and unbound states, or whether the simulations reached convergence. Without this information, it is unclear whether the sampling is sufficient to support the thermodynamic and kinetic calculations.  
- **Why it matters** Repetitive events are necessary for reliable kinetic estimates, but the number of events and their statistical independence directly affect the confidence in the calculated rate constants. Insufficient sampling would invalidate the kinetic claims.  
- **Resolution test** Report the number of observed association and dissociation events, the distribution of residence times, and convergence metrics such as block averaging or multiple independent runs showing consistent results.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological clarity  
- **Claim pointer** The abstract describes the method as "selectively boosts interaction potential energy between protein partners" and applies "another boost potential to the remaining potential energy of the entire system."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not specify how the selective boost is defined, how the boost parameters are determined, or how the two boost potentials are combined. The reweighting scheme needed to recover unbiased free energies and kinetics is not described.  
- **Why it matters** The validity of GaMD-based methods depends critically on the boost potential design and the reweighting procedure. Without these details, the method cannot be reproduced or evaluated for correctness.  
- **Resolution test** Provide a full methods section describing the boost potential formulation, parameter selection criteria, and the reweighting approach used to calculate free energies and kinetics.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Method name  
- **Evidence pointer** Abstract title and text  
- **Issue** The name "PPI-GaMD" is introduced without explaining how it differs from standard GaMD beyond the selective boosting.  
- **Required correction** Briefly state the key methodological distinction from prior GaMD implementations in the abstract.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Mechanistic insights  
- **Evidence pointer** Abstract text  
- **Issue** The claim of "mechanistic insights into barstar binding to barnase" is vague. No specific findings are described.  
- **Required correction** Provide one or two concrete examples of the mechanistic insights, such as the nature of the binding pathways or the role of specific electrostatic interactions.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Generalizability  
- **Affected element** Method applicability  
- **Evidence pointer** Abstract text  
- **Issue** The abstract states the method is "easy-to-use" but provides no evidence of ease of implementation or transferability to other systems.  
- **Required correction** Either temper this claim or provide a brief statement on the expected effort to apply the method to other PPI systems.

## Risk / unsupported claims
- The claim of agreement between calculated and experimental binding free energies and kinetic rate constants is unsupported without quantitative data.
- The claim that the method captures "repetitive" dissociation and rebinding events is unverifiable without event counts or trajectory analysis.
- The claim of providing "mechanistic insights" is unsupported without specific findings.
- The claim that the method is "highly efficient and easy-to-use" is not substantiated by any performance metrics or implementation details.
- The novelty of the method relative to existing GaMD approaches is not established from the abstract alone.