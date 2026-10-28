## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Materials and Methods, Results, Discussion, Conclusions)
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims relative to provided evidence, and suitability for a Nature-style journal
- **Shared manuscript claim summary** The authors present an integrated computational pipeline combining hdWGCNA, ensemble machine learning (ElasticNet, Random Forest, XGBoost), and in silico perturbation (scTenifoldKnk, CellOracle) to identify cell-type-specific transcriptional regulators in tomato leaves from a public scRNA-seq dataset. They report 19 cell clusters mapped to five cell types, eight co-expression modules, a consensus set of 33 core TFs, and four candidate TFs whose virtual knockout is predicted to dysregulate functional pathways and, for two guard-cell WRKYs, shift cell identity toward a mesophyll-like state.
- **Visible evidence base** Full text including Methods, Results with figure references (Figures 1–5, Figure S3), and supplementary table references (Tables S1, S2, S4–S9). No actual figures, tables, or supplementary materials were provided for inspection.
- **Missing materials affecting confidence** All figures, supplementary tables, and supplementary figures are referenced but not included. The underlying scRNA-seq data, code, and parameter settings for reproducibility are not provided. The DNase-seq processing details and quality metrics are described but not verifiable.

## Reviewer
- **Overall assessment** This manuscript presents a computationally intensive framework for dissecting cell-type-specific regulatory programs in tomato leaves. The integration of multiple independent methods (co-expression networks, three machine learning classifiers, three GRN inference tools, and two perturbation strategies) is conceptually appealing and reflects current best practices in single-cell regulatory inference. However, the manuscript suffers from several critical weaknesses that prevent the case from being established. First, the central claims regarding cell-type identity shifts upon TF knockout rest entirely on in silico predictions with no experimental validation, and the authors acknowledge this limitation. Second, the biological novelty is limited: the cell-type composition of tomato leaves is already established, and the identified TF families (WRKY, ERF, G2-like) are well-known regulators. Third, several methodological details are insufficiently described or potentially problematic, including the use of a single public dataset without independent replication, the lack of clarity on how the "consensus" of 33 TFs was derived, and the absence of any benchmarking against known regulatory interactions. Fourth, the manuscript is written for a specialized computational audience, with limited accessibility for general readers. The work may be suitable for a specialized computational biology or plant science journal, but it does not meet the bar for broad-impact, high-novelty publication.

- **Who would be interested in the results, and why** Computational plant biologists and researchers working on single-cell transcriptomics in non-model crops would find the pipeline description useful. Researchers studying tomato leaf development, stomatal biology, or trichome specialization may be interested in the candidate TF lists. Methodologists developing GRN inference or in silico perturbation frameworks might appreciate the multi-method integration strategy. However, the lack of experimental validation limits the audience to those interested in hypothesis generation rather than established biological mechanisms.

- **Major strengths**  
  1. The multi-method integration strategy (three machine learning classifiers, three GRN inference tools, two perturbation frameworks) is methodologically thorough and represents a best-practice approach for reducing false positives in regulatory inference.  
  2. The use of orthogonal developmental trajectory methods (RNA velocity via VeloVI, CytoTRACE) with concordant results strengthens the developmental interpretation.  
  3. The authors are transparent about limitations, including the lack of experimental validation and the reliance on inferred GRNs.  
  4. The identification of convergent targets across four independent knockout simulations (e.g., Solyc09g084470) provides a testable hypothesis for future work.

