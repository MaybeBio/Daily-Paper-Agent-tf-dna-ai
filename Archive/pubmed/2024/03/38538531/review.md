## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full manuscript, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors present a replica exchange method with dynamical scaling (REDS) that combines enhanced sampling with free energy calculations to compute absolute free energies, enthalpies, and entropies for drug binding. Applied to the BRD4 system, the method yields accurate free energies but inaccurate entropies and enthalpies, with the entropic contribution being too positive, suggesting that entropy and enthalpy are more stringent tests of force field quality than free energy.
- **Visible evidence base** Abstract text only; no numerical data, methodological details, or comparative benchmarks are provided
- **Missing materials affecting confidence** Full methods, force field parameters, simulation protocols, convergence criteria, error estimates, comparison with experimental or reference data, and any figures or tables

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting approach to a challenging problem in computational drug binding, namely the calculation of absolute entropies and enthalpies. The REDS method, which uses a modified Hamiltonian replica to bridge temperature gaps, is a plausible innovation. However, the abstract provides insufficient detail to evaluate the method's validity, the accuracy of the reported results, or the strength of the conclusion that force fields fail on entropy and enthalpy. The claim that free energies are accurate while entropies and enthalpies are not is stated without quantitative support, and the absence of error analysis or comparison to established benchmarks limits the current assessment. The work may be of interest to computational chemists and drug designers, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Computational chemists and biophysicists working on free energy methods, enhanced sampling, and force field development would be interested because the work addresses a known limitation in binding thermodynamics. Drug discovery researchers using simulation-based affinity predictions may also find the method relevant, as accurate enthalpy and entropy decomposition could inform lead optimization. The finding that force fields fail on entropy and enthalpy could guide future force field improvements.
- **Major strengths** The abstract addresses a significant and under-solved problem, namely the calculation of absolute entropies and enthalpies for drug binding, which is more challenging than free energy alone. The REDS method is described as efficient for protein-sized systems, which is a practical advantage. The honest reporting of the method's failure to reproduce entropies and enthalpies is a strength, as it provides a clear benchmark for future work.
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
  Originality: The REDS approach appears novel in its use of a modified Hamiltonian replica to bridge temperature ranges, but the abstract does not clarify how it differs from existing replica exchange or Hamiltonian replica methods, so the degree of originality is not fully assessable.  
  Scientific importance: The problem of calculating binding entropies and enthalpies is important, and the finding that force fields fail on these quantities is potentially significant, but the abstract lacks the quantitative evidence needed to establish this importance.  
  Interdisciplinary readership: The work is likely to appeal to computational chemists and drug discovery researchers, but the abstract is written in a specialized manner that may limit broader accessibility.  
  Technical soundness: The method description is too brief to assess technical soundness; key details on the modified Hamiltonian, sampling efficiency, and error estimation are missing.  
  Readability for nonspecialists: The abstract is reasonably clear for a specialist audience but uses jargon (e.g., "replica exchange with dynamical scaling") without sufficient explanation for nonspecialists.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a promising method and an important finding, but the lack of quantitative results, methodological detail, and error analysis means the case is not made. A revised submission with full data and analysis could be supportive.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The abstract claims that "for the force fields used, the free energies are accurate but the entropies and enthalpies are not, with the entropic contribution being too positive."  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The claim of accurate free energies and inaccurate entropies and enthalpies is stated without any numerical values, error bars, or comparison to experimental or reference data. No benchmarks are cited, and the magnitude of the errors is not quantified.  
- **Why it matters** The central conclusion of the work rests on this comparison. Without quantitative evidence, the reader cannot judge whether the errors are significant, whether they are within expected force field limitations, or whether the method itself introduces systematic biases.  
- **Resolution test** Provide numerical values for free energies, enthalpies, and entropies for the BRD4 system, with associated uncertainties, and compare them to experimental or high-level reference data. Show that the free energy errors are within an acceptable range while the entropy and enthalpy errors exceed that range by a defined margin.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological clarity  
- **Claim pointer** The abstract describes REDS as using "two conventional simulations at different temperatures" and "a third replica... with a modified Hamiltonian that allows it to span the temperature range of the conventional replicas."  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** The description of the REDS method is too vague to evaluate its validity or novelty. Key details are missing, including the nature of the modified Hamiltonian, how the third replica spans the temperature range, how the free energy is extracted from the temperature dependence, and how the method ensures adequate sampling.  
- **Why it matters** The method is the core contribution of the work. Without a clear description, the reader cannot assess whether the approach is sound, whether it is genuinely novel, or whether it is likely to be efficient for protein-sized systems as claimed.  
- **Resolution test** Provide a detailed description of the REDS algorithm, including the Hamiltonian modification, the replica exchange scheme, the free energy estimator, and the sampling efficiency. Include a schematic or pseudocode if necessary.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Generalizability  
- **Claim pointer** The abstract states that "reproducing the entropy and enthalpy of binding appears to be a more stringent test of the force fields than reproducing the free energy."  
- **Evidence pointer** Abstract text; location not provided  
- **Concern** This conclusion is drawn from a single application to the BRD4 system. The abstract does not indicate whether the finding is specific to this system, the chosen force fields, or the REDS method, or whether it is a general property of force fields.  
- **Why it matters** The claim has broad implications for force field development and drug design. If it is based on a single case, it may be overgeneralized. The reader needs to know the scope of the evidence before accepting this conclusion.  
- **Resolution test** Apply the method to multiple protein-ligand systems with diverse binding modes and force fields. Show that the pattern of accurate free energies but inaccurate entropies and enthalpies is consistent across systems, or clearly state the limitations of the current study.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract sentence on method difficulty  
- **Evidence pointer** Abstract text; location not provided  
- **Issue** The statement that "entropy and enthalpy are roughly an order of magnitude more difficult to calculate than the free energy" is presented without justification or citation.  
- **Required correction** Provide a reference or a brief explanation for this claim, or soften the language to reflect that it is a general observation.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Use of "absolute" in the title and abstract  
- **Evidence pointer** Abstract text; location not provided  
- **Issue** The term "absolute" free energies, enthalpies, and entropies is used, but the abstract does not clarify what "absolute" means in this context, particularly whether it refers to absolute binding quantities as opposed to relative values.  
- **Required correction** Define "absolute" in the context of drug binding, or use a more standard term such as "absolute binding free energies" with a brief definition.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Force field specification  
- **Evidence pointer** Abstract text; location not provided  
- **Issue** The abstract mentions "the force fields used" but does not specify which force fields were employed.  
- **Required correction** Name the force fields in the abstract or indicate that they are specified in the full manuscript.

## Risk / unsupported claims
- The claim that free energies are accurate while entropies and enthalpies are not is unsupported by quantitative data in the abstract.
- The claim that entropy and enthalpy are more stringent tests of force fields is unsupported by evidence from multiple systems.
- The efficiency of REDS for protein-sized systems is stated but not demonstrated with performance metrics.
- The novelty of REDS relative to existing replica exchange methods is not established from the abstract alone.