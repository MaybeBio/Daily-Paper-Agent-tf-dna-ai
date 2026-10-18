## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and conclusions as stated in the abstract; no methods, figures, tables, or supplementary material were provided
- **Shared manuscript claim summary** The authors propose a computational framework combining committor-based enhanced sampling with spectral analysis of the infinitesimal generator to characterize ligand binding and unbinding pathways. Applied to benzamidine (BEN) and para-amino benzamidine (PAB) with trypsin, the method reportedly reveals distinct binding pathways, a previously uncharacterized BEN binding site, a common rotational bottleneck for unbinding, computed unbinding free energies consistent with experiment, and residence times and kinetic rate constants consistent with experimental data and independent OPES flooding simulations at reduced computational cost.
- **Visible evidence base** Abstract text only; no figures, tables, methods descriptions, or numerical data provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods details, simulation parameters, error estimates, comparison datasets, and computational cost benchmarks

## Reviewer
- **Overall assessment** The abstract presents an ambitious and potentially valuable methodological advance in simulating protein–ligand binding and unbinding kinetics. The combination of committor-based sampling with spectral analysis of the infinitesimal generator is conceptually interesting and could address a recognized bottleneck in ligand characterization. However, the abstract alone provides insufficient evidence to evaluate the validity, robustness, or generalizability of the claims. Several assertions, particularly the discovery of a new binding site and the quantitative agreement with experimental kinetics, require detailed methodological and numerical support that is not visible here. The work is likely to interest computational chemists and biophysicists, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Computational chemists and biophysicists working on enhanced sampling methods, protein–ligand binding kinetics, and drug discovery would be the primary audience. The promise of reduced computational cost for residence time prediction and the ability to resolve multiple binding pathways could appeal to those developing or applying kinetic characterization tools in pharmaceutical research. Methodologists interested in spectral analysis of dynamical systems and committor-based approaches would also find the framework relevant.
- **Major strengths** The proposed combination of committor-based enhanced sampling with spectral analysis of the infinitesimal generator is conceptually novel and addresses a real bottleneck in ligand kinetics calculation. The application to a well-studied benchmark system (BEN–trypsin) with a congeneric ligand (PAB) provides a sensible comparative design. The claim of agreement with both experimental data and independent simulations, if substantiated, would strengthen confidence in the method. The stated computational efficiency advantage is practically significant.
- **Major Concerns**  
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness  
  - **Claim pointer** The framework "reveals distinct and multifaceted binding pathways for the two ligands, uncovering a previously uncharacterized BEN binding site that competes with the crystallographic site"  
  - **Evidence pointer** Abstract only; location not provided  
  - **Concern** The claim of a previously uncharacterized BEN binding site is a strong structural and functional assertion. No evidence is presented to demonstrate how this site was identified, how its competition with the crystallographic site was quantified, or how the authors ruled out artifacts from the enhanced sampling method.  
  - **Why it matters** A new binding site claim has significant implications for understanding BEN–trypsin interactions and for the method's credibility. If the site is an artifact of the sampling protocol or analysis, the central conclusion would be undermined.  
  - **Resolution test** Provide structural evidence (e.g., density maps, representative conformations, occupancy analysis) and a clear definition of "competition" with quantitative metrics. Demonstrate reproducibility across independent simulations and show that the site is not an artifact of biased sampling.

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness  
  - **Claim pointer** "The computed unbinding free energies closely agree with experimental measurements" and "residence times and kinetic rate constants that agree with available experimental data"  
  - **Evidence pointer** Abstract only; location not provided  
  - **Concern** Quantitative agreement claims require numerical values, error bars, and a clear statement of the experimental references used. Without these, the agreement cannot be assessed, and the magnitude of any discrepancy is unknown.  
  - **Why it matters** The quantitative accuracy of free energies and kinetics is the core validation of the method. Unsupported agreement claims are not verifiable and could mislead readers about the method's reliability.  
  - **Resolution test** Provide a table comparing computed and experimental values with uncertainties, specify the experimental sources, and state the statistical significance of any differences. Include convergence checks for the free energy and rate estimates.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness  
  - **Claim pointer** The approach "requires substantially less computational effort" than independent OPES flooding simulations  
  - **Evidence pointer** Abstract only; location not provided  
  - **Concern** The computational cost claim is presented without any quantitative basis. No wall-clock times, core-hours, or convergence criteria are given, and the comparison to OPES flooding is not contextualized.  
  - **Why it matters** Computational efficiency is a stated advantage and a key motivator for adoption. Without quantitative support, this claim is unverifiable and could be misleading.  
  - **Resolution test** Provide a direct benchmark comparing total computational cost (e.g., core-hours) for both methods to achieve comparable statistical accuracy, including details of hardware and software.

  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Reproducibility  
  - **Claim pointer** The framework combines "committor-based enhanced sampling with spectral analysis of the infinitesimal generator"  
  - **Evidence pointer** Abstract only; location not provided  
  - **Concern** The methodological description is too brief to assess novelty, implementation details, or potential limitations. Key aspects such as how committor estimates were obtained, how the generator was constructed and discretized, and how spectral components were interpreted are not described.  
  - **Why it matters** Reproducibility and critical evaluation require a detailed methods section. The abstract alone cannot establish that the approach is correctly implemented or that the spectral analysis is statistically robust.  
  - **Resolution test** Provide a complete methods description with equations, algorithmic steps, and validation on a system with known kinetics. Include sensitivity analyses for key parameters.