- **Major Concerns**

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency for causal claims  
- **Claim pointer** "The simulations predicted that these knockouts might dysregulate core functional pathways" and "the virtual deletion of the guard-cell-associated SlWRKY-78 and SlWRKY-75 could induce a directional trajectory shift from the terminally differentiated guard cells back to the less differentiated mesophyll territory"  
- **Evidence pointer** Section 3.4, Figures 4 and 5, location not provided  
- **Concern** The central biological claims of this manuscript rest entirely on in silico perturbation predictions with no experimental validation. The authors themselves acknowledge this in Section 4.4, stating that "candidate TFs identified here were prioritized through computational approaches without direct experimental validation." While computational predictions can generate hypotheses, the manuscript presents these predictions as the primary findings without any orthogonal evidence (e.g., published mutant phenotypes, expression validation, or chromatin confirmation) to support the predicted regulatory roles. The claim that knockout of SlWRKY-78 and SlWRKY-75 "could induce a directional trajectory shift" is presented as a significant result, but it is a model prediction that has not been tested.  
- **Why it matters** In a Nature-style journal, causal claims about gene function require experimental support or at minimum strong convergent evidence from independent experimental sources. Without validation, the biological significance of the predicted regulatory network remains speculative. The manuscript does not establish that the predicted trajectory shifts reflect real biological phenomena rather than artifacts of the inference pipeline.  
- **Resolution test** Provide experimental validation of at least one candidate TF (e.g., CRISPR knockout or knockdown followed by phenotyping and transcriptomic analysis), or substantially reframe the claims as purely predictive and hypothesis-generating, removing language that implies biological causality.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological transparency and reproducibility  
- **Claim pointer** "A consensus of 33 core TFs was identified" and "The intersection of three putative GRNs retained 536 regulatory edges connecting 72 TFs to 365 target genes"  
- **Evidence pointer** Sections 3.3 and 3.4, Figure 3G, Figure S3, Tables S7–S9, location not provided  
- **Concern** The derivation of the "consensus" set of 33 TFs is not clearly described. The text states that the consensus was "extracted by the intersection of the top 100 features consistently identified across all three algorithms," but the criteria for "consistently identified" are ambiguous. Does this mean the intersection of the top 100 from each algorithm (which would yield at most 100, not 33), or a different threshold? Similarly, the GRN intersection of 536 edges from three methods is described but the specific filtering criteria, score thresholds, and the degree of overlap between methods are not quantified. Without these details, the reproducibility of the core results is questionable.  
- **Why it matters** The central methodological contribution of this work is the integration of multiple computational approaches. If the integration criteria are not precisely specified, other researchers cannot reproduce the analysis or assess whether the results are robust to parameter choices. The lack of code or detailed parameter settings further compounds this issue.  
- **Resolution test** Provide a precise, step-by-step description of how the 33-TF consensus was derived, including exact thresholds for each algorithm, the overlap calculation method, and the handling of ties or missing values. Make the analysis code and parameter files publicly available.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Data quality and preprocessing rigor  
- **Claim pointer** "The initial dataset comprised 9615 cells and 34,075 genes. Sequential removal of low-quality cells, likely multiplets, and lowly expressed genes retained 8703 cells and 23,127 genes. Further exclusion of cells with insufficient spliced and unspliced transcript information yielded a final analytic dataset of 7993 cells."  
- **Evidence pointer** Section 3.1, location not provided  
- **Concern** The quality control (QC) pipeline is described only in terms of cell and gene counts, with no information on the specific thresholds used for filtering (e.g., minimum/maximum UMI counts, mitochondrial read fraction, gene detection rate). The manuscript does not report the proportion of cells removed at each step, the distribution of QC metrics, or whether the filtering criteria were pre-specified or data-adaptive. Additionally, the use of a single public dataset without any independent replication or cross-validation raises concerns about the generalizability of the findings.  
- **Why it matters** QC decisions substantially influence downstream clustering, cell-type annotation, and network inference. Without transparent reporting of QC thresholds and their rationale, the validity of the 19 clusters and subsequent analyses cannot be assessed. The lack of replication means that the specific cell-type proportions and marker genes may reflect dataset-specific artifacts.  
- **Resolution test** Report all QC thresholds explicitly, provide QC metric distributions before and after filtering, and validate the clustering and annotation on an independent tomato leaf scRNA-seq dataset if available, or clearly state the limitations of single-dataset analysis.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Biological novelty and interpretive depth  
- **Claim pointer** "These findings provide a promising computational framework for deciphering cell-type-specific regulatory programs in horticultural crops"  
- **Evidence pointer** Sections 4.1–4.3, location not provided  
- **Concern** The biological insights derived from this analysis are largely confirmatory of known plant biology. The identification of photosynthesis-related programs in mesophyll cells, redox homeostasis in guard cells, and the involvement of WRKY and ERF TFs in stress and development are well-established in the literature. The manuscript does not identify previously unknown cell types, novel regulatory mechanisms, or unexpected TF-target relationships that would constitute a significant advance. The discussion sections are largely speculative, with phrases such as "suggests," "consistent with," and "potential" used throughout, without concrete testable predictions beyond what is already known.  
- **Why it matters** For a high-impact journal, the findings must offer new biological insight or a methodological advance that enables new discoveries. This manuscript offers a pipeline description with confirmatory results. The claim of a "promising computational framework" is not sufficient to establish scientific novelty if the framework does not reveal previously unknown biology.  
- **Resolution test** Identify and highlight at least one novel, non-obvious biological finding (e.g., a previously uncharacterized TF-target interaction, a new cell state, or a regulatory mechanism that challenges current models) and provide evidence that this finding is robust and biologically meaningful.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** No  
- **Axis** Statistical rigor and uncertainty quantification  
- **Claim pointer** "XGBoost achieving the highest accuracy (0.85) to define cell identity" and "AUC values were consistently high for the abundant mesophyll and guard cell populations (AUC > 0.95 across all classifiers)"  
- **Evidence pointer** Section 3.3, Figure 3D–F, Table S7, location not provided  
- **Concern** The performance metrics for the machine learning classifiers are reported without confidence intervals, statistical significance testing, or comparison to baseline models. The accuracy of 0.85 for XGBoost is presented as "highest," but the difference from ElasticNet (0.83) and Random Forest (0.81) is not tested for significance. The AUC values are reported as point estimates without variance. Additionally, the manuscript does not describe how the training and test sets were partitioned, whether class imbalance was addressed, or whether the reported metrics are from cross-validation or a held-out test set.  
- **Why it matters** Without uncertainty quantification and proper statistical comparison, the claim that XGBoost is the best-performing model is not supported. The differences in accuracy (0.85 vs 0.83 vs 0.81) may be within noise. Furthermore, the high AUC values for abundant cell types may reflect class imbalance rather than genuine discriminative power.  
- **Resolution test** Report confidence intervals or standard deviations for all performance metrics, perform statistical significance testing for model comparisons, describe the train/test split and cross-validation scheme, and address class imbalance in the evaluation.

