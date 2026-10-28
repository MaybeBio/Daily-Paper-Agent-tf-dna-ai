## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, acknowledgments)
- **Assessment boundary** Scientific and technical evaluation of the modeling framework, theoretical claims, and simulation results as presented
- **Shared manuscript claim summary** The authors propose a mathematical model coupling transcription dynamics to local DNA supercoiling, and demonstrate in silico that a DNA-binding protein modulating the supercoiling dissipation length can control transcription rates, including pulsatile and tracking behaviors
- **Visible evidence base** Equations (1)–(20), Propositions 1, Theorems 1–3, Table 1 (referenced), Figures 2 and 3 (referenced), simulation descriptions
- **Missing materials affecting confidence** Table 1 parameter values not provided; Figures 2 and 3 not included; no experimental validation data; no code or reproducibility details beyond "available upon request"

## Reviewer
- **Overall assessment** The manuscript presents a novel conceptual framework linking supercoiling dynamics to transcriptional control via a tunable DNA-binding protein. The mathematical formulation is clear and the theoretical results are internally consistent. However, the evidence base is limited to simulations with unreported parameters and figures, and several technical gaps in the proofs and model justification weaken the case. The work is potentially interesting to the synthetic biology and control theory communities, but the current manuscript does not fully establish the claimed control efficacy or biological relevance.
- **Who would be interested in the results, and why** Researchers in synthetic biology, gene circuit design, and biophysical control theory would find the concept of using supercoiling as a control actuator novel and potentially impactful. The control Lyapunov approach for a biophysical system may also interest the broader control engineering community seeking new application domains.
- **Major strengths** The core idea of exploiting supercoiling as a control input is creative and underexplored. The model structure is simple enough to be analytically tractable while capturing a nonlinear coupling. The theoretical results (stability, monotonicity, tracking) are clearly stated and proofs are attempted. The discussion of practical implementation challenges (e.g., switching control) shows awareness of experimental constraints.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (proof of Theorem 1), R1-M2 (control law singularity), R1-M3 (parameter and figure absence), R1-M4 (biological plausibility of u(t))
- **Assessment against Nature-style criteria**  
  - Originality: High. The concept of controlling transcription via supercoiling manipulation is novel and not widely explored.  
  - Scientific importance: Moderate. If validated experimentally, the approach could offer a new modality for gene regulation, but the current theoretical-only evidence limits immediate impact.  
  - Interdisciplinary readership: Moderate. The topic bridges control theory and molecular biology, but the presentation may be too technical for biologists and too biology-heavy for control engineers.  
  - Technical soundness: Weak to moderate. The proofs have gaps, and the simulation evidence is incomplete.  
  - Readability for nonspecialists: Moderate. The introduction is accessible, but the mathematical sections assume familiarity with control Lyapunov functions and chemical reaction network modeling.