- **Minor Comments**  
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Abstract wording  
  - **Evidence pointer** Abstract, "eventful journey" phrase  
  - **Issue** The title and opening phrase are informal and do not convey the technical nature of the work.  
  - **Required correction** Use a more precise and descriptive title that reflects the methodological advance.

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Completeness  
  - **Affected element** Abstract scope  
  - **Evidence pointer** Abstract, last sentence  
  - **Issue** The claim of "potential applications to ligand screening" is speculative and not supported by any demonstration in the abstract.  
  - **Required correction** Either remove the speculation or provide a brief indication of how the method could be adapted for screening.

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Precision  
  - **Affected element** Terminology  
  - **Evidence pointer** Abstract, "common rotational bottleneck"  
  - **Issue** The term "bottleneck" is used without defining its kinetic or structural meaning in this context.  
  - **Required correction** Define what constitutes a bottleneck (e.g., a specific transition state or slow rotational mode) and provide evidence for its commonality across both ligands.

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4. The core claims of new binding site discovery, quantitative agreement with experiment, computational efficiency, and methodological validity all require detailed evidence not present in the abstract.
- **Assessment against Nature-style criteria**  
  - Originality: The combination of committor-based sampling with spectral analysis appears novel, but the abstract does not allow assessment of how it differs from prior spectral methods or committor approaches.  
  - Scientific importance: If validated, the method could address a recognized bottleneck in ligand kinetics, which is of high importance. However, importance is contingent on the robustness of the claims.  
  - Interdisciplinary readership: The work bridges computational chemistry, biophysics, and drug discovery, which could attract broad interest. The abstract is accessible but lacks technical depth for specialists.  
  - Technical soundness: Not assessable from the abstract. The absence of methods details and numerical results prevents evaluation of correctness or convergence.  
  - Readability for nonspecialists: The abstract is generally readable, but terms like "committor-based" and "infinitesimal generator" are used without explanation, which may limit accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising framework, but the central claims require substantial methodological and numerical support. A supportive recommendation would be contingent on the full manuscript addressing the major concerns, particularly the new binding site evidence, quantitative validation, and computational cost comparison.

## Risk / unsupported claims
- The discovery of a previously uncharacterized BEN binding site is unsupported without structural or statistical evidence.
- Quantitative agreement of computed free energies, residence times, and rate constants with experimental data is unverifiable without numerical values and error estimates.
- The claim of substantially reduced computational effort is unsupported without a direct benchmark.
- The generalizability of the method to other ligand–protein systems is asserted but not demonstrated.
- The "common rotational bottleneck" is described without defining its structural or kinetic basis.