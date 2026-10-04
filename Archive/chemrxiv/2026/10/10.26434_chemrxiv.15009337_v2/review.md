## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose ProtMutMap, a network-based method that integrates multiple free energy perturbation (FEP) pathways to predict binding free energy changes (ΔΔG) for protein variants with multiple mutations. The method is claimed to outperform additive approximation, stepwise approaches, and Rosetta flex ddG on a dataset of 7 protein complex systems from SKEMPI2, achieving an RMSE of 1.13 kcal/mol.
- **Visible evidence base** Abstract text only; no numerical details beyond the reported RMSE, no dataset composition, no statistical analysis, no methodological description
- **Missing materials affecting confidence** Full manuscript, methods section, figures, tables, dataset details, error bars or confidence intervals, computational details, and comparison protocols

## Reviewer
- **Overall assessment** The abstract presents a potentially useful idea for addressing nonadditive effects in multiple-mutation ΔΔG prediction by integrating multiple FEP pathways through a network formulation. However, the evidence provided in the abstract is insufficient to evaluate the validity, robustness, or generalizability of the claimed improvements. The reported single RMSE value, without variance, statistical testing, or detailed comparison conditions, does not establish the superiority of ProtMutMap over existing methods.
- **Who would be interested in the results, and why** Computational biophysicists and structural biologists working on protein engineering, drug design, and alchemical free energy calculations would be interested. The method addresses a known limitation of additive models for multiple mutations, which is relevant for antibody engineering and protein design applications.
- **Major strengths** The conceptual framing of using a network of intermediate variants to integrate multiple FEP pathways is a reasonable and potentially novel approach to capture nonadditive effects. The comparison against both additive and stepwise baselines, as well as Rosetta flex ddG, is appropriate in principle.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "ProtMutMap achieved a root mean squared error (RMSE) of 1.13 kcal/mol, lower than that of either comparison method."
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract reports a single RMSE value without any measure of uncertainty, statistical significance, or per-system breakdown. It is unclear whether the improvement over comparison methods is consistent across the 7 systems or driven by a subset. No confidence intervals, standard deviations, or paired statistical tests are reported.
  - **Why it matters** A single aggregate metric cannot establish that the method reliably outperforms baselines. Without variance or per-system results, the claimed improvement may not be robust or generalizable.
  - **Resolution test** Provide per-system RMSE values, confidence intervals or bootstrapped estimates, and a paired statistical test (e.g., Wilcoxon signed-rank) comparing ProtMutMap against each baseline.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological transparency
  - **Claim pointer** "ProtMutMap simultaneously estimates the binding ΔΔG of each variant from all edge values using Huber loss."
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract does not describe how the network is constructed, how edge values are computed, how Huber loss is applied to the network estimation, or how the method handles cycles, inconsistent edge values, or missing edges. The computational cost and convergence properties are also not mentioned.
  - **Why it matters** Without methodological detail, the approach cannot be reproduced or assessed for correctness. The network formulation may introduce biases or artifacts that are not apparent from the abstract.
  - **Resolution test** Provide a full methods description including network construction, edge weighting, optimization procedure, and handling of inconsistent or missing FEP values.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Dataset and comparison validity
  - **Claim pointer** "using a multiple-mutation dataset comprising 7 protein complex systems derived from SKEMPI2" and "ProtMutMap also yielded lower prediction errors than Rosetta flex ddG."
  - **Evidence pointer** Abstract, location not provided
  - **Concern** The abstract does not specify the number of variants, the range of mutation counts, the distribution of mutation types, or the selection criteria for the 7 systems. The comparison with Rosetta flex ddG is mentioned without any numerical result or description of how the comparison was performed (e.g., same evaluation points, same FEP protocol).
  - **Why it matters** A small dataset of 7 systems may not be representative. The Rosetta flex ddG comparison could be confounded by different input preparation, force fields, or evaluation protocols. Without these details, the external validity of the claim is unclear.
  - **Resolution test** Report dataset composition, mutation count distribution, and a detailed description of the Rosetta flex ddG comparison protocol including input structures, parameters, and evaluation points.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Terminology
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The term "multiple-mutation networks" in the title is not defined in the abstract. The relationship between the network structure and the biological or physical meaning of the nodes and edges is not explained.
  - **Required correction** Define the network components explicitly in the abstract or provide a brief schematic description.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reporting completeness
  - **Affected element** Evaluation points
  - **Evidence pointer** Abstract, location not provided
  - **Issue** The abstract states "30 evaluation points, including intermediate variants" but does not clarify how these points are distributed across the 7 systems or whether they include single-mutation variants as controls.
  - **Required correction** Specify the number of evaluation points per system and the composition of the evaluation set.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Software availability
  - **Evidence pointer** Abstract, location not provided
  - **Issue** No mention of code availability, input data preparation, or force field parameters used for FEP calculations.
  - **Required correction** State where the code and data will be made available and list the FEP protocol parameters.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3. The current abstract does not provide sufficient evidence to establish that ProtMutMap reliably outperforms existing methods or that the network-based approach is methodologically sound.
- **Assessment against Nature-style criteria**  
  Originality: The network-based integration of multiple FEP pathways is a conceptually distinct idea, though its novelty relative to existing multi-state or pathway-sampling methods cannot be fully assessed from the abstract.  
  Scientific importance: Addressing nonadditive effects in multiple-mutation ΔΔG prediction is relevant for protein engineering, but the importance is not yet demonstrated with robust evidence.  
  Interdisciplinary readership: The topic is of interest to computational biologists and biophysicists, but the abstract is too technical for a broad interdisciplinary audience without additional context.  
  Technical soundness: Cannot be evaluated from the abstract alone; the reported single RMSE is insufficient.  
  Readability for nonspecialists: The abstract assumes familiarity with FEP, ΔΔG, and SKEMPI2, which limits accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The idea is promising, but the abstract alone does not provide enough detail or statistical support to justify publication. A full manuscript with detailed methods, per-system results, and statistical analysis would be required to assess the claims.

## Risk / unsupported claims
- The claim that ProtMutMap outperforms additive approximation and stepwise methods is unsupported without variance or statistical testing.
- The claim that ProtMutMap outperforms Rosetta flex ddG is unsupported as no numerical comparison is provided.
- The claim that integrating multiple pathways "improves" predictions is a causal statement not supported by the correlational evidence presented.
- The generalizability of the method beyond the 7 systems is not assessable from the abstract.