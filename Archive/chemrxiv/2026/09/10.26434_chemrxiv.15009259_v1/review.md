## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full manuscript, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors generated 20 ns molecular dynamics (MD) trajectories for 2,502 protein–ligand complexes and evaluated five scoring function architectures trained on crystallographic structures and MD-derived frames under four sampling protocols. They report that MD-only training generally reduced predictive performance on CASF-2016 and CASF-2013 benchmarks, while augmenting crystallographic data with MD frames improved four of five architectures. Averaged across models, benchmarks, and sampling protocols, augmentation increased Pearson correlation coefficient (PCC) by 0.072 and reduced root mean square error (RMSE) by 0.165 relative to MD-only training. A nearest-neighbor analysis purportedly argues against a similarity-based explanation for the augmentation benefit. The authors conclude that MD conformations are most effective as augmentation rather than replacement for crystallographic training data.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary information were supplied
- **Missing materials affecting confidence** Full manuscript, detailed methods for MD simulation and sampling protocols, benchmark results per architecture, statistical significance tests, nearest-neighbor analysis details, and data availability verification

## Reviewer
- **Overall assessment** The abstract presents a potentially useful empirical comparison of training strategies for machine-learning scoring functions, with a clear central question and a plausible conclusion. However, the evidence base is limited to summary statistics and qualitative statements. The reported improvements are modest and lack statistical context, and the mechanistic interpretation is not fully supported by the described analyses. The work may be of interest to the computational drug discovery community, but the case for a generalizable conclusion is not established from the abstract alone.
- **Who would be interested in the results, and why** Researchers developing machine-learning scoring functions for protein–ligand binding affinity prediction and virtual screening, as well as computational chemists interested in the utility of MD-derived conformations for training data augmentation. The results could inform practical decisions about training data composition.
- **Major strengths** The study addresses a relevant and under-explored question about whether MD-derived conformations provide transferable information for training scoring functions. The scale of the dataset (2,502 complexes, 20 ns trajectories) is substantial. The comparison of multiple architectures and sampling protocols adds breadth. The inclusion of a nearest-neighbor analysis to test a competing explanation is a thoughtful design element.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of statistical significance reporting), R1-M2 (insufficient methodological detail for reproducibility), R1-M3 (nearest-neighbor analysis not described in sufficient detail to support the claim)
- **Assessment against Nature-style criteria**  
  - Originality: The question is not entirely new, but the systematic comparison across architectures and sampling protocols adds a useful dimension. The claim that augmentation outperforms replacement is a reasonable contribution, though not surprising.  
  - Scientific importance: Moderate. The findings could influence training data practices in the field, but the reported effect sizes are modest and the generalizability is uncertain.  
  - Interdisciplinary readership: Limited. The work is primarily relevant to computational chemists and machine-learning practitioners in drug discovery; it is unlikely to attract broad interdisciplinary attention.  
  - Technical soundness: Cannot be fully assessed from the abstract. The lack of statistical details and methodological specifics prevents verification of the core claims.  
  - Readability for nonspecialists: The abstract is concise and generally clear, though terms like "PCC" and "RMSE" are used without definition, which may hinder nonspecialist comprehension.
