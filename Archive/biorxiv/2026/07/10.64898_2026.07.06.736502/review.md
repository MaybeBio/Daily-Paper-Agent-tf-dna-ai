## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, supplementary materials)
- **Assessment boundary** Scientific validity, technical soundness, methodological rigor, clarity of claims, and alignment with stated contributions
- **Shared manuscript claim summary** The authors present EpiBinder, a multimodal deep-learning framework that integrates DNA sequence with base-resolution epigenetic features (CpG, CHG, CHH methylation and DNase I hypersensitivity) to predict transcription factor binding in a cell-type-specific manner. They claim consistent improvements over sequence-only baselines across GM12878, K562, and HepG2 cell lines, and demonstrate interpretability through motif discovery, TF-TF interaction perturbation analysis, and methylation sensitivity mapping.
- **Visible evidence base** Main text tables (Tables 1-4), figures referenced (Figures 2-7), supplementary tables (S5-S11), supplementary figures (8-12), methods descriptions, and data availability statement
- **Missing materials affecting confidence** Actual figures and tables are not provided in the manuscript text; supplementary tables and figures referenced but not included; no code repository link beyond a Zenodo archive; no hyperparameter details for the transformer backbone; no explicit description of the train/validation/test split ratio beyond chromosome-based separation

## Reviewer
- **Overall assessment** The manuscript presents a timely and potentially valuable contribution to the field of regulatory genomics by explicitly integrating epigenetic context into TF-binding prediction. The core idea of combining sequence with base-resolution methylation and chromatin accessibility is well motivated and the reported performance gains are encouraging. However, the manuscript as provided has several critical gaps that prevent full evaluation: the actual results tables and figures are not visible, the statistical comparison methodology is incompletely described, and several claims in the discussion go beyond what the presented evidence can support. The interpretability analyses are thoughtful and well-designed, but their conclusions require more rigorous validation. The manuscript would benefit from clearer reporting of experimental details and a more cautious framing of some claims.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, TF binding prediction, and deep learning applications to genomics would be the primary audience. Researchers studying cell-type-specific gene regulation, epigenetic mechanisms of TF occupancy, and those developing interpretable AI models for biology would also find value. The methylation sensitivity analysis and mQTL integration could interest researchers in epigenetic epidemiology and EWAS interpretation.

