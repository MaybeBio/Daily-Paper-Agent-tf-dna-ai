## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors introduce EpiZoo, a 2.6 billion parameter mixture-of-experts transformer foundation model for cross-species single-cell epigenomics. The model converts single-cell epigenomic profiles into "cell sentences" integrating DNA sequence information, sequence-independent epigenomic context, and accessibility-based importance. It is pretrained on a manually curated multi-species corpus (Omni-scATAC) of approximately 20.9 million cells. The authors claim state-of-the-art performance on feature extraction, cell type annotation, and data imputation; extension to evolutionarily diverse species; support for comparative analysis of regulatory conservation and divergence in primate evolution; context-aware prioritization of somatic mutations in cancer; and prediction of cell-type-specific chromatin accessibility from DNA sequences.
- **Visible evidence base** Abstract text only; no quantitative results, benchmark details, dataset descriptions, or methodological specifications are provided
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, benchmark definitions, dataset composition and preprocessing details, model architecture specifications, training hyperparameters, evaluation protocols, and any statistical analyses

## Reviewer
- **Overall assessment** The abstract presents an ambitious and potentially impactful model that addresses a genuine gap in single-cell epigenomic foundation models, namely the limitation to individual species imposed by genomic coordinate dependence. The conceptual design, particularly the integration of DNA sequence information with epigenomic context, is timely and well motivated. However, the abstract provides no quantitative evidence to support the stated performance claims. Without access to benchmark results, dataset details, or methodological specifics, the core claims of state-of-the-art performance and broad applicability cannot be evaluated. The scope of claimed capabilities is very broad, spanning fundamental analysis tasks, evolutionary comparisons, cancer genomics, and sequence-based prediction, which raises questions about whether each claim is supported by sufficiently rigorous evaluation.
- **Who would be interested in the results, and why** Researchers in single-cell genomics, computational biology, and epigenomics would be the primary audience. The cross-species capability would interest evolutionary biologists studying regulatory divergence. The cancer mutation prioritization application would appeal to cancer genomics researchers. The sequence-to-accessibility prediction component would interest those working on regulatory genomics and sequence-based models. Given the scale of the model and the multi-species corpus, groups working on foundation models in biology would also find this relevant.
- **Major strengths** The conceptual advance of moving beyond species-specific coordinate systems by incorporating DNA sequence information is a clear and important contribution to the field. The scale of the pretraining corpus (approximately 20.9 million cells across species) is substantial. The breadth of downstream applications, from basic analysis tasks to evolutionary and clinical contexts, suggests a versatile model with potentially wide utility. The mixture-of-experts architecture is a reasonable design choice for handling multi-species heterogeneity.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4  
  - R1-M5
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria**  
  Originality: The concept of a DNA sequence-aware foundation model for cross-species single-cell epigenomics appears novel and addresses a recognized limitation of existing models. The "cell sentence" formulation is an interesting conceptual contribution.  
  Scientific importance: If the claims are substantiated, the work would be of high importance to single-cell genomics and regulatory biology. The cross-species capability and the cancer application would broaden its impact.  
  Interdisciplinary readership: The work spans machine learning, genomics, evolutionary biology, and cancer research, which would attract a broad readership if the results are clearly presented.  
  Technical soundness: Cannot be assessed from the abstract alone. No methodological details, evaluation protocols, or statistical analyses are provided.  
  Readability for nonspecialists: The abstract is reasonably accessible but uses field-specific terminology (e.g., "cell sentences," "mixture-of-experts transformer," "Omni-scATAC") without sufficient explanation for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual framing is promising, but the absence of any quantitative results or methodological detail in the abstract prevents assessment of whether the core claims are supported. The recommendation would be supportive if the full manuscript provides rigorous benchmarking, clear descriptions of the corpus and model, and appropriate statistical validation.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "EpiZoo achieves state-of-the-art performance in fundamental single-cell analysis tasks, including feature extraction, cell type annotation and data imputation"  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract claims state-of-the-art performance across three distinct tasks but provides no quantitative results, no comparison baselines, no evaluation metrics, and no description of the benchmark datasets used.  
