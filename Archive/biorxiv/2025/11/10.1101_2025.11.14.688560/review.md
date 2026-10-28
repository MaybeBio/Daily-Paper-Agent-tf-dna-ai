## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report a meta-transcriptomic analysis of drought-responsive gene expression in cultivated *Vitis vinifera* and two hybrid rootstocks (M4 and 101-14), identifying 4,617 consistently drought-responsive genes across more than twenty drought-control comparisons. They constructed gene regulatory networks integrating transcription factor binding motif analysis with random forest-based machine learning, and identified key transcription factors (ABF2, MYB30A, an uncharacterized HMG-box domain protein) as central regulators. The network is described as hierarchically organized, with top-ranking TFs acting as positive regulators and lower-hierarchy TFs showing inverse expression relationships with predicted targets.
- **Visible evidence base** Abstract text only; no datasets, statistical details, network figures, or validation results were provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, supplementary data, statistical details, validation experiments, and any code or data availability statements

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting bioinformatics-driven approach to identifying drought-responsive regulatory networks in grapevine. The scale of the meta-analysis (more than twenty comparisons) and the integration of motif analysis with machine learning are commendable. However, the abstract alone does not provide sufficient evidence to evaluate the technical soundness of the analysis, the robustness of the network inference, or the biological validity of the proposed regulatory relationships. Several claims, particularly regarding the directionality of TF regulation and the hierarchical network architecture, are stated without supporting quantitative or experimental evidence. The work may be of interest to the grapevine and plant stress biology communities, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in grapevine genomics and breeding, plant abiotic stress physiology, and computational regulatory network inference would be interested. The identification of candidate transcription factors for drought tolerance could inform breeding and biotechnological strategies, and the methodological approach may be relevant to those working on meta-transcriptomic analyses in other crops.
- **Major strengths** The use of a meta-transcriptomic approach across multiple cultivars and rootstocks is a strength, as it may improve generalizability over single-experiment studies. The integration of TF binding motif analysis with random forest-based network inference is a modern and potentially powerful combination. The focus on identifying consistent drought-responsive genes across diverse genetic backgrounds is biologically meaningful.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
- **Technical failings that need to be addressed before the case is established** The abstract does not report any statistical thresholds, cross-validation procedures, or independent validation of the network predictions. The claim of "directional" TF activity is not supported by any experimental evidence, and the directionality of regulation inferred from expression correlation alone is not established. The absence of any performance metrics for the random forest models or motif enrichment significance is a technical gap.
- **Assessment against Nature-style criteria** 
  - Originality: The combination of meta-transcriptomics with machine learning-based network inference in grapevine is somewhat novel, but the abstract does not clearly differentiate this from prior network inference studies in plants.
  - Scientific importance: Drought tolerance in grapevine is of practical importance, and identifying regulatory hubs could have applied value. However, the abstract does not demonstrate that the identified TFs are functionally validated or that the network provides new biological insight beyond known ABA signaling components.
  - Interdisciplinary readership: The work sits at the interface of genomics, computational biology, and plant physiology, which could attract a broad readership, but the abstract is written in a way that is accessible primarily to specialists.
  - Technical soundness: Not assessable from the abstract. No details on data processing, normalization, batch effect correction, network inference parameters, or validation are provided.
  - Readability for nonspecialists: The abstract is reasonably clear but uses jargon (e.g., "meta-transcriptomic," "random forest-based regulatory network generation") without sufficient explanation for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is promising but lacks the technical detail and validation needed to support the core claims. A full manuscript with methods, figures, and validation would be required to assess whether the case can be made.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to have identified a core set of 4,617 drought-responsive genes that were "consistently misregulated across multiple experimental conditions" using more than twenty drought-control comparisons.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not specify the criteria used to define "consistently" differentially expressed genes. No thresholds for fold change, statistical significance, or direction of change are given. It is unclear how heterogeneity across datasets (e.g., different platforms, tissue types, drought severities, time points) was handled, and whether batch effects or technical variation were addressed.
