## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methodology, results, conclusions, data availability, supporting information description)
- **Assessment boundary** Technical soundness and validity of the proposed hierarchical method, adequacy of benchmarking, support for biological claims, reproducibility, and clarity of presentation
- **Shared manuscript claim summary** The authors propose a two-step hierarchical method to analyze protein-DNA interfaces, using Cα-O5′ distance cutoffs to preselect interfacial residue-nucleotide pairs before computing heavy atom contact matrices. They claim this reduces computational cost by three orders of magnitude, and apply it to 1937 PDB structures to report residue preferences and interaction-type distributions in nucleosomes versus non-nucleosomes.
- **Visible evidence base** Abstract, Introduction, Methodology, Results and Discussion, Conclusions, Data and Software Availability, Supporting Information description, Figure captions (Figures 1-6), Table S1-S3 references
- **Missing materials affecting confidence** Full figures and their data, Supporting Information (Tables S1-S3, Figure SI, flowchart), the deposited code and data at Zenodo, detailed numerical results, statistical analyses, and any validation against experimental or independent computational benchmarks

## Reviewer
- **Overall assessment** The manuscript presents a computationally motivated methodological contribution with a clear practical benefit. The hierarchical filtering strategy is conceptually simple and the reported speedup is substantial. However, the current evidence base is insufficient to fully validate the method's accuracy and generalizability. The benchmarking against the full heavy atom method is limited to 10 nucleosome structures, and no comparison with established tools such as DNAproDB or PDIdb is provided. The biological conclusions, while plausible, are derived from a single analysis pipeline without independent cross-validation or statistical treatment. The manuscript would benefit from a more rigorous validation framework, clearer presentation of the benchmark results, and a more cautious interpretation of the biological findings.
- **Who would be interested in the results, and why** Computational structural biologists studying protein-DNA recognition, developers of bioinformatics tools for macromolecular interface analysis, and researchers in the DNA repair, transcription, and chromatin fields who need efficient large-scale analysis of protein-DNA complexes. The method's low computational cost makes it attractive for high-throughput screening of the growing PDB repository.
- **Major strengths** The hierarchical approach is a pragmatic and effective solution to a real computational bottleneck. The two-step filtering strategy is intuitive and the reported three-orders-of-magnitude speedup is impressive. The application to a large dataset of 1937 structures provides a useful survey of residue preferences and interaction types. The authors make their code and data publicly available, which supports reproducibility.
- **Major Concerns** The validation is too narrow. Benchmarking on only 10 nucleosome structures, without testing on non-nucleosome complexes or diverse structural classes, leaves the method's generalizability unproven. The choice of Cα-O5′ distance cutoffs (1.2 nm for Arg/Lys, 1.0 nm for others) appears arbitrary and is not systematically optimized or justified. The comparison with the full heavy atom method is presented only as a computational time comparison, not as an accuracy comparison. No metrics such as precision, recall, or overlap of identified interface residues are reported. The biological conclusions, such as arginine dominance and phosphate backbone preference, are consistent with prior literature but are presented without statistical confidence intervals or significance testing. The claim of "three orders of magnitude" reduction in computational cost is based on a single hardware configuration and may not generalize. The manuscript lacks a comparison with existing tools like DNAproDB, which would contextualize the method's novelty and utility.
- **Minor Comments** The abstract mentions "05′" which should be "O5′" for clarity. The introduction contains a typo "the between the protein and DNA" which should be corrected. The methodology section would benefit from a more detailed description of the hierarchical algorithm, including pseudocode or a formal step-by-step procedure. The results section refers to "Figure SI" and "Table SI" without consistent naming conventions. The statement that "the protein-DNA interface is dominated by the arginine residues with a notable presence of lysine, serine, and tyrosine" in the abstract is not fully consistent with the results section which also highlights threonine. The authors should clarify whether the analysis is at the residue level or atom level and how redundancy in the PDB (e.g., homologous structures) was handled. The data availability statement provides a Zenodo link but does not specify the exact contents or file formats.
- **Technical failings that need to be addressed before the case is established** The absence of accuracy metrics comparing the hierarchical method's identified interface residues against the full heavy atom method is a critical gap. The lack of validation on non-nucleosome structures and on a broader set of protein-DNA complex types undermines the claim of general applicability. The arbitrary choice of Cα-O5′ cutoffs without sensitivity analysis is a technical weakness. The computational time comparison is reported for a single processor type and does not account for variations in structure size or complexity.
- **Assessment against Nature-style criteria** Originality: The hierarchical filtering concept is not entirely novel, as similar distance-based preselection strategies exist in other macromolecular analysis tools, but its specific application to protein-DNA interfaces with a focus on computational efficiency is a modest incremental contribution. Scientific importance: The method addresses a practical need for scalable analysis of the rapidly growing PDB, but the biological insights derived are largely confirmatory of known trends rather than transformative. Interdisciplinary readership: The work is primarily of interest to computational biologists and bioinformaticians; the biological conclusions are not sufficiently novel to attract a broad readership. Technical soundness: The core algorithmic idea is sound, but the validation is insufficient to establish reliability. Readability for nonspecialists: The manuscript is generally clear but contains some typographical errors and would benefit from a more explicit explanation of the method's workflow for readers unfamiliar with structural biology.
- **Recommendation posture** Supportive if technical concerns are resolved. The method has clear potential value, but the current evidence does not fully establish its accuracy, generalizability, or superiority over existing approaches. A revised manuscript with comprehensive benchmarking, sensitivity analysis, and statistical rigor could make a solid contribution.