- **Why it matters** State-of-the-art is a strong, comparative claim that requires demonstration against existing methods on standardized benchmarks. Without any numbers or methodological detail, the claim is unfalsifiable from the provided material.  
- **Resolution test** Provide benchmark results with specific metrics, comparison methods, statistical significance tests, and descriptions of evaluation datasets in the full manuscript.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "EpiZoo is pretrained on our manually curated multi-species Omni-scATAC corpus of approximately 20.9 million cells"  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The corpus is described as "manually curated" but no details are given about species composition, tissue types, data sources, quality control procedures, or how the corpus was assembled. The approximate cell count suggests possible heterogeneity in data quality that is not addressed.  
- **Why it matters** The pretraining corpus is the foundation of the model's cross-species capability. Without transparency about its composition and curation, the generalizability claims cannot be assessed, and reproducibility is compromised.  
- **Resolution test** Provide a detailed description of the corpus, including species list, number of cells per species, data sources, preprocessing and quality control steps, and any filtering criteria.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "Its sequence-aware architecture enables extension to evolutionarily diverse species, and supports comparative analysis of regulatory conservation and divergence during primate evolution"  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The abstract claims the model can be extended to evolutionarily diverse species and supports comparative evolutionary analyses, but no results are presented demonstrating these capabilities. No species are named, no evolutionary analyses are described, and no findings are reported.  
- **Why it matters** Extension to new species and evolutionary comparative analysis are central claims of the work. Without demonstration, these remain aspirations rather than validated capabilities.  
- **Resolution test** Provide specific examples of model application to species not seen in pretraining, and present concrete comparative analyses of regulatory conservation and divergence with appropriate evolutionary metrics.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** "EpiZoo enables context-aware prioritization of somatic mutations in cancer and prediction of cell-type-specific chromatin accessibility from DNA sequences across genomic regions and species"  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** Two additional application domains are claimed, cancer mutation prioritization and sequence-based accessibility prediction, but no results, case studies, or performance metrics are provided for either.  
- **Why it matters** These are substantial claims with potential clinical and translational relevance. Without evidence, the reader cannot determine whether these applications are validated or merely plausible extensions of the model.  
- **Resolution test** Provide evaluation results for both applications, including relevant benchmarks, comparison to existing methods, and appropriate validation on independent datasets.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical transparency  
- **Claim pointer** "EpiZoo converts million-dimensional single-cell epigenomic profiles from diverse species into compact cell sentences that integrate DNA-encoded regulatory information, sequence-independent epigenomic context and accessibility-based importance"  
- **Evidence pointer** Abstract only; location not provided  
- **Concern** The "cell sentence" formulation is a central conceptual contribution, but the abstract does not explain how this conversion is performed, what the components represent, how the integration is achieved, or how the model architecture implements this design.  
- **Why it matters** The novelty of the work rests substantially on this design. Without technical detail, the contribution cannot be evaluated or reproduced, and the relationship to existing representation learning approaches in single-cell genomics is unclear.  
- **Resolution test** Provide a detailed description of the cell sentence construction, the model architecture, and how each component (DNA sequence, epigenomic context, accessibility importance) is encoded and integrated.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Terminology  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The term "cell sentences" is introduced without definition or analogy, which may confuse readers unfamiliar with natural language processing analogies in genomics.  
- **Required correction** Define the term explicitly upon first use, explaining how the components map to the epigenomic data.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Model scale  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The model is stated to contain 2.6 billion parameters, but no information is given about training compute, hardware, or training time, which is relevant for assessing feasibility and reproducibility.  
- **Required correction** Include training infrastructure details and computational cost in the methods.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Precision  
- **Affected element** Dataset description  
- **Evidence pointer** Abstract; location not provided  
- **Issue** The corpus is described as containing "approximately 20.9 million cells" but the species composition and balance across species are not mentioned, which affects interpretation of cross-species performance.  
- **Required correction** Provide a breakdown of cell counts by species and note any class imbalance or its handling.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Accessibility  
- **Affected element** Resource availability  
- **Evidence pointer** Abstract; location not provided  
- **Issue** No mention is made of code, model weights, or data availability, which is important for a resource-intensive foundation model intended for community use.  
- **Required correction** State availability of code, pretrained model, and data access conditions.

## Risk / unsupported claims
- State-of-the-art performance on feature extraction, cell type annotation, and data imputation is unsupported by any quantitative evidence in the abstract.
- Extension to evolutionarily diverse species is claimed but not demonstrated with any results.
- Comparative analysis of regulatory conservation and divergence during primate evolution is claimed but no findings are presented.
- Context-aware prioritization of somatic mutations in cancer is claimed but no results or validation are provided.
- Prediction of cell-type-specific chromatin accessibility from DNA sequences is claimed but no performance metrics are given.
- The quality and composition of the Omni-scATAC corpus cannot be assessed from the abstract.
- The "cell sentence" representation and its implementation in the model architecture are not described in sufficient detail to evaluate the novelty or correctness of the approach.