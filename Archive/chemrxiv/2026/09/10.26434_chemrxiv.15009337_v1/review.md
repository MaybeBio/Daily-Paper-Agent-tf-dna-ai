## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose ProtMutMap, a network-based method that integrates multiple free energy perturbation (FEP) pathways to predict binding free energy changes (ΔΔG) for protein variants with multiple mutations. The method is claimed to outperform additive approximation, stepwise FEP, and Rosetta flex ddG on a dataset of 7 protein complex systems from SKEMPI2, achieving an RMSE of 1.13 kcal/mol.
- **Visible evidence base** Abstract text only; no numerical tables, figures, or methodological details beyond those summarized in the abstract
- **Missing materials affecting confidence** Full methods, dataset composition and filtering criteria, definition of the 30 evaluation points, error bars or uncertainty estimates, statistical significance tests, computational cost analysis, and any comparison details for Rosetta flex ddG

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting approach to a recognized problem in computational protein engineering, namely the nonadditivity of multiple mutations at protein-protein interfaces. The network formulation that integrates multiple FEP pathways is a plausible methodological contribution. However, the evidence provided in the abstract is insufficient to evaluate the robustness of the claimed performance. Key details about the dataset, evaluation protocol, and statistical significance are absent. The claim of superiority over Rosetta flex ddG is particularly difficult to assess without knowing the comparison conditions.
- **Who would be interested in the results, and why** Computational biophysicists and protein engineers working on affinity maturation, variant effect prediction, and rational protein design would be interested. The method addresses a practical bottleneck in predicting the combined effect of multiple mutations, which is directly relevant to antibody engineering and protein-protein interaction design.
- **Major strengths** The problem addressed is well-defined and practically important. The network-based integration of multiple FEP pathways is a novel conceptual framing that departs from the standard additive or sequential approaches. The use of Huber loss for simultaneous estimation is a reasonable robust regression choice. The comparison against both additive and stepwise baselines, as well as Rosetta flex ddG, indicates awareness of the relevant benchmark landscape.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria**  
  Originality: The network-based multi-pathway integration appears conceptually novel, though the abstract does not clarify how it differs from existing multi-state or alchemical network methods in sufficient detail.  
  Scientific importance: The problem of nonadditive multiple mutations is of high importance for protein engineering, and a reliable predictive method would be valuable.  
  Interdisciplinary readership: The work is likely to appeal to computational chemists, structural biologists, and protein engineers, but the abstract is written in a way that assumes familiarity with FEP terminology, which may limit accessibility.  
  Technical soundness: Cannot be fully assessed from the abstract. The reported RMSE of 1.13 kcal/mol is presented without uncertainty or significance testing, and the evaluation protocol is underspecified.  
  Readability for nonspecialists: The abstract is concise but dense; the network concept is introduced clearly, but the evaluation details are not accessible to a broad audience.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual approach is promising, but the abstract alone does not provide sufficient methodological detail or statistical rigor to support the performance claims. A full manuscript with detailed methods, dataset description, and significance testing would be required to assess whether the case can be made.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "ProtMutMap achieved a root mean squared error (RMSE) of 1.13 kcal/mol, lower than that of either comparison method."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract reports a single RMSE value without any measure of uncertainty, confidence intervals, or statistical significance testing against the comparison methods. It is unclear whether the difference between 1.13 kcal/mol and the RMSEs of the additive or stepwise methods is meaningful given the likely variance across the 30 evaluation points and 7 systems.  