- **Why it matters** The core gene set is the foundation for all downstream network inference. If the criteria for inclusion are not rigorous or are biased by dataset composition, the entire network and the identified TFs could be artifacts. Without this information, the reliability of the 4,617-gene set cannot be evaluated.
- **Resolution test** Provide a detailed methods section describing data collection, normalization, statistical testing, and meta-analysis procedures. Report the exact thresholds used and the number of genes passing each filter. Include a sensitivity analysis showing how the core gene set changes with different thresholds.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that gene regulatory networks were constructed by integrating genome-wide TF binding motif analysis with random forest-based regulatory network generation, and that key TFs (ABF2, MYB30A, an HMG-box protein) were identified as central regulators.
- **Evidence pointer** Abstract only; location not provided
- **Concern** No details are provided on how the random forest models were trained, what features were used, how the motif analysis was integrated, or how "central regulator" status was defined. There is no mention of cross-validation, model performance metrics, or how false positives were controlled. The choice of these three TFs as central regulators appears arbitrary without supporting network statistics.
- **Why it matters** Machine learning-based network inference is highly sensitive to input features and parameters. Without performance metrics and validation, the identified TFs may not be true regulators but rather statistical artifacts. The claim of centrality requires quantitative support, such as degree or betweenness measures, and ideally experimental validation.
- **Resolution test** Provide a full description of the network inference pipeline, including feature selection, model training, hyperparameter tuning, and validation. Report performance metrics (e.g., AUC, precision-recall) and network statistics for the identified TFs. Include independent validation, such as ChIP-seq, DAP-seq, or expression perturbation experiments, to confirm regulatory relationships.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Biological validity
- **Claim pointer** The authors claim that top-ranking TFs were "primarily identified as positive regulators of their target genes, while lower-hierarchy TFs exhibited inverse expression relationships with their predicted targets," and that the network exhibits a "hierarchical organization architecture" linked to ABA signaling.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The directionality of regulation (positive vs. inverse) is inferred from expression correlations, which do not establish causality. The claim of hierarchy is not supported by any network topology analysis or functional validation. The link to ABA signaling is based on homology to known ABA-related TFs, but no direct evidence is provided that these TFs actually participate in ABA signaling in grapevine.
- **Why it matters** The central biological claim of the paper is that the network is hierarchically organized and directionally regulated. If this is based solely on correlation, it is a weak inference. The ABA link is plausible but speculative without experimental evidence. Overstating these findings could mislead the field.
- **Resolution test** Provide network topology analyses (e.g., directed acyclic graph testing, motif analysis) that support hierarchy. Use experimental approaches (e.g., overexpression or knockout lines, transcriptome profiling after perturbation) to demonstrate that the predicted TFs regulate their targets in the claimed direction. Provide direct evidence of ABA involvement, such as ABA treatment assays or mutant analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and data availability
- **Claim pointer** The abstract implies that the analysis is based on publicly available datasets (meta-transcriptomic), but no data accession numbers, code availability, or software versions are mentioned.
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract does not state which datasets were used, how they were accessed, or whether the analysis code is available. Without this information, the analysis cannot be reproduced or independently verified.
- **Why it matters** Reproducibility is a core requirement for computational studies. The lack of data and code availability undermines confidence in the results and prevents the community from building on this work.
- **Resolution test** Provide a data availability statement with accession numbers for all datasets used, and a code availability statement with a link to a public repository containing the analysis scripts and any custom software.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract, "misregulated" (location not provided)
- **Issue** The term "misregulated" is imprecise. It is unclear whether this means differentially expressed, dysregulated, or something else.
- **Required correction** Replace with "differentially expressed" or "consistently altered in expression" for clarity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract scope
- **Evidence pointer** Abstract, "more than twenty drought-control comparisons" (location not provided)
- **Issue** The abstract does not specify the number of unique datasets or the diversity of conditions (e.g., rootstock types, tissue types, drought duration). This makes it difficult to assess the generalizability of the findings.
- **Required correction** Provide a brief summary of the datasets used, including the number of independent studies, tissue types, and drought conditions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Abstract claim on TF families
- **Evidence pointer** Abstract, "several TF families represented, each potentially operating at distinct regulatory tiers" (location not provided)
- **Issue** The phrase "potentially operating" is speculative and does not indicate whether this was tested or is a hypothesis.
- **Required correction** Clarify whether this is a hypothesis or a finding, and if tested, provide the supporting evidence.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract language
- **Evidence pointer** Abstract, "random forest-based regulatory network generation employing machine learning techniques" (location not provided)
- **Issue** The phrase is redundant ("machine learning techniques" is implied by "random forest") and could be simplified for readability.
- **Required correction** Revise to "random forest-based regulatory network inference" or similar.

## Risk / unsupported claims
- The claim of 4,617 consistently drought-responsive genes is unsupported without statistical thresholds and dataset details.
- The identification of ABF2, MYB30A, and an HMG-box protein as central regulators is unsupported without network statistics or validation.
- The claim of directional TF activity (positive vs. inverse regulation) is unsupported; correlation does not establish directionality.
- The claim of hierarchical network organization is unsupported without topology analysis.
- The link to ABA signaling is speculative and based on homology only.
- The general statement that the findings "offer novel insights" and "provide key candidate regulators" is not evaluable without evidence of functional significance.