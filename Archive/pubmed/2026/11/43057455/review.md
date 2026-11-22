## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full methods, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors propose a systems-level framework combining transcriptomic analysis, network toxicology, immune profiling, and molecular docking to identify 80 candidate genes and 8 hub genes linking polystyrene microplastics exposure to MASH, with JUN/AP-1 as a central regulatory node and a polystyrene pentamer showing potential binding to selected transcription factors.
- **Visible evidence base** Abstract text only; no datasets, statistical outputs, or methodological details provided
- **Missing materials affecting confidence** Full methods, all figures and tables, supplementary data, statistical analysis details, docking scores, and validation results

## Reviewer
- **Overall assessment** The abstract presents a plausible integrative bioinformatics workflow that could generate useful hypotheses, but the evidence base is insufficient to evaluate the validity, robustness, or novelty of the findings. The core claims rest on computational predictions and curated database overlaps without experimental validation or clear effect sizes. The manuscript may be of interest to researchers in environmental toxicology and liver disease, but the current abstract does not establish a causal or mechanistic link between PS-MPs and MASH.
- **Who would be interested in the results, and why** Researchers studying microplastic toxicity, environmental health risk assessment, and metabolic liver disease may find the proposed framework and candidate gene list useful as a starting point for targeted mechanistic studies. The integration of public databases with transcriptomic data could appeal to those employing systems toxicology approaches.
- **Major strengths** The study addresses a timely and relevant environmental health question. The integrative use of multiple computational methods is methodologically ambitious. The identification of a focused set of hub genes and a central transcription factor provides a clear, testable hypothesis for future work.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide any statistical measures, effect sizes, or validation metrics. The molecular docking result is presented without scores or comparison to controls. The causal direction between PS-MPs exposure and MASH gene expression changes is not addressed. The relevance of a polystyrene pentamer to environmental exposure conditions is unclear.
- **Assessment against Nature-style criteria** Originality: moderate, as the combination of methods is not entirely novel but the specific application to PS-MPs and MASH is new. Scientific importance: potentially relevant but not established from the abstract alone. Interdisciplinary readership: the topic bridges environmental science and hepatology, but the abstract may not be accessible to nonspecialists due to heavy reliance on bioinformatics jargon. Technical soundness: cannot be assessed without methods and data. Readability for nonspecialists: the abstract is dense and assumes familiarity with multiple computational approaches.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a hypothesis-generating computational study, but the claims of "establishing a systems-level framework" and "structural support" are overstated relative to the evidence presented. Support would require full access to methods, statistical validation, and a more cautious interpretation of computational predictions.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim identification of 80 candidate genes and 8 hub genes linking PS-MPs to MASH.
- **Evidence pointer** Abstract only; no figures or tables provided
- **Concern** The abstract provides no statistical thresholds, enrichment scores, or validation metrics for the gene selection process. It is unclear how the 80 candidate genes were prioritized from the intersection and how the 8 hub genes were selected from protein-protein interaction analysis.
- **Why it matters** Without quantitative criteria, the gene lists could be arbitrary or driven by database biases. The core finding of the study depends on the robustness of this selection.
- **Resolution test** Provide the full methods with specific thresholds, enrichment p-values, and network centrality measures. Show that the hub gene selection is stable under different parameter choices.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The study implies a molecular association between PS-MPs exposure and MASH based on overlapping gene sets.
- **Evidence pointer** Abstract only; no exposure-response data
- **Concern** The abstract does not address whether the overlapping genes are specific to PS-MPs or shared with other environmental stressors. The direction of the association is unclear, as MASH-related gene expression changes could be unrelated to PS-MPs exposure.
- **Why it matters** The central hypothesis of the study is that PS-MPs are molecularly relevant to MASH. Without demonstrating specificity or directionality, the overlap could be coincidental.
- **Resolution test** Include a comparison against unrelated chemicals or diseases to show specificity. Provide evidence that PS-MPs exposure alters the expression of the identified genes in experimental systems.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validity of docking
- **Claim pointer** Molecular docking provided structural support for interactions between a polystyrene pentamer and selected transcription factors.
- **Evidence pointer** Abstract only; no docking scores or methods
- **Concern** The abstract reports docking results without any binding affinity values, comparison to known ligands, or assessment of docking reliability. A polystyrene pentamer is a small oligomer, and its relevance to environmental PS-MPs particles is not justified.
- **Why it matters** The docking claim is presented as supporting evidence, but without quantitative results and appropriate controls, it cannot be evaluated. Overinterpretation of weak computational binding predictions is a common pitfall.
- **Resolution test** Provide docking scores, RMSD values, and comparison to positive and negative controls. Justify the use of a pentamer as a representative model for PS-MPs.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and incremental contribution
- **Claim pointer** The study establishes a "systems-level framework" integrating multiple data types.
- **Evidence pointer** Abstract only
- **Concern** The abstract does not clarify how this framework differs from existing network toxicology or transcriptomic integration approaches. The novelty may be limited to the specific application to PS-MPs and MASH.
- **Why it matters** For a high-impact journal, the incremental contribution must be clear. If the framework is standard, the value lies in the specific findings, which are not yet validated.
- **Resolution test** Clearly state the methodological innovations and compare the framework to prior similar studies. Highlight what new biological insight is gained beyond the individual datasets.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract structure
- **Evidence pointer** Abstract text
- **Issue** The abstract is dense and lists many methods and findings without clear logical flow. The connection between immune infiltration analysis and the hub genes is stated but not explained.
- **Required correction** Restructure the abstract to clearly separate hypothesis, methods, key results, and implications. Briefly explain why immune infiltration analysis is relevant to the gene prioritization.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "establish"
- **Evidence pointer** Abstract text
- **Issue** The phrase "establish a systems-level framework" overstates what a computational study can achieve. The framework is proposed, not established.
- **Required correction** Replace "establish" with "propose" or "develop" to align with the hypothesis-generating nature of the study.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Abstract text
- **Issue** The abstract does not mention accession numbers for the GEO dataset or the version of the CTD database used. This limits reproducibility.
- **Required correction** Include database versions and accession numbers in the abstract or state that they are provided in the methods.

## Risk / unsupported claims
- The claim of "structural support" for PS-MPs interactions with transcription factors is unsupported without docking scores and controls.
- The claim that the 8 hub genes are "consistently associated" with inflammatory signaling, oxidative stress, and metabolic dysregulation is not verifiable without enrichment statistics.
- The assertion that immune infiltration analysis indicates "close association" is not quantifiable from the abstract.
- The overall implication of a molecular link between PS-MPs and MASH is not supported by causal or experimental evidence.
- The relevance of a polystyrene pentamer to environmental PS-MPs exposure is not justified.