### Major Concerns
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The hierarchical method "reduces the computational cost by three orders of magnitude" and is "adequate to capture details of the protein-DNA interaction at the interface."
- **Evidence pointer** Results and Discussion, Figure 3, Table S3
- **Concern** The benchmarking is performed on only 10 nucleosome structures. The claim of adequacy is based on a visual comparison of relative population distributions (Figure 3) without quantitative metrics such as precision, recall, or F1-score for the identified interface residues. The computational time comparison is reported for a single hardware configuration and does not account for variability across structure sizes or complexity.
- **Why it matters** Without quantitative accuracy metrics and a broader benchmark set, the method's reliability and generalizability cannot be established. The three-orders-of-magnitude speedup claim may not hold across different structure types or hardware.
- **Resolution test** Provide a quantitative comparison of interface residues identified by the hierarchical method versus the full heavy atom method on a diverse set of at least 50 structures spanning nucleosome and non-nucleosome classes. Report precision, recall, and overlap metrics. Include a sensitivity analysis of the Cα-O5′ cutoff values. Report computational times for multiple structure sizes and hardware configurations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The method is described as a "new and robust hierarchical approach" with a specific two-step procedure.
- **Evidence pointer** Methodology, Data and Software Availability
- **Concern** The methodology section lacks a detailed algorithmic description, including pseudocode or a formal step-by-step procedure. The Zenodo deposit is mentioned but its contents are not described in sufficient detail to allow independent replication. The exact parameters for the heavy atom contact calculation (e.g., atom types, distance definitions) are not fully specified.
- **Why it matters** Reproducibility is a core requirement for methodological contributions. Without a complete algorithmic description and accessible, well-documented code, other researchers cannot implement or verify the method.
- **Resolution test** Provide a detailed algorithmic description in the main text or supplementary material, including pseudocode. Ensure the Zenodo deposit contains the full source code, input/output examples, and a README file with usage instructions. Specify all parameters used in the analysis.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** "The protein-DNA interface is dominated by the arginine residues with a notable presence of lysine, serine, and tyrosine" and "nucleosomes have a greater arginine enrichment than non-nucleosomes."
- **Evidence pointer** Results and Discussion, Figures 4-6
- **Concern** The biological conclusions are presented without statistical analysis. No confidence intervals, significance tests, or effect sizes are reported. The comparison between nucleosome and non-nucleosome groups does not account for potential confounding factors such as protein family, DNA sequence composition, or structural redundancy in the PDB.
- **Why it matters** Without statistical rigor, the observed differences could be due to sampling bias or random variation. The conclusions may not be robust or generalizable.
- **Resolution test** Perform statistical tests (e.g., permutation tests, bootstrap) to assess the significance of differences in residue preferences and interaction-type distributions between nucleosome and non-nucleosome groups. Report effect sizes and confidence intervals. Address potential redundancy in the PDB by clustering structures at a sequence or structural similarity threshold.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparative validation
- **Claim pointer** The hierarchical method is presented as an improvement over "the commonly used heavy atom (of all residues of protein) to heavy atom (of all nucleotides) methodology."
- **Evidence pointer** Results and Discussion, Figure 3
- **Concern** The comparison is limited to computational time. No comparison is made with established tools such as DNAproDB, PDIdb, or other interface analysis software in terms of accuracy, feature set, or usability. The claim of improvement is therefore only partially supported.
- **Why it matters** To establish the method's value, it must be shown to be at least as accurate as existing tools while offering the computational advantage. Without such a comparison, the novelty and utility of the approach are unclear.
- **Resolution test** Compare the hierarchical method's output with that of DNAproDB or PDIdb on a common set of structures. Report agreement in identified interface residues and interaction types. Discuss any discrepancies and the relative advantages of each approach.

### Minor Comments
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The term "05′" is used instead of "O5′" for the oxygen atom of the nucleotide.
- **Required correction** Replace "05′" with "O5′" throughout the manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Language
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The sentence "Generally, the between the protein and DNA is analyzed" contains a grammatical error.
- **Required correction** Change to "Generally, the interaction between the protein and DNA is analyzed."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Abstract and Conclusions
- **Evidence pointer** Abstract, Conclusions
- **Issue** The abstract lists "tyrosine" as a notable residue, while the conclusions and results also highlight "threonine." The inconsistency may confuse readers.
- **Required correction** Ensure consistent reporting of notable residues across the abstract, results, and conclusions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodology detail
- **Affected element** Methodology
- **Evidence pointer** Methodology
- **Issue** The description of the hierarchical method lacks a formal algorithmic outline, making it difficult to follow the exact steps.
- **Required correction** Add a step-by-step algorithmic description or pseudocode in the methodology section or supplementary material.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results and Discussion
- **Evidence pointer** Figure 3
- **Issue** The benchmark comparison in Figure 3 is described only qualitatively. No numerical values or error bars are provided.
- **Required correction** Include numerical data or a table summarizing the comparison, with appropriate statistical measures.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and Software Availability
- **Evidence pointer** Data and Software Availability
- **Issue** The Zenodo deposit is mentioned but its contents are not described. It is unclear what files are included and how to use them.
- **Required correction** Provide a brief description of the deposit contents, including file formats and a usage example.

## Risk / unsupported claims
- The claim of "three orders of magnitude" reduction in computational cost is based on a single benchmark and may not generalize across different structure types or hardware.
- The assertion that the method is "adequate to capture details of the protein-DNA interaction at the interface" is supported only by a qualitative visual comparison, not quantitative accuracy metrics.
- The biological conclusions regarding residue preferences and interaction-type distributions are presented without statistical analysis, making their robustness uncertain.
- The claim that the method is "robust" is not supported by sensitivity analysis or testing on diverse structural classes.
- The statement that the method is "tractable even on personal computers" is plausible but not demonstrated with specific hardware specifications or runtime data beyond the single benchmark.