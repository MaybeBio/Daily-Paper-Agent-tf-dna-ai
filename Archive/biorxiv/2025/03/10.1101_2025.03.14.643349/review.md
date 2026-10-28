## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability, author contributions, funding, conflict of interest, acknowledgements)
- **Assessment boundary** Scientific content, methodological soundness, validity of claims relative to presented evidence, and clarity of reporting. No assessment of formatting, grammar, or editorial style beyond what affects scientific comprehension.
- **Shared manuscript claim summary** The authors present a workflow for integrating paired single-cell RNA-seq and ATAC-seq data, benchmark three integration methods (scPair, MultiVI, MOFA+), select scPair as the best performer, and apply it to SEA-AD middle temporal gyrus data from 26 donors. They report AD-associated gene expression changes in glial subpopulations, identify regulatory programs involving transcription factors (JUN, FOSL2 in astrocytes; ZNF family in microglia; SOX family in oligodendrocytes), and highlight Solute Carrier (SLC) family genes as novel contributors to AD glial dysfunction. They use interpretable machine learning (feature attribution) to cross-validate findings from DORC/FigR analyses.
- **Visible evidence base** Abstract, Introduction, Materials and Methods, Results, Discussion, Data Availability, Author Contributions, Funding, Conflict of Interest, Acknowledgements. No figures, tables, or supplementary materials were provided.
- **Missing materials affecting confidence** All figures and figure legends, all supplementary materials, all tables, exact statistical outputs, parameter settings for scPair beyond those described, code availability statement, and any validation metrics beyond those mentioned in text. The absence of figures is particularly limiting for assessing clustering quality, UMAP visualizations, DORC score distributions, and feature attribution results.

## Reviewer

- **Overall assessment** This manuscript addresses a timely and important problem: the lack of standardized workflows for integrating single-cell multiomic data in disease contexts. The authors benchmark three integration methods and apply the best performer to a well-characterized AD dataset. The biological findings, particularly the identification of SLC family genes and specific transcription factors in glial subtypes, are potentially interesting. However, the manuscript as presented has several critical gaps. The absence of all figures and tables makes it impossible to evaluate the core results. The benchmarking section lacks quantitative detail on how "best" was determined. The feature attribution analysis is described but its validation is circular: the same model that generates embeddings is used to identify important features, and these are then compared to DORC results from a different method without a clear statistical framework for agreement. The claim of "first" for linking SLC family genes to AD in multiple cell types is strong and requires more careful literature review. The sample selection for benchmarking (4 donors) and the exclusion of 2 donors from the full analysis are not adequately justified. Overall, the workflow is sensible and the biological questions are relevant, but the evidence as presented does not fully establish the claims.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing or applying single-cell multiomic integration methods would be interested in the benchmarking comparison and workflow design. Alzheimer's disease researchers, particularly those studying glial biology, would be interested in the identified regulatory programs and candidate genes (SLC family, JUN, FOSL2, ZNF family, SOX family). Researchers working on interpretable machine learning for genomics would find the feature attribution approach relevant. The manuscript could also be of interest to method developers seeking validated workflows for SEA-AD or similar datasets.

- **Major Strengths**
  - The manuscript addresses a real methodological gap: standardized workflows for single-cell multiomic integration in disease contexts.
  - The benchmarking of three distinct integration approaches (supervised deep learning, unsupervised deep generative, factorization-based) is a useful contribution.
  - The focus on glial cells in AD is biologically relevant and timely.
  - The combination of DORC analysis with interpretable machine learning (feature attribution) is a thoughtful approach to cross-validating findings.
  - The identification of specific transcription factors and SLC family genes provides concrete, testable hypotheses.
  - The workflow is described in sufficient detail to be reproducible, assuming code is made available.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that scPair was the "most effective integration tool" based on benchmarking results.