- **Why it matters** Without significance testing or error bars, the claimed improvement could be within noise. The reader cannot determine whether the observed difference is robust or an artifact of a small or biased evaluation set.  
- **Resolution test** Provide per-system and per-evaluation-point errors, confidence intervals or bootstrapped estimates, and a statistical test (e.g., paired t-test or Wilcoxon signed-rank test) comparing ProtMutMap against each baseline.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Dataset and evaluation protocol  
- **Claim pointer** "using a multiple-mutation dataset comprising 7 protein complex systems derived from SKEMPI2" and "at 30 evaluation points, including intermediate variants"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not specify how the 7 systems were selected, how the 30 evaluation points were defined, what constitutes an "intermediate variant," or how experimental ΔΔG values were obtained and processed. The criteria for including or excluding mutations and the balance of the dataset across systems are unknown.  
- **Why it matters** The generalizability of the method depends on the representativeness and quality of the evaluation dataset. If the 7 systems are biased toward certain complex types or mutation patterns, the reported performance may not transfer to other systems. The definition of evaluation points directly affects the comparability of the RMSE across methods.  
- **Resolution test** Provide a detailed description of dataset construction, including selection criteria, mutation types, number of variants per system, and the exact definition of the 30 evaluation points. Report the distribution of errors across systems and variants.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Comparison fairness  
- **Claim pointer** "ProtMutMap also yielded lower prediction errors than Rosetta flex ddG."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The comparison with Rosetta flex ddG is mentioned without any detail on how it was run, whether the same evaluation points were used, whether the same input structures and protonation states were employed, or whether any parameter optimization was performed for the baseline. The abstract does not report the actual error value for Rosetta flex ddG.  
- **Why it matters** A fair comparison requires identical evaluation conditions and transparent reporting of baseline performance. Without these details, the claim of superiority over Rosetta flex ddG cannot be verified, and the reader cannot judge whether the comparison is meaningful.  
- **Resolution test** Report the RMSE (or other metrics) for Rosetta flex ddG on the same evaluation points, describe the exact protocol used, and state whether any tuning was performed. Ideally, include a per-system breakdown.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Methodological clarity  
- **Claim pointer** "ProtMutMap simultaneously estimates the binding ΔΔG of each variant from all edge values using Huber loss."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not explain how the network is constructed, how edge values are computed, how the Huber loss is applied to the network, or how the method handles cycles, inconsistent edge values, or missing edges. The computational cost relative to stepwise FEP is also not mentioned.  
- **Why it matters** The methodological novelty is the core of the contribution, but the abstract provides insufficient detail to understand the algorithm or to assess its feasibility and scalability. Without this information, the reader cannot evaluate whether the method is practical for larger mutation sets or more complex systems.  
- **Resolution test** Provide a clear description of the network construction, the FEP protocol for edge values, the optimization procedure, and a complexity analysis. Include a schematic figure if possible.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Reporting completeness  
- **Affected element** Dataset description  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract states "7 protein complex systems derived from SKEMPI2" but does not name the systems or indicate their diversity in terms of complex type, binding affinity range, or mutation types.  
- **Required correction** List the 7 systems and provide basic characteristics in the full manuscript, and mention this in the abstract if space permits.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Metric selection  
- **Affected element** Performance evaluation  
- **Evidence pointer** Abstract, location not provided  
- **Issue** Only RMSE is reported. Other metrics such as Pearson or Spearman correlation, mean absolute error, or the fraction of predictions within a given threshold (e.g., 1 kcal/mol) would provide a more complete picture of predictive performance.  
- **Required correction** Report additional metrics in the full manuscript, and consider including a scatter plot of predicted versus experimental ΔΔG.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** "Multiple-mutation networks"  
- **Evidence pointer** Title and abstract  
- **Issue** The term "multiple-mutation networks" is used in the title but not defined in the abstract. It is unclear whether this refers to the network of variants or to a network representation of mutations themselves.  
- **Required correction** Define the term clearly in the introduction or abstract, and ensure consistent usage throughout the manuscript.

## Risk / unsupported claims
- The claim that ProtMutMap outperforms both additive approximation and stepwise FEP is unsupported without statistical significance testing and per-system error reporting.
- The claim of superiority over Rosetta flex ddG is unsupported because the comparison protocol is not described and the baseline error value is not reported.
- The generalizability of the method to other protein systems is not assessable from the abstract alone, given the limited description of the 7 systems and 30 evaluation points.
- The methodological claim of "integrating information from multiple pathways" improving predictions is plausible but not verifiable without a detailed description of the network construction and the FEP protocol.