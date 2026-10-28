## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary material provided
- **Shared manuscript claim summary** The authors evaluate multiple λ Dynamics perturbation schemes for predicting protein-DNA binding free energy changes (ΔΔGb) for the WRKY transcription factor binding to its W-box site (GGTCAA) versus a nonspecific sequence (GATAAA). They report that a single λ per base pair protocol achieves the fastest convergence and highest precision, and that applying this protocol to additional mutations yields ΔΔGb values that successfully rank binding affinities, suggesting potential for high-throughput screening.
- **Visible evidence base** Abstract text only; no quantitative results, statistical measures, or methodological details are available
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, numerical ΔΔGb values, convergence criteria, system setup details, force field parameters, simulation lengths, error estimates, and any comparison to experimental data

## Reviewer
- **Overall assessment** The abstract presents a potentially useful application of λ Dynamics to protein-DNA binding affinity prediction, with a clear comparative claim about perturbation schemes. However, the evidence base is limited to a brief summary, and the central claims regarding convergence, precision, and successful ranking cannot be evaluated without quantitative data and methodological detail. The work may be of interest to computational biophysicists and those studying transcription factor specificity, but the current abstract does not establish the robustness or generalizability of the approach.
- **Who would be interested in the results, and why** Computational chemists and biophysicists working on free energy methods, particularly those applying alchemical perturbation techniques to biomolecular interactions. Researchers studying transcription factor-DNA recognition and specificity, as well as developers of high-throughput screening tools for DNA binding sites, would also find the results relevant if the claims are substantiated.
- **Major strengths** The study addresses a biologically important problem, namely transcription factor binding specificity, using an advanced computational method. The comparative evaluation of different λ Dynamics perturbation schemes is a useful contribution to method development. The stated goal of high-throughput screening is practically motivated and could have broad applicability.
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
  Originality: The application of λ Dynamics to protein-DNA binding affinity prediction is not entirely novel, as λ Dynamics has been used for ligand-receptor systems, but its specific application to DNA base pair mutations in a transcription factor context may offer a new angle. The originality claim is weak from the abstract alone.  
  Scientific importance: The problem of predicting transcription factor binding affinities is significant, and a reliable computational method would be valuable. However, the abstract does not demonstrate that the method outperforms existing approaches or provides new biological insight.  
  Interdisciplinary readership: The topic bridges computational chemistry, molecular biology, and genomics, which could attract a broad audience. However, the abstract is too brief to convey the technical depth needed to engage specialists across these fields.  
  Technical soundness: Cannot be assessed from the abstract. No convergence criteria, error analysis, or validation against experimental data are provided.  
  Readability for nonspecialists: The abstract is concise and generally clear, but terms such as "λ Dynamics perturbation schemes" and "ΔΔGb" are used without sufficient context for a general reader.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially interesting study, but the absence of quantitative results and methodological detail prevents any assessment of validity or impact. A full manuscript with rigorous data would be required to evaluate the claims.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The single λ per base pair protocol demonstrated the fastest convergence and highest precision.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The abstract states that the single λ per base pair protocol showed the fastest convergence and highest precision, but no quantitative metrics are given. There is no definition of convergence, no numerical precision values, and no comparison of the schemes in terms of statistical error or computational cost.  
- **Why it matters** The central methodological claim of the paper rests on this comparison. Without quantitative evidence, the reader cannot judge whether the observed differences are meaningful or within statistical noise.  
- **Resolution test** Provide convergence plots, precision measures such as standard errors or confidence intervals, and a clear definition of convergence criteria for each scheme. Show that the differences are statistically significant.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Validation  
- **Claim pointer** Applying this protocol to additional mutations yielded ΔΔGb values that successfully ranked binding affinities.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** The claim of successful ranking is not supported by any data. There is no mention of how many mutations were tested, what the predicted values were, or how they compare to experimental measurements or known affinities.  
- **Why it matters** The practical utility of the method depends on its ability to reproduce or predict experimental binding trends. Without a comparison to experimental data or a clear benchmark, the claim of successful ranking is unsubstantiated.  
- **Resolution test** Present a table or figure comparing predicted ΔΔGb values to experimental data for a defined set of mutations, including correlation coefficients, error metrics, and the number of cases tested.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The study evaluates different λ Dynamics perturbation schemes for determining ΔΔGb of the WRKY transcription factor upon mutating its W-box binding site.  
- **Evidence pointer** Abstract; location not provided  
- **Concern** No methodological details are provided regarding the simulation setup, including force field parameters, system preparation, simulation length, number of replicas, temperature, or treatment of long-range electrostatics. Without these details, the results cannot be reproduced or assessed for technical validity.  
- **Why it matters** Reproducibility is a core requirement for computational studies. The absence of any methodological information makes it impossible to evaluate the reliability of the results or to compare them with other free energy methods.  
- **Resolution test** Provide a full methods section describing all simulation parameters, software versions, and analysis protocols. Include sufficient detail to allow independent replication.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Terminology  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "λ Dynamics perturbation schemes" is used without explanation of what distinguishes the schemes. The reader is left to infer what "single λ per base pair" means relative to other approaches.  
- **Required correction** Briefly define the perturbation schemes in the abstract or provide a schematic in the full manuscript that clarifies the differences.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Scope of mutations  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract mentions "additional mutations" but does not specify how many or what types of mutations were considered. This limits the reader's ability to gauge the breadth of the validation.  
- **Required correction** State the number and nature of the mutations tested, and clarify whether they include both strong and weak binding variants.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Context  
- **Affected element** Comparison to existing methods  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The abstract does not compare the performance of the λ Dynamics approach to other computational methods for predicting protein-DNA binding affinities, such as molecular mechanics Poisson-Boltzmann surface area or machine learning approaches.  
- **Required correction** Add a brief statement in the abstract or introduction that situates the method relative to existing tools and highlights any advantages.

## Risk / unsupported claims
- The claim that the single λ per base pair protocol achieves the fastest convergence and highest precision is unsupported without quantitative data.
- The claim that ΔΔGb values successfully ranked binding affinities is unsupported without comparison to experimental data or a defined benchmark.
- The general statement that the method demonstrates "strong potential for high-throughput screening" is speculative and not supported by the abstract alone.
- Any implication of biological insight into WRKY binding specificity is not supported by the provided text.