- **Recommendation posture** Currently not established from the provided evidence. The concept is promising, but the technical gaps and missing simulation details must be addressed before the claims can be supported.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** Theorem 1 claims global exponential stability of the equilibrium point (me, σe) for system (8) when α4−α3>0.  
- **Evidence pointer** Section "Transcriptional Dynamics with Supercoiling", Theorem 1 and its proof  
- **Concern** The proof bounds the vector field by a decoupled linear system Ax+b and argues that since A is Hurwitz and b is bounded, the original system is exponentially stable. This reasoning is not valid in general. Bounding a nonlinear system by a stable linear system does not imply stability of the nonlinear system unless additional conditions (e.g., comparison principles or Lyapunov inequalities) are satisfied. The radial basis function e^(−σ²/s) is bounded, but the coupling between m and σ through the shared term is not addressed. The proof does not construct a Lyapunov function for the full nonlinear system, nor does it show that the error dynamics decay exponentially.  
- **Why it matters** The global exponential stability claim is central to the paper's theoretical contribution. If the proof is invalid, the stability result is unsubstantiated, and the subsequent control design in Theorem 3 may rest on an unsound foundation.  
- **Resolution test** Provide a rigorous Lyapunov function for the full nonlinear system (8) and show that its derivative is negative definite with exponential decay bounds. Alternatively, use a comparison theorem or contraction mapping argument that explicitly accounts for the nonlinear coupling.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** Theorem 3 claims that the control law (12) asymptotically tracks a dynamic reference mr(t) and stabilizes σ(t) about σr.  
- **Evidence pointer** Section "Supercoiling-Transcription Model with DNA Binding Protein Interference", Theorem 3 and its proof  
- **Concern** The control law (12) contains a division by the term [k1(σr−σ)+(α4−α3)σ]. If this term equals zero at any time, the control input u(t) becomes singular. The proof does not address this possibility, nor does it specify conditions on the reference signals or initial conditions to avoid singularity. Additionally, the derivation of u(t) in equation (15) appears to have an error: solving for u from ėσ = −k1eσ should yield u = [k1eσ + σ̇r + (α4−α3)σ] / (α2 e^(−σ²/s)), but the manuscript writes u(t) = α2 e^(−σ²/s) [k1eσ + σ̇r + (α4−α3)σ], which is dimensionally inconsistent.  
- **Why it matters** The control law is the main practical contribution. A singular or incorrectly derived control law cannot be implemented, and the tracking claim is not credible without a correct and well-defined expression.  
- **Resolution test** Correct the algebra in the derivation of u(t). State conditions under which the denominator is nonzero (e.g., bounds on σr, σ, and parameters). Provide a simulation example where the control law is implemented without singularities and tracking is demonstrated.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The simulation results in Section "Simulation Results" claim pulsatile responses, tracking behavior, and switching control outcomes.  
- **Evidence pointer** Section "Simulation Results", Table 1, Figures 2 and 3  
- **Concern** Table 1 (parameter values) and Figures 2 and 3 are referenced but not provided in the manuscript. Without these, the simulation results cannot be reproduced or independently verified. The text states "parameters are defined in Table 1" and "plotted in Figure 3," but the actual values and plots are absent.  
- **Why it matters** Reproducibility is a core requirement for scientific claims. The numerical results are the only evidence for the theoretical predictions, and their absence prevents any assessment of the model's behavior.  
- **Resolution test** Include Table 1 with all parameter values and Figures 2 and 3 with clear axis labels, legends, and captions. Provide the simulation code or a detailed pseudocode to enable replication.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Biological plausibility  
- **Claim pointer** The manuscript proposes that a DNA-binding protein can be used to control the supercoiling dissipation length Lt in real time, including negative values of u(t).  
- **Evidence pointer** Section "Supercoiling-Transcription Model with DNA Binding Protein Interference"  
- **Concern** The manuscript states that u(t) may range from positive to negative values, where negative u(t) would indicate binding upstream of the gene. However, the physical interpretation of a negative length is unclear, and the manuscript does not explain how a DNA-binding protein could be repositioned rapidly enough to implement the control law (12) in vivo. The authors acknowledge that "the experimental details of such a realization are beyond the scope of this paper," but the model's control authority depends on this assumption.  
- **Why it matters** If the proposed actuator cannot be realized, the control scheme remains purely theoretical. The paper should either provide a more concrete biophysical mechanism or clearly state the assumptions under which the control law is feasible.  
- **Resolution test** Provide a more detailed discussion of how a DNA-binding protein could be dynamically positioned (e.g., optogenetic, magnetic, or chemical induction) and how negative u(t) would be interpreted physically. Alternatively, restrict the control law to positive u(t) and discuss the implications for controllability.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Proposition 1 proof  
- **Evidence pointer** Section "Transcriptional Dynamics with Supercoiling", Proposition 1  
- **Issue** The proof states that the intersection occurs with σe<0, but the proposition claims σe>0. This appears to be a typographical error.  
- **Required correction** Correct the sign in the proof to be consistent with the proposition statement.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Notation  
- **Affected element** Equation (8) and subsequent text  
- **Evidence pointer** Section "Transcriptional Dynamics with Supercoiling"  
- **Issue** The notation σ is used both as the supercoiling density variable and in the radial basis function exponent. This is not confusing per se, but the subscript σX is dropped without explicit mention, which may confuse readers.  
- **Required correction** State explicitly that σ denotes σX throughout the remainder of the paper.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Simulation section  
- **Evidence pointer** Section "Simulation Results"  
- **Issue** The simulation section mentions "three numerical findings" but only two are described in detail (pulsatile response and dynamic control). The third (switching control) is mentioned but not elaborated.  
- **Required correction** Provide a more detailed description of the switching control simulation, including the switching law, parameter choices, and expected behavior.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Referencing  
- **Affected element** Introduction  
- **Evidence pointer** Section "Introduction"  
- **Issue** The introduction cites references [1]–[32] but does not provide a reference list in the manuscript.  
- **Required correction** Include a complete reference list.

## Risk / unsupported claims
- The claim of global exponential stability (Theorem 1) is not supported by the provided proof, which relies on an invalid bounding argument.
- The control law in Theorem 3 is derived with an apparent algebraic error and may be singular for some states; the tracking claim is therefore not established.
- The simulation results (pulsatile response, tracking, switching) are not verifiable because Table 1 and Figures 2 and 3 are not included.
- The biological feasibility of dynamically controlling u(t) (including negative values) is asserted without a concrete mechanism or experimental precedent.
- The model's assumption that polymerase concentration is vastly abundant and gene copy number is low (Assumption 1) is stated but not justified with biological data or references.