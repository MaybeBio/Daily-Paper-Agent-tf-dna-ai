## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability) without figures, tables, or supplementary materials
- **Assessment boundary** Methodological soundness, validity of claims relative to provided evidence, clarity of presentation, and suitability for the stated scope of the journal
- **Shared manuscript claim summary** The authors present STED, a computational framework that uses topic modeling of single-cell RNA-seq reference data to deconvolve bulk epigenomic datasets (ATAC-seq, ChIP-seq, CUT&Tag) and reconstruct cell-type-specific regulatory signals, including transcription factor motifs and super-enhancers
- **Visible evidence base** Text descriptions of benchmarking results, ablation studies, and biological case studies; references to figures and tables not directly viewable
- **Missing materials affecting confidence** All figures, tables, supplementary materials, and code repository contents are not accessible in the provided input, limiting verification of quantitative claims

## Reviewer
- **Overall assessment** The manuscript describes a timely and potentially useful computational framework that addresses a real gap in the analysis of legacy bulk epigenomic data. The modular design separating topic-model backends from cross-modal deconvolution is conceptually appealing. However, the manuscript as provided has several critical gaps in methodological detail, validation evidence, and clarity that prevent full assessment of the claims. The central novelty relative to existing deconvolution tools needs sharper articulation, and the quantitative evidence supporting key performance claims is not verifiable from the text alone.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on epigenetic data integration, particularly those interested in deconvolution of bulk chromatin accessibility and histone modification data. Researchers studying cell-type-specific gene regulation in complex tissues, cancer epigenomics, and developmental biology would also find the framework relevant. The incorporation of large language model-based topic modeling (BERTopic) may attract researchers exploring foundation model applications in genomics.