- **Recommendation posture** Currently not established from the provided evidence. The abstract reports plausible results, but the absence of statistical context, methodological detail, and supporting analyses means the core claims cannot be evaluated. A revised submission with full methods and results would be needed to assess whether the case is convincing.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** The authors claim that augmentation increased PCC by 0.072 and reduced RMSE by 0.165 relative to MD-only training, averaged across models, benchmarks, and sampling protocols.  
- **Evidence pointer** Abstract, results section; location not provided  
- **Concern** The reported improvements are presented as averages without any measure of variance, confidence intervals, or statistical significance. It is unclear whether these differences are robust across individual models, benchmarks, or sampling protocols, or whether they are driven by a subset of conditions.  
- **Why it matters** Without statistical context, the reader cannot determine whether the observed improvements are meaningful or within the range of random variation. This is critical for the central claim that augmentation is beneficial.  
- **Resolution test** Provide per-condition results with confidence intervals or significance tests (e.g., paired tests across models or bootstrapping) to demonstrate that the improvement is consistent and not due to outliers.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The authors state that they generated 20 ns MD trajectories for 2,502 complexes and evaluated five scoring function architectures under four sampling protocols.  
- **Evidence pointer** Abstract, methods section; location not provided  
- **Concern** The abstract provides no details on the MD simulation parameters, force field, water model, equilibration protocol, or how frames were selected for training. The four sampling protocols are not described, and the five scoring function architectures are not named. Without this information, the experiments cannot be reproduced or critically evaluated.  
- **Why it matters** Reproducibility is a core requirement for scientific claims. The lack of methodological detail prevents other researchers from replicating the study or assessing whether the choices made are appropriate.  
- **Resolution test** Provide a full methods section describing MD simulation setup, frame selection, sampling protocols, and architecture details, with sufficient specificity for replication.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence strength  
- **Claim pointer** The authors claim that a nearest-neighbor analysis showed the benefits of augmentation were not restricted to complexes similar to frames, arguing against a simple similarity-based explanation.  
- **Evidence pointer** Abstract, results section; location not provided  
- **Concern** The nearest-neighbor analysis is mentioned in a single sentence with no description of the method, the definition of "similarity," the threshold used, or the results. It is impossible to assess whether the analysis is appropriate or whether the conclusion follows from the data.  
- **Why it matters** This analysis is used to argue against a plausible alternative explanation for the augmentation benefit. If the analysis is flawed or misinterpreted, the mechanistic interpretation of the results is weakened.  
- **Resolution test** Describe the nearest-neighbor analysis in detail, including the similarity metric, the comparison procedure, and the quantitative results, and show that the conclusion is robust to reasonable variations in the analysis parameters.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Generalizability  
- **Claim pointer** The authors conclude that MD conformations are most effective as augmentation rather than replacement for crystallographic training data.  
- **Evidence pointer** Abstract, results section; location not provided  
- **Concern** The conclusion is based on two benchmarks (CASF-2016 and CASF-2013) and a specific set of scoring function architectures. It is unclear whether these findings would generalize to other benchmarks, other types of scoring functions, or other protein–ligand systems.  
- **Why it matters** The claim is presented as a general principle, but the evidence base is limited. Overgeneralization could mislead practitioners who apply these findings to different contexts.  
- **Resolution test** Acknowledge the scope of the findings and discuss potential limitations, or provide additional evidence from diverse benchmarks or architectures to support the generalizability of the conclusion.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract, results section  
- **Evidence pointer** Abstract, results section; location not provided  
- **Issue** The terms "PCC" and "RMSE" are used without definition. While these are standard in the field, defining them would improve accessibility for nonspecialist readers.  
- **Required correction** Define PCC and RMSE at first use, or provide a brief parenthetical explanation.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract, availability section  
- **Evidence pointer** Abstract, availability section; location not provided  
- **Issue** The data availability statement provides a Zenodo link, but it is not clear whether the link is functional or whether the data are sufficient to reproduce the training and evaluation procedures.  
- **Required correction** Clarify the contents of the deposited data and confirm that the link is accessible and complete.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Precision  
- **Affected element** Abstract, results section  
- **Evidence pointer** Abstract, results section; location not provided  
- **Issue** The phrase "controlled structural perturbations" is vague and could be interpreted in multiple ways. It is unclear what specific perturbations were applied or how they were controlled.  
- **Required correction** Specify what is meant by "controlled structural perturbations" in the context of the MD frames and training data augmentation.

## Risk / unsupported claims
- The claim that augmentation improved four of five architectures is not supported by per-architecture results, which are not provided.
- The claim that the nearest-neighbor analysis argues against a similarity-based explanation is not supported by any described methodology or quantitative outcome.
- The claim that MD conformations are most effective as augmentation rather than replacement is presented as a general conclusion but is based on a limited set of benchmarks and architectures.
- The reported average improvements in PCC and RMSE are not accompanied by any measure of uncertainty or statistical significance, making their reliability unassessable.