- **Evidence pointer** Results section "Benchmarking of scMultiome integration tools suggested top performer for proper integrative analysis"; Figure 2 (not provided)
- **Concern** The benchmarking results are described only qualitatively in the text. The authors state that scPair "ranked highest across the most of integration metrics" and "outperformed" alternatives, but no quantitative values, statistical tests, or confidence intervals are provided. The figure that would support this claim is not available for review. It is impossible to assess whether the differences between methods are meaningful or within noise.
- **Why it matters** The selection of scPair is the foundation for all downstream analyses. If the benchmarking is not rigorously demonstrated, the entire workflow's validity is in question.
- **Resolution test** Provide the full benchmarking results with quantitative metrics for all methods across all evaluation criteria, including statistical significance testing where appropriate. The figure must be available for review.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validity
- **Claim pointer** The manuscript claims that feature attribution analysis "identified genes that strongly contribute to integrated cell states" and that these genes overlap with DORC-identified genes, implying cross-validation.
- **Evidence pointer** Methods section "Glial cell subpopulation analysis and feature attribution calculations"; Results sections for each cell type; Figures 4e-f, 5e-f, 6e-f (not provided)
- **Concern** The feature attribution analysis is performed on the scPair model's embeddings, and the DORC analysis is performed on the same data. The agreement between these two methods is presented as validation, but this is circular reasoning. Both methods are derived from the same underlying data and model, so agreement does not constitute independent confirmation. Furthermore, the threshold for "highly ranked" features (top 100 per method per cluster) is arbitrary, and the statistical significance of the overlap between FA and DORC genes is not assessed.
- **Why it matters** The claim of cross-validation is central to the manuscript's methodological contribution. If the two methods are not independent, the "validation" is illusory, and the identified genes may be artifacts of the model rather than biologically meaningful.
- **Resolution test** Provide a clear explanation of how the two methods provide independent evidence. Perform a permutation or enrichment test to show that the overlap between FA and DORC genes is greater than expected by chance. Alternatively, validate the identified genes using an independent dataset or experimental approach.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that "Our study is the first to name SLC family genes as key regulatory genes in AD in multiple cell types."
- **Evidence pointer** Discussion section
- **Concern** This is a strong novelty claim. The authors do not provide a comprehensive literature review to support it. SLC family genes have been extensively studied in the context of AD, including SLC2A1 (GLUT1), which the authors themselves cite as known. The claim that no direct link exists between SLC family genes and AD is contradicted by the authors' own citations. The claim needs to be substantially softened or supported with a systematic literature search.
- **Why it matters** Overclaiming novelty undermines the credibility of the manuscript and could mislead readers.
- **Resolution test** Conduct a systematic literature search on SLC family genes in AD and revise the claim to accurately reflect the existing knowledge. If the claim is retained, provide specific evidence that no prior study has linked these particular SLC genes to AD in these cell types.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological transparency
- **Claim pointer** The manuscript describes the analysis of 26 of 28 donors, excluding two due to "relatively low glial cell counts."
- **Evidence pointer** Methods section "scMultiome integration for glial cells using scPair"
- **Concern** The exclusion of H20.33.040 and H20.33.043 is mentioned but not justified in detail. The threshold for "relatively low" is not defined. If these donors are excluded, it is unclear whether the remaining 26 donors are balanced for sex, age, and disease status. This could introduce bias into the downstream analyses.
- **Why it matters** Sample selection bias can affect the validity of all reported findings. The authors need to demonstrate that the excluded donors do not systematically differ from the included ones in ways that could confound the results.
- **Resolution test** Provide a table of donor characteristics (age, sex, disease status, glial cell count) for all 28 donors, with the exclusion criteria clearly stated. Show that the remaining 26 donors are balanced across relevant covariates.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The manuscript describes a "comprehensive workflow" for single-cell multiomic analysis.
- **Evidence pointer** Methods section; Figure 1 (not provided)
- **Concern** No code availability statement is provided. The methods are described in text, but the exact parameters, hyperparameters, and software versions are not fully specified. For example, the scPair training details are partially described, but the MultiVI and MOFA+ implementations rely on default parameters that are not stated. The absence of code and detailed parameters makes it difficult for others to reproduce the workflow.
- **Why it matters** Reproducibility is a core requirement for computational biology manuscripts. Without code and full parameter specifications, the workflow cannot be independently validated or applied by other researchers.
- **Resolution test** Provide a code availability statement with a link to a public repository containing all analysis scripts, and include a detailed parameter file or configuration for all methods used.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Benchmarking sc-multiome integration methods"
- **Evidence pointer** Location not provided
- **Issue** The sentence "We set the learning rate to 0.001, batch size to 300, and employed batch normalization and layer normalization with GELU activation function. We used the Adam optimizer and set the dropout rate to 0.1, and." contains a grammatical error ("and." at the end) and is missing the output distribution specification for the ATAC-to-RNA component.
- **Required correction** Correct the grammatical error and specify the output distribution for the ATAC-to-RNA component (e.g., Bernoulli, ZINB).

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "scMultiome analysis revealed key regulatory elements in in astrocytes"
- **Evidence pointer** Location not provided
- **Issue** The section title contains a duplicated "in" ("in in").
- **Required correction** Correct the title to "scMultiome analysis revealed key regulatory elements in astrocytes".

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "scMultiome analysis uncovers an AD-specific state in microglia"
- **Evidence pointer** Location not provided
- **Issue** The list of 14 genes identified by FA analysis is presented as a run-on list within a paragraph, making it difficult to read. Additionally, the text states "cluster 8 (Fig. 5a, b)" but the figure is not provided.
- **Required correction** Format the gene list as a proper list or table, and ensure all figure references are correct and figures are available.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Dataset description"
- **Evidence pointer** Location not provided
- **Issue** The data access date is given, but no details on the specific data version or any preprocessing steps applied by the SEA-AD consortium are provided.
- **Required correction** Specify the data version and any consortium-provided preprocessing steps.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion section
- **Evidence pointer** Location not provided
- **Issue** The discussion states "Our study is the first to name SLC family genes as key regulatory genes in AD in multiple cell types" but this is not supported by the evidence presented and is contradicted by the authors' own citations of SLC2A1, SLC22A8, and SLCO1A2.
- **Required correction** Soften the claim to "Our study identifies SLC family genes as potentially novel regulatory genes in AD glial cells" and provide a more nuanced discussion of prior literature.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Benchmark performance evaluation"
- **Evidence pointer** Location not provided
- **Issue** The metrics used for evaluation are listed, but the specific thresholds or criteria for "good" performance are not defined. For example, what constitutes an acceptable cLISI or batchASW value?
- **Required correction** Provide clear criteria for interpreting each metric and how they were weighted in the final decision.

## Risk / unsupported claims
- The claim that scPair is the "most effective integration tool" is unsupported without quantitative benchmarking data.
- The claim of cross-validation between FA and DORC analyses is unsupported due to circular reasoning.
- The claim of being "first" to link SLC family genes to AD in multiple cell types is unsupported and likely overstated.
- The biological significance of the identified genes (e.g., GLDN, SYNDIG1) is speculative and not experimentally validated.
- The statement that "Our findings offer novel insights into disease-related changes in gene regulation" is not fully supported without comparison to existing AD single-cell studies.
- The claim that the workflow "enabled effective batch correction and cross-modality alignment" is not quantitatively demonstrated in the text.
- The exclusion of two donors is not justified, and the potential for selection bias is not addressed.
- The absence of all figures and tables makes many specific claims unverifiable.