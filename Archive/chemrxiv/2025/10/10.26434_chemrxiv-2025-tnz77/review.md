## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors propose coarse-grained funnel metadynamics (CG-FMD) with the Martini 3 forcefield as a computationally efficient alternative to all-atom molecular dynamics (AA-MD) for protein-ligand binding free energy estimation. They report that CG-FMD produces ΔGbind estimates comparable to experimental values for colchicine binding to two protein targets, at a fraction of the computational cost of AA-MD, with reduced statistical uncertainty from extensive sampling exceeding 7 milliseconds of simulation.
- **Visible evidence base** Abstract text only; no quantitative data, simulation details, or experimental comparisons are presented
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, simulation parameters, error analysis, and experimental reference values

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable methodological contribution addressing a well-recognized gap between docking throughput and all-atom MD accuracy. The combination of coarse-graining with funnel metadynamics is conceptually sound and the reported scale of sampling is impressive. However, the abstract provides insufficient quantitative evidence to evaluate the central claims. Key metrics such as the magnitude of ΔGbind values, the degree of agreement with experiment, the actual computational speedup, and the statistical uncertainties are all absent. The claim of robustness across simulation setup aspects is unsubstantiated without details on which aspects were varied and how results changed. The scope is narrow, with only one ligand and two targets, which limits generalizability claims. The work may be of interest to computational chemists and drug discovery researchers, but the case is not established from the provided material.
- **Who would be interested in the results, and why** Computational chemists and biophysicists developing or applying enhanced sampling methods for binding free energy prediction would be the primary audience. Drug discovery researchers seeking higher-throughput yet physics-based screening approaches may also find the work relevant. The methodological focus on balancing accuracy and cost addresses a practical need in these communities.
- **Major strengths** The conceptual combination of Martini 3 coarse-graining with funnel metadynamics is a reasonable and potentially impactful innovation. The reported collection of over 7 milliseconds of CG-FMD simulation time demonstrates a serious commitment to statistical rigor. The explicit acknowledgment of trade-offs between simplified representation and extensive sampling is a thoughtful framing.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria**  
  Originality: The specific combination of CG-FMD with Martini 3 is not entirely novel but may offer a distinct contribution if the performance claims hold. Scientific importance: The problem addressed is significant, but the narrow test set limits the importance of the specific results. Interdisciplinary readership: The work is primarily relevant to computational chemistry and biophysics, with limited reach beyond these fields. Technical soundness: Cannot be assessed from the abstract alone; the absence of quantitative data prevents evaluation of methodological rigor. Readability for nonspecialists: The abstract is clear and accessible, though technical terms are used without definition.
- **Recommendation posture** Currently not established from the provided evidence. The abstract promises a useful method but does not provide the quantitative support needed to evaluate the core claims. A revised abstract with specific numbers and a full manuscript would be required for a supportive posture.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The claim that CG-FMD yields ΔGbind estimates comparable to experimental values is central to the work.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract states that CG-FMD produces ΔGbind estimates comparable to experimental values but provides no numerical data. No ΔGbind values, experimental references, or error margins are given. The phrase "comparable to" is undefined without quantitative context.
- **Why it matters** The primary contribution of the work is the accuracy of binding free energy predictions. Without specific values and a defined criterion for comparability, the claim cannot be verified or reproduced. This is the core evidence needed to support the method's utility.
- **Resolution test** Provide the computed ΔGbind values for both targets, the corresponding experimental values, and the associated uncertainties. Define a quantitative threshold for "comparable" (e.g., within 1 kcal/mol or within experimental error).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The claim that CG-FMD requires only a fraction of the computational cost of AA-MD is a key advantage.
- **Evidence pointer** Abstract, location not provided
- **Concern** No quantitative comparison of computational cost is provided. The abstract does not state the speedup factor, the wall-clock time, or the computational resources used for CG-FMD versus AA-MD.
- **Why it matters** The efficiency advantage is a central selling point of the method. Without concrete numbers, the claim is unverifiable and the practical benefit cannot be assessed. This is essential for readers to judge whether the trade-off between accuracy and cost is favorable.
- **Resolution test** Report the relative computational cost (e.g., speedup factor or CPU-hours) for CG-FMD compared to AA-MD for the same systems, with clear definitions of the comparison basis.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The claim that extensive CG-FMD sampling reduces statistical uncertainty is presented as a compensating advantage.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract mentions reduced statistical uncertainty but provides no quantitative measures. No error bars, confidence intervals, or convergence metrics are reported. The relationship between sampling time and uncertainty reduction is not demonstrated.
- **Why it matters** Statistical rigor is critical for binding free energy predictions. Without quantitative uncertainty estimates, the reliability of the results cannot be evaluated. This is necessary to support the claim that CG-FMD compensates for the simplified representation.
- **Resolution test** Provide statistical uncertainties (e.g., standard error or 95% confidence intervals) for the ΔGbind estimates and show how they decrease with increasing simulation time.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Scope and generalizability
- **Claim pointer** The abstract implies the method is broadly applicable, but the test set is limited to one ligand and two targets.
- **Evidence pointer** Abstract, location not provided
- **Concern** The study uses colchicine with two protein targets only. The abstract does not discuss the diversity of the test systems or the potential for method failure on other ligand-target pairs. The claim of robustness across simulation setup aspects is mentioned but not detailed.
- **Why it matters** Binding free energy methods often perform well on specific systems but fail on others. A two-system test is insufficient to establish generalizability. The robustness claim is unsubstantiated without specifying which setup aspects were varied and the results of those variations.
- **Resolution test** Expand the test set to include a broader range of ligands and targets, or clearly state the limitations of the current scope. Provide details on the setup variations tested and their impact on ΔGbind predictions.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "state-of-the-art enhanced sampling techniques" is vague and does not specify which techniques are used beyond funnel metadynamics.
- **Required correction** Specify the exact enhanced sampling methods employed (e.g., well-tempered metadynamics, multiple walkers) to improve clarity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Simulation details
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not mention the Martini 3 version, the protein and ligand parameterization details, or the system setup (e.g., box size, salt concentration).
- **Required correction** Include key simulation parameters in the abstract or refer to a methods section where these are fully described.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Context
- **Affected element** Comparison to existing methods
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not compare CG-FMD performance to other enhanced sampling or coarse-grained approaches, which would help contextualize the contribution.
- **Required correction** Add a brief comparison to existing methods (e.g., standard funnel metadynamics in AA, other CG approaches) to highlight the specific advantages.

## Risk / unsupported claims
- The claim that CG-FMD yields ΔGbind estimates comparable to experimental values is unsupported due to the absence of quantitative data.
- The claim that CG-FMD requires only a fraction of the computational cost of AA-MD is unsupported without specific cost comparisons.
- The claim that extensive sampling reduces statistical uncertainty is unsupported without quantitative uncertainty measures.
- The claim of robustness across various aspects of the simulation setup is unsubstantiated as no details on the variations or results are provided.
- The generalizability of the method beyond the tested systems (colchicine with two targets) is not supported by the evidence presented.