## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use extensive molecular simulations to investigate how short-range electrostatic interactions, specifically salt-bridges between a phosphorylated serine and conserved positively charged residues within the phospho-motif of the NCBD of CBP/p300, can reshape the conformational ensemble of this intrinsically disordered protein and rescue its binding competency, in contrast to previously reported long-range electrostatic effects that drive compaction and reduce binding affinity.
- **Visible evidence base** Abstract text only; no simulation details, system setup, force field parameters, convergence criteria, or quantitative results are provided
- **Missing materials affecting confidence** Full manuscript, simulation methodology, force field validation, convergence analysis, quantitative ensemble comparisons, binding affinity calculations, and any experimental validation

## Reviewer
- **Overall assessment** The abstract presents an interesting hypothesis regarding the role of short-range versus long-range electrostatics in modulating the conformational ensemble of a phosphorylated intrinsically disordered protein. The concept of charge relaying within phospho-motifs as a regulatory mechanism is potentially novel and could have broader implications for understanding phosphorylation-dependent signaling. However, the abstract provides insufficient technical detail to evaluate the robustness of the simulation approach, the statistical significance of the observed ensemble differences, or the strength of the claim that binding competency is "rescued." The central conclusion rests on simulation evidence that is not described in sufficient detail to assess its validity.
- **Who would be interested in the results, and why** Researchers studying intrinsically disordered proteins, phosphorylation-dependent signaling, and the role of electrostatics in protein conformational regulation. Computational biophysicists interested in molecular dynamics simulations of disordered proteins would also find the methodological approach relevant. The potential generalizability to other phospho-motifs could attract a broader audience in cell signaling and structural biology.
- **Major strengths** The abstract addresses a mechanistically important question about how phosphorylation effects on disordered proteins might be modulated by local sequence context. The distinction between long-range and short-range electrostatic interactions is conceptually clear and provides a testable framework. The suggestion that conserved positive charges in phospho-motifs may act as a general regulatory relay is an intriguing and potentially impactful hypothesis.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide any quantitative metrics for ensemble differences, no description of how "binding competency" was assessed in silico, no information on simulation length, sampling convergence, or force field choice, and no statistical analysis supporting the claim that the observed effects are robust rather than stochastic.
- **Assessment against Nature-style criteria**  
  - Originality: The concept of charge relaying within phospho-motifs appears novel, though the abstract does not fully distinguish it from previously described electrostatic screening effects.  
  - Scientific importance: Potentially high if the mechanism generalizes beyond NCBD, but the abstract does not provide evidence for such generalizability.  
  - Interdisciplinary readership: The topic bridges computational biophysics and cell signaling, which could attract a broad audience, but the abstract is written in a way that assumes significant prior knowledge of NCBD and disordered protein simulation.  
  - Technical soundness: Cannot be assessed from the abstract alone; no methodological details are provided.  
  - Readability for nonspecialists: The abstract is dense and uses specialized terminology without sufficient context, making it difficult for nonspecialists to follow the key distinction between short-range and long-range electrostatics.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is interesting and worth pursuing, but the abstract alone does not provide sufficient evidence to support the central claims. A supportive posture would require access to the full manuscript with detailed simulation methodology and quantitative results.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors claim that "empowering proximal electrostatic interactions, as opposed to long-range electrostatics, can reshape the NCBD ensemble rescuing the binding competency of phosphorylated NCBD."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract provides no quantitative description of the simulation results that support this claim. No metrics are given for ensemble differences, no comparison between the short-range and long-range electrostatic scenarios is quantified, and no definition of "binding competency" in the context of the simulations is provided.  
- **Why it matters** The central conclusion of the abstract rests entirely on the ability of the simulations to demonstrate a meaningful and statistically robust difference between the two electrostatic regimes. Without quantitative evidence, the claim cannot be evaluated or reproduced.  
- **Resolution test** Provide quantitative ensemble descriptors (e.g., radius of gyration, contact maps, secondary structure propensities) with associated uncertainties, a clear definition of how binding competency is assessed in silico, and statistical tests demonstrating that the observed differences are significant.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The authors state that "extensive molecular simulations" were performed to investigate the effect of short-range electrostatics on the NCBD conformational ensemble.  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** No methodological details are provided regarding the simulation setup. The force field, water model, salt concentration, temperature, simulation length, number of replicas, and convergence criteria are all absent. For intrinsically disordered proteins, simulation results are highly sensitive to force field choice and sampling quality.  
- **Why it matters** Without knowledge of the simulation parameters, it is impossible to assess whether the simulations adequately sampled the conformational ensemble or whether the results are artifacts of the chosen methodology. This is particularly critical for disordered proteins where force field biases are well documented.  
- **Resolution test** Provide full simulation details in the manuscript, including force field validation against experimental data for NCBD, convergence analysis (e.g., block averaging, multiple independent runs), and demonstration that the observed ensemble differences are robust across simulation conditions.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Scientific importance  
- **Claim pointer** The authors propose that "proximal electrostatic interactions might dampen the effects of phosphorylation and act as a relay to regulate phosphorylated intrinsically disordered proteins, ultimately tuning the binding affinity for different cellular partners."  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract does not provide any evidence that the proposed mechanism extends beyond the specific NCBD system studied. No data are presented on other phospho-motifs, other disordered proteins, or experimental validation of the predicted effects on binding affinity.  
- **Why it matters** The broader significance of the work depends on the generalizability of the proposed charge relaying mechanism. Without evidence for generality, the claim remains speculative and the impact on the field is limited.  
- **Resolution test** Provide either additional simulation data on other phospho-motif-containing proteins or experimental validation (e.g., binding assays with mutated phospho-motifs) demonstrating that the proposed mechanism operates in other contexts.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract uses the term "phospho-motif" without defining its boundaries or consensus sequence, which may confuse readers unfamiliar with NCBD.  
- **Required correction** Define the phospho-motif sequence and its position within NCBD in the abstract or provide a brief contextual description.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Scientific importance  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not state the specific phosphorylated serine residue or the positively charged residues involved in the proposed short-range interactions.  
- **Required correction** Identify the specific residues studied to allow readers to contextualize the findings within the NCBD structure.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract text  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The phrase "charge relaying" is introduced in the title but not explicitly defined or explained in the abstract.  
- **Required correction** Briefly explain what is meant by charge relaying in the context of the proposed mechanism.

## Risk / unsupported claims
- The claim that short-range electrostatics "rescue" binding competency is unsupported by quantitative data in the abstract.
- The claim that the proposed mechanism may "act as a relay to regulate phosphorylated intrinsically disordered proteins" is speculative and not supported by evidence beyond the NCBD system.
- The assertion that the findings have implications for "tuning the binding affinity for different cellular partners" is not supported by any binding data presented in the abstract.
- The distinction between the previously reported long-range electrostatics and the current short-range electrostatics is not quantified, making the novelty of the contribution difficult to assess.