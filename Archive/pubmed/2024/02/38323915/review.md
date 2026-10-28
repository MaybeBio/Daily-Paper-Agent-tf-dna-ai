## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose a combined Hamiltonian replica exchange nonequilibrium alchemical method to compute absolute binding free energies for protein-ligand systems, claiming reliable results even when starting from suboptimal docking poses. The method is applied to six ligands of the BRD4 bromodomain, with starting poses from both crystallographic and top-scoring docked conformations, and the authors report statistically equivalent binding free energies between the two starting conditions.
- **Visible evidence base** Abstract text only; no numerical data, methodological details, or statistical analyses are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, computational details, force field parameters, simulation protocols, convergence criteria, statistical analysis methods, and any comparison with experimental or alternative computational results

## Reviewer
- **Overall assessment** The abstract presents a potentially valuable methodological advance for alchemical free energy calculations, addressing a recognized limitation in the field. The core idea of using Hamiltonian replica exchange to enhance sampling of binding poses before nonequilibrium alchemical transformations is conceptually sound and of practical interest. However, the abstract provides insufficient evidence to evaluate the robustness of the claims. The statistical equivalence of results from different starting poses is asserted without any quantitative support, and the scope of validation (six ligands, one protein target) is limited. The work may be of interest to computational chemists and drug discovery researchers, but the current evidence base is too thin to establish the case.
- **Who would be interested in the results, and why** Computational chemists and biophysicists working on free energy calculations, particularly those developing or applying alchemical methods for binding affinity prediction. Drug discovery scientists using structure-based virtual screening and pose prediction would also be interested, as the method could reduce the dependence on accurate crystallographic poses. Method developers in enhanced sampling and nonequilibrium thermodynamics would find the combination of Hamiltonian replica exchange with nonequilibrium alchemical transformations conceptually relevant.
- **Major strengths** The problem addressed is well recognized and practically important. The methodological combination is novel and logically motivated. The choice of a relevant pharmaceutical target (BRD4) and the comparison between crystallographic and docked poses directly tests a practical scenario. The claim of statistical equivalence, if substantiated, would be a meaningful result.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide any quantitative evidence for the central claim of statistical equivalence. No error bars, statistical tests, or convergence metrics are mentioned. The number of replicas, Hamiltonian perturbation schedule, nonequilibrium work protocol, and number of independent simulations are not described. Without these details, the reliability of the results cannot be assessed.
- **Assessment against Nature-style criteria** Originality: The combination of Hamiltonian replica exchange with nonequilibrium alchemical transformations for pose correction appears novel, though the individual components are established. Scientific importance: The problem of pose dependence in alchemical calculations is significant for the field, and a robust solution would have broad applicability. Interdisciplinary readership: The work is primarily of interest to computational chemists and structural biologists; broader interdisciplinary appeal is limited. Technical soundness: Cannot be evaluated from the abstract alone; the lack of methodological detail and quantitative results prevents assessment. Readability for nonspecialists: The abstract is reasonably clear for a technical audience but assumes familiarity with alchemical methods and replica exchange; it would be challenging for nonspecialists to assess the significance without more context.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual approach is promising, but the abstract alone does not provide sufficient evidence to support the central claims. A full manuscript with detailed methods, convergence analysis, and statistical validation would be required to assess whether the case is made.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that the method "produces statistically equivalent binding free energies" when starting from crystallographic versus docked poses.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The central claim of statistical equivalence is stated without any quantitative support. No numerical values, error estimates, statistical tests, or confidence intervals are provided. The abstract does not indicate how equivalence was assessed, what threshold was used, or how many independent simulations were performed.
- **Why it matters** The entire value proposition of the method rests on the demonstration that results are independent of starting pose. Without quantitative evidence, the claim is unverifiable and could reflect insufficient sampling rather than true convergence. Statistical equivalence in free energy calculations requires careful analysis of variance and convergence, which cannot be assessed from the abstract.
- **Resolution test** Provide the computed binding free energies for each ligand from both starting poses, with associated uncertainties, and describe the statistical test used to establish equivalence. Include convergence plots and replicate information.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The method is described as a "combined Hamiltonian replica exchange nonequilibrium alchemical method" that "enhances the sampling of slow degrees of freedom."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract provides no details on the Hamiltonian replica exchange protocol, including the number of replicas, the perturbation parameter schedule, the exchange acceptance criteria, or the length of the replica exchange phase. Similarly, the nonequilibrium alchemical protocol is not described, including the switching time, the number of work values collected, or how free energies were estimated from the work distributions.
- **Why it matters** The reliability of nonequilibrium alchemical calculations depends critically on the protocol design. Without these details, it is impossible to assess whether the method is well-converged, whether the replica exchange phase is sufficient to overcome pose barriers, or whether the results are sensitive to protocol choices. Reproducibility requires full methodological transparency.
- **Resolution test** Provide a complete description of the Hamiltonian replica exchange and nonequilibrium alchemical protocols, including all parameters, in the full manuscript. Include validation of convergence and sensitivity analysis where appropriate.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors state the method is "a useful tool for computational drug discovery pipelines."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The method is tested on only six ligands of a single protein target (BRD4). This is a very limited validation set. The claim of general utility for drug discovery pipelines implies broader applicability, but the abstract provides no evidence that the method works for diverse targets, ligand chemotypes, or binding site geometries.
- **Why it matters** Pose correction is likely to be system-dependent. The difficulty of escaping suboptimal poses depends on the energy landscape, the size and flexibility of the ligand, and the nature of the binding site. Six ligands of one bromodomain do not establish general applicability.
- **Resolution test** Either temper the claim to reflect the limited validation, or provide additional evidence from diverse systems in the full manuscript. If the claim is retained, justify why BRD4 is representative of the broader challenges in pose correction.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term "suboptimal initial binding poses" is used, but the degree of suboptimality is not quantified. The abstract later mentions that crystallographic and docked poses are "often significantly different," but no metric is given.
- **Required correction** Define what constitutes a suboptimal pose, for example by reporting RMSD values between crystallographic and docked poses for each ligand.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Context
- **Affected element** Comparison with existing methods
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract does not compare the proposed method with existing approaches for handling pose uncertainty, such as multiple independent simulations from different starting poses or enhanced sampling methods applied directly to the alchemical transformation.
- **Required correction** Briefly state how the proposed method compares with or improves upon existing strategies, or acknowledge that such a comparison is provided in the full manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Software and data availability
- **Evidence pointer** Abstract text; location not provided
- **Issue** No mention is made of software availability, input files, or data deposition. For a methodological paper, reproducibility is enhanced by making these materials available.
- **Required correction** State in the full manuscript whether the code and data are available, and under what license or access conditions.

## Risk / unsupported claims
- The claim of "statistically equivalent binding free energies" is unsupported by any quantitative evidence in the abstract.
- The claim that the method is "a useful tool for computational drug discovery pipelines" is a general assertion not supported by the limited validation described.
- The implicit claim that the Hamiltonian replica exchange phase reliably populates the correct binding pose from approximate docking poses is not directly evidenced; the abstract only reports final free energy equivalence, not pose populations during the simulation.
- The performance of the method relative to computational cost is not addressed, which is relevant for practical utility in drug discovery.