- **Major strengths** The manuscript addresses a genuine gap in the field by moving beyond sequence-only models to explicitly incorporate epigenetic context. The design of four complementary evaluation tasks (prediction, cross-cell transfer, motif discovery, TF-TF interaction perturbation) is comprehensive and well-structured. The use of auPRC rather than auROC is methodologically appropriate for imbalanced ChIP-seq data. The interpretability framework, particularly the perturbation-based TF-TF interaction analysis and the SORT1 enhancer case study with MPRA validation, represents a thoughtful approach to model interrogation. The cross-cell transfer analysis with Cohen's d provides a useful quantitative framework for understanding generalization.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims consistent improvements over sequence-only baselines across all evaluated cell lines, with up to 10% improvement in auPRC.
- **Evidence pointer** Table 1, Figure 2, Section 3.1
- **Concern** The actual results tables and figures are not included in the provided manuscript text. Table 1, which is central to the main performance claim, is referenced but its contents are not visible. Similarly, Figure 2, which is supposed to show the distribution of auPRC values and the relationship between data availability and performance, is not provided. Without access to these data, the core claim of improved predictive performance cannot be verified or evaluated.
- **Why it matters** The primary contribution of the manuscript is the claimed improvement in TF-binding prediction. If the actual performance data are not available for review, the central thesis of the paper cannot be assessed.
- **Resolution test** Provide the actual tables and figures with numerical values for all cell lines and baselines, including confidence intervals or significance tests for the reported improvements.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript states that EpiBinder "consistently outperforms" sequence-only baselines and reports specific percentage improvements.
- **Evidence pointer** Section 2.3, Section 3.1, Table 1
- **Concern** The statistical comparison methodology is incompletely described. The manuscript mentions that training and testing sets were split by chromosomes, but does not describe how many independent training runs were performed, whether statistical significance was assessed across runs, or what the variance of the performance estimates is. The claim of "consistent" improvement requires some measure of variability or statistical testing. Additionally, the comparison to baselines such as DeepSEA, DNABERT, BigBird, and HyenaDNA is described, but the specific training protocols for these baselines are not fully detailed.
- **Why it matters** Without proper statistical characterization, the reported performance improvements could be within the range of random variation, particularly given the heterogeneity in TF binding data quality and quantity.
- **Resolution test** Report the number of independent training runs, provide standard deviations or confidence intervals for all performance metrics, and describe the statistical tests used to establish significance of improvements.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological clarity
- **Claim pointer** The manuscript claims that EpiBinder provides "base-level attribution maps that enable systematic interrogation of regulatory context, including candidate methylation-sensitive loci, contextual motif dependencies, and putative TF-TF interactions."
- **Evidence pointer** Section 2.3, Section 3.3, Section 3.4, Section 3.5
- **Concern** The interpretability analyses are described at a high level, but several methodological details are missing. For the TF-TF interaction perturbation analysis, the manuscript states that motifs are randomized "through nucleotide randomization" but does not specify the exact randomization procedure (e.g., uniform random nucleotide selection, dinucleotide shuffling, or preservation of GC content). The choice of 500 bp window for motif pair enumeration is not justified. For the methylation sensitivity analysis, the threshold for "high-sensitivity" is described as "top quantile" but the specific quantile is not stated. The functional enrichment analysis methodology is described but the specific background model and multiple testing correction details are incomplete.
- **Why it matters** These interpretability analyses are a key differentiator of the manuscript. Without precise methodological details, the results cannot be reproduced or properly evaluated for potential artifacts.
- **Resolution test** Provide complete methodological details for all interpretability analyses, including exact randomization procedures, parameter choices with justification, and complete statistical testing frameworks.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Claim overreach
- **Claim pointer** The discussion states that "these results position EpiBinder as a practical framework for modeling and exploring the local regulatory grammar underlying cell-type-specific TF occupancy" and questions "the prevailing emphasis on extending receptive fields to hundreds of kilobases or to the megabase scale."
- **Evidence pointer** Section 4, Discussion
- **Concern** The discussion makes broad claims about the relative importance of local context versus long-range sequence information based on a comparison to models that were not designed to capture long-range interactions in the same way as models like Enformer or AlphaGenome. The comparison to DeepSEA, DNABERT, BigBird, and HyenaDNA is appropriate for benchmarking, but the conclusion that "increasing sequence span alone offers limited benefit" is a strong claim that would require direct comparison to long-context models on the same tasks. Additionally, the claim that EpiBinder captures "local regulatory grammar" is supported by the interpretability analyses, but the generalization of this to a general principle about TF binding prediction is premature.
- **Why it matters** The discussion frames the contribution in a way that may overstate the implications of the results. This could mislead readers about the state of the field and the relative merits of different modeling approaches.
- **Resolution test** Either temper the claims in the discussion to be more specifically about the models compared in this study, or add direct comparisons to long-context models to support the broader claim.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Validation of biological claims
- **Claim pointer** The manuscript claims that the model "captures context-dependent binding logic, including motif-pair dependencies that are consistent with both cooperative and competitive effects" and that methylation-sensitive loci "may function as methylation-controlled regulatory regions."
- **Evidence pointer** Section 3.4, Section 3.5, Figure 5, Figure 6, Figure 7
- **Concern** The biological interpretations derived from the in silico analyses are presented without experimental validation. While the SORT1 enhancer analysis with MPRA data provides some external validation, the broader claims about TF-TF interactions and methylation-controlled regulatory regions are based solely on model predictions. The manuscript does not discuss potential confounding factors, such as the correlation between methylation and chromatin accessibility, or the possibility that the model may be learning indirect associations rather than direct causal relationships.
- **Why it matters** The interpretability analyses are presented as providing biological insight, but without validation or discussion of limitations, readers may overinterpret the model's attributions as causal mechanisms.
- **Resolution test** Add a discussion of the limitations of in silico interpretability analyses, and either provide additional validation (e.g., comparison to known biological interactions, experimental validation of a subset of predictions) or temper the biological claims.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.3, Model Validation
- **Evidence pointer** Section 2.3
- **Issue** The description of the training procedure mentions "approximately 2.2 million training samples" and "227,512 held-out samples" but does not specify the number of TF tasks per cell line or the total number of genomic windows used. The relationship between the number of samples and the number of TF labels is unclear.
- **Required correction** Clarify the dataset composition, including the number of TF tasks per cell line, the total number of genomic windows, and how the training/validation/test split was performed across chromosomes.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.2, Model Architecture
- **Evidence pointer** Section 2.2, Table S7
- **Issue** The model architecture is described at a high level, but key hyperparameters (number of layers, hidden dimensions, attention heads, learning rate, batch size, etc.) are not specified in the main text. While Table S7 is referenced, it is not included in the provided material.
- **Required correction** Provide the full architecture details, either in the main text or by ensuring the supplementary table is accessible and complete.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 3.3, Jaccard Overlap Score
- **Evidence pointer** Section 3.3, Section S2.4
- **Issue** The Jaccard Overlap Score (JOS) is introduced as a new metric, but its interpretation is not immediately intuitive. The description states that values near 0 indicate collapse onto a restricted motif set and values near 1 indicate diverse associations, but the relationship between the Jaccard index and this interpretation could be explained more clearly.
- **Required correction** Provide a more intuitive explanation of JOS, possibly with a simple illustrative example, to help readers understand what the score measures.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Section 3.5, Methylation Analysis
- **Evidence pointer** Section 3.5, Figure 7
- **Issue** The manuscript uses the term "CpG m" to denote methylated CpG sites, but this notation is not standard and could be confused with the "CpG island" notation. The term "mCpG" or "5mC at CpG sites" would be more conventional.
- **Required correction** Use standard notation for methylated CpG sites throughout the manuscript.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 7, Data Availability
- **Evidence pointer** Section 7
- **Issue** The data availability statement mentions a Zenodo archive for the software, but does not specify whether the trained model weights, the processed training data, or the code for reproducing the interpretability analyses are included.
- **Required correction** Clarify what exactly is included in the Zenodo archive and provide clear instructions for accessing all code and data needed to reproduce the results.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language
- **Affected element** Section 3.2, Cross-Cell Generalization
- **Evidence pointer** Section 3.2, Table 4
- **Issue** The phrase "retains substantial predictive signal" is vague. The Cohen's d values are reported, but the interpretation of what constitutes "substantial" is not defined.
- **Required correction** Provide context for interpreting the Cohen's d values, such as comparison to typical values in the field or a discussion of what magnitude of performance drop is considered acceptable for practical applications.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Section 1.2, Related Work
- **Evidence pointer** Section 1.2
- **Issue** The related work section mentions several models and methods but does not provide a critical comparison of their limitations in the context of the proposed approach. The discussion of why existing methods are insufficient is brief.
- **Required correction** Expand the related work section to more clearly articulate the specific gaps in existing methods that EpiBinder addresses.

## Risk / unsupported claims
- The claim that EpiBinder "consistently outperforms" sequence-only baselines cannot be evaluated without access to the actual results tables and figures.
- The claim that "increasing sequence span alone offers limited benefit for TF-binding prediction" is not directly supported by the experiments described, as no long-context models were included in the comparison.
- The biological interpretations of TF-TF interactions and methylation-sensitive loci are based solely on in silico analyses and are presented without sufficient caveats about their speculative nature.
- The claim that the model "captures the local regulatory grammar" is supported by the interpretability analyses, but the generalizability of this claim beyond the three cell lines studied is not established.
- The statement that EpiBinder "retains substantial predictive signal" under cross-cell transfer is not quantified against any benchmark or threshold for what constitutes "substantial."
- The manuscript's assertion that the model provides "candidate methylation-sensitive loci" and "putative TF-TF interactions" is appropriately hedged with "candidate" and "putative," but the downstream functional significance of these predictions is not validated.