- **Minor Comments**

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity of writing  
- **Affected element** Section 3.3, last paragraph  
- **Evidence pointer** "Cross-referencing the normalized importance scores of the top 10 TFs with the algorithms that selected them further underscored this convergence further illustrated this convergence"  
- **Issue** This sentence contains a grammatical error with a duplicated phrase ("further underscored this convergence further illustrated this convergence").  
- **Required correction** Revise to a single, clear statement, e.g., "Cross-referencing the normalized importance scores of the top 10 TFs with the algorithms that selected them further underscored this convergence."

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Figure accessibility  
- **Affected element** Figures 1–5  
- **Evidence pointer** Figure legends not provided in the manuscript text  
- **Issue** The manuscript references Figures 1–5 extensively, but the figure legends are not included in the provided text. Without legends, the reader cannot interpret the figures.  
- **Required correction** Ensure all figure legends are included and self-explanatory, describing the data shown, the statistical tests used, and the meaning of all axes, colors, and symbols.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Terminology consistency  
- **Affected element** Section 2.4 and Section 3.2  
- **Evidence pointer** "hdWGCNA" used throughout, but the method is described as "high-dimensional weighted gene co-expression" in the Abstract  
- **Issue** The abbreviation "hdWGCNA" is introduced in the Abstract but the full term is not consistently defined at first use in the main text.  
- **Required correction** Define "hdWGCNA" in full at first use in the main text (Section 2.4) and use the abbreviation consistently thereafter.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Reference completeness  
- **Affected element** Section 2.1  
- **Evidence pointer** "The tomato reference genome assemblies (SL2.5 and SL4.0) were obtained from Sol Genomics Network [17]"  
- **Issue** The reference for the Sol Genomics Network is cited as [17], but the full reference list is not provided in the manuscript text.  
- **Required correction** Ensure all references are complete and correctly formatted in the final submission.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Data availability  
- **Affected element** Section 2.1  
- **Evidence pointer** "Single-cell RNA-seq FASTQ data of healthy tomato leaves (SRX15090984) were retrieved from European Nucleotide Archive"  
- **Issue** The manuscript does not include a Data Availability Statement indicating where the processed data, analysis scripts, and code are deposited.  
- **Required correction** Add a Data Availability Statement specifying the accession numbers for raw and processed data and the repository for analysis code.

## Risk / unsupported claims
- The claim that knockout of SlWRKY-78 and SlWRKY-75 "could induce a directional trajectory shift from the terminally differentiated guard cells back to the less differentiated mesophyll territory" is unsupported by experimental evidence and relies entirely on in silico predictions from inferred GRNs.
- The claim that "these knockouts might dysregulate core functional pathways" is based on computational predictions without validation.
- The claim that the 33-TF consensus set represents "core TFs" associated with cell identity is not supported by any functional validation or independent experimental evidence.
- The claim that the pipeline provides "a promising methodological framework" is not supported by benchmarking against known regulatory interactions or comparison to alternative methods.
- The biological interpretation that mesophyll cells serve as "putative progenitor" cells is speculative and not directly supported by lineage tracing or experimental evidence.
- The performance comparison between machine learning models (XGBoost accuracy 0.85 vs ElasticNet 0.83 vs Random Forest 0.81) is not statistically validated, and the claim that XGBoost is "highest" is not supported.
- The claim of "higher-resolution dissection of healthy leaf architecture" relative to prior work is not quantitatively supported by comparison to the reference dataset.
- The statement that "no opposing trends" were observed between VeloVI and CytoRank correlations is presented without statistical testing or quantitative thresholds.
- The claim that module 4 TFs have "negligible pseudotime trends" is based on an unreported correlation threshold.
- The claim that the four candidate TFs were "selected" for knockout analysis is not justified with explicit criteria for this selection.