- **Major strengths** The modular architecture separating topic discovery from deconvolution is a thoughtful design choice that could improve flexibility and comparability across methods. The use of gene activity scores as a cross-modal bridge is physically motivated and addresses a real technical challenge. The inclusion of multiple topic-modeling backends, including a foundation-model-based approach, demonstrates forward-looking methodology. The application to diverse biological systems (PBMCs, brain, zebrafish, colorectal cancer) suggests broad applicability.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that STED "significantly outperforms existing rigid-reference tools in accuracy and robustness against cross-platform batch effects"
- **Evidence pointer** Results section, benchmarking descriptions; specific figures not viewable
- **Concern** The quantitative basis for the performance claims is not verifiable from the text. The manuscript states PCC values and comparative results but does not provide sufficient detail on the benchmarking methodology, statistical testing, or effect sizes. The comparison against EPI-ATAC and DeConPeaker is described only qualitatively in the text, and the specific metrics, datasets, and conditions under which STED outperforms these tools are not fully specified.
- **Why it matters** The central claim of the manuscript is that STED provides superior performance over existing tools. Without verifiable quantitative evidence, this claim cannot be evaluated. The reproducibility of the benchmarking is essential for the community to assess whether STED genuinely advances the state of the art.
- **Resolution test** Provide full benchmarking tables with confidence intervals, statistical significance tests, and detailed descriptions of the evaluation protocol. Include the exact versions of comparison tools, parameter settings, and data preprocessing steps. Make all benchmarking scripts and intermediate results available.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "STED successfully identifies cell-type-specific transcription factor binding motifs and differential peaks associated with lineage commitment" in the hematopoietic stem cell differentiation model
- **Evidence pointer** Results section, HSC differentiation analysis; Figures 6 and S7 referenced but not viewable
- **Concern** The validation of the reconstructed cell-type-specific signals against ground truth is not described in sufficient detail. The manuscript states that STED recovered over 90% of validated bulk peaks, but the definition of "validated" peaks, the comparison methodology, and the statistical significance of the recovery rate are not specified. The biological validation of the identified motifs and peaks is also not described.
- **Why it matters** The biological utility of STED depends on the accuracy of the reconstructed cell-type-specific signals. Without rigorous validation against independent ground truth, the biological claims cannot be distinguished from artifacts of the computational pipeline.
- **Resolution test** Provide detailed validation methodology, including how ground truth was established, what constitutes a "validated" peak, and how the 90% recovery rate was calculated. Include comparison against alternative reconstruction methods and demonstrate that the identified motifs and peaks are biologically meaningful through independent experimental validation or literature support.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "STED couples these latent regulatory topics with a physics-based 'gene activity score' transformation, which acts as a cross-modal bridge to deconvolve bulk chromatin accessibility"
- **Evidence pointer** Methods section, Cross-modal transformation via gene activity scores
- **Concern** The gene activity score calculation is described only briefly. The manuscript states that weights are assigned based on distance with a decay parameter of 5000, but the exact functional form of the weighting scheme, the rationale for the specific decay parameter, and the sensitivity of results to this choice are not provided. The "physics-based" characterization is not justified with a clear physical model.
- **Why it matters** The gene activity score is a critical component of the cross-modal bridge. If the weighting scheme is arbitrary or poorly justified, the validity of the entire deconvolution approach is compromised. The sensitivity of results to this parameter needs to be established.
- **Resolution test** Provide the complete mathematical formulation of the gene activity score, justify the choice of decay parameter through sensitivity analysis, and clarify what "physics-based" means in this context. Show that results are robust to reasonable variations in the weighting scheme.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "STED provides a scalable, foundation-model-empowered solution" and that BERTopic "can exploit semantic structure captured by single-cell foundation models"
- **Evidence pointer** Methods section, Foundation-model-based topic modeling; Results section, benchmarking descriptions
- **Concern** The computational cost and scalability of the BERTopic approach are not quantified. The manuscript mentions that clustering is the computational bottleneck but does not provide runtime comparisons, memory usage, or scaling behavior with increasing cell numbers. The practical utility of the foundation-model-based approach for large datasets is therefore unclear.
- **Why it matters** Scalability is a stated advantage of the framework. Without quantitative evidence of computational performance, users cannot assess whether the BERTopic backend is practical for their dataset sizes.
- **Resolution test** Provide runtime and memory benchmarks across dataset sizes, compare computational costs across the three backends, and discuss the practical limits of the approach.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Originality
- **Claim pointer** The manuscript claims that STED's "key idea" is "the construction of a shared latent interface that connects three tasks within one workflow"
- **Evidence pointer** Introduction, Methods section
- **Concern** The novelty of the shared latent interface approach relative to existing multi-omics integration methods needs sharper articulation. The manuscript acknowledges that topic modeling has been used in genomics before, but does not clearly delineate what specific aspects of the shared latent interface are new compared to prior work in transfer learning, domain adaptation, or multi-view learning applied to genomics.
- **Why it matters** The contribution of the manuscript depends on the novelty of the methodological approach. If the shared latent interface is essentially a combination of existing techniques, the contribution is incremental rather than transformative.
- **Resolution test** Provide a more detailed comparison with existing methods, explicitly stating what is conceptually new about the shared latent interface and demonstrating why this design leads to improved performance over simpler alternatives.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, Model selection and evaluation
- **Evidence pointer** Methods section, text description
- **Issue** The description of hyperparameter optimization is vague. The manuscript states that K and other parameters are optimized but does not specify the search space, optimization strategy, or criteria for selecting the final parameters.
- **Required correction** Provide a detailed description of the hyperparameter optimization procedure, including search ranges, optimization algorithms, and selection criteria.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section, Data preprocessing
- **Evidence pointer** Methods section, text description
- **Issue** The description of the gene activity score calculation mentions normalization by gene length but does not specify the exact normalization procedure or whether other confounders (e.g., GC content, mappability) were considered.
- **Required correction** Provide the complete normalization formula and discuss potential confounding factors and how they were addressed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section, benchmarking
- **Evidence pointer** Results section, text description
- **Issue** The manuscript reports PCC and RMSE values but does not describe the number of replicates, the variability across replicates, or the statistical significance of differences between methods.
- **Required correction** Report the number of independent replicates, provide confidence intervals or standard deviations, and perform appropriate statistical tests for method comparisons.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section, colorectal cancer analysis
- **Evidence pointer** Results section, text description
- **Issue** The colorectal cancer analysis is described briefly, and the comparison with bulk analysis is mentioned only qualitatively. The specific findings and their biological significance are not described in detail.
- **Required correction** Provide a more detailed description of the colorectal cancer findings, including the specific super-enhancers identified, their associated genes, and the biological pathways implicated.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Methods section, notation summary
- **Evidence pointer** Table 1 referenced but not viewable
- **Issue** The notation summary table is referenced but not provided in the text. Without this table, the mathematical notation in the methods is difficult to follow.
- **Required correction** Include the notation table in the main text or provide a comprehensive list of symbols and their definitions in the methods section.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability section
- **Evidence pointer** Data availability section, text description
- **Issue** The data availability section lists repositories for publicly available data but does not provide specific accession numbers or identifiers for each dataset used in the study.
- **Required correction** Provide complete accession numbers or DOIs for all datasets used, including the specific versions and processing pipelines applied.

## Risk / unsupported claims
- The claim of "significantly outperforms existing rigid-reference tools" is not quantitatively verifiable from the provided text without access to the referenced figures and tables
- The claim of recovering "over 90% of validated bulk peaks" lacks definition of "validated" and the validation methodology
- The characterization of the gene activity score as "physics-based" is not justified with a clear physical model
- The claim of "scalable" performance is not supported by computational benchmarks
- The biological findings in the colorectal cancer analysis (578 and 386 super-enhancers) are stated without statistical confidence measures or validation details
- The claim that STED "uncovers tumor-specific super-enhancers... a mechanism obscured in bulk signals" requires demonstration that the identified super-enhancers are indeed cell-type-specific and not artifacts of the reconstruction
- The performance comparison with EPI-ATAC and DeConPeaker is described qualitatively without specific quantitative results visible in the text
- The claim that BERTopic "captures high-dimensional semantic states" is not supported by direct comparison with alternative embedding approaches