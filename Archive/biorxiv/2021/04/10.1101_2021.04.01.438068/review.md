## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, and supplementary figure references)
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and reproducibility as presented in the provided text
- **Shared manuscript claim summary** The authors benchmark cell-type annotation of mouse brain scATAC-seq data using meta-analytic marker gene sets, demonstrate that redundant marker genes improve classification accuracy, and provide a public resource (Meta scATAC-seq server) with re-annotated datasets and deep learning-based chromatin accessibility predictions
- **Visible evidence base** Results sections 2.1–2.7, methods section, figure references (Figures 1–5), supplementary figure references (Supplementary Figs. 1–7), and data availability statements
- **Missing materials affecting confidence** Figure panels and supplementary figures are referenced but not provided; exact AUROC values for many comparisons are not stated in text; details of the deep learning model architecture and training are incomplete; no code or data files are accessible for verification

## Reviewer
- **Overall assessment** The manuscript addresses a timely and practically important problem in single-cell epigenomics: robust cell-type annotation of scRNA-seq and scATAC-seq data using marker gene sets. The central claim, that meta-analytic marker genes with redundancy improve classification performance and enable simple aggregation methods to rival machine learning classifiers, is plausible and potentially useful. However, the evidence as presented is incomplete in several critical respects. The manuscript relies heavily on figures and supplementary materials that are not available for review, and several quantitative claims are stated without supporting numbers in the text. The deep learning component, while interesting, is under-specified and its connection to the main benchmarking claims is not fully developed. The work has clear potential for broad impact in the single-cell community, but the current manuscript does not fully establish its case from the provided material.

- **Who would be interested in the results, and why** Researchers working on single-cell epigenomics, particularly those analyzing scATAC-seq data, will find the benchmarking results and the proposed marker gene approach directly relevant. The Meta scATAC-seq server and the deep learning predictions will be of interest to computational biologists studying cell-type-specific gene regulation and chromatin accessibility. The finding that simple aggregation of redundant marker genes can outperform more complex classifiers is conceptually important for practitioners seeking robust and interpretable annotation methods. The work also speaks to the broader community interested in data integration across single-cell modalities.

- **Major strengths**  
  1. The problem addressed is of high practical relevance, and the systematic comparison across seven datasets is a valuable contribution.  
  2. The concept of using meta-analytic marker genes with redundancy to improve robustness in sparse scATAC-seq data is well motivated and conceptually sound.  
  3. The public availability of the Meta scATAC-seq server and the re-annotated datasets is a significant resource for the community.  
  4. The integration of deep learning for sequence-based prediction of cell-type-specific accessibility is a forward-looking addition.

- **Major Concerns**

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence completeness  
- **Claim pointer** The authors claim that "redundant marker genes give a dramatic improvement for a sparse scATAC-seq annotation across the data collected from different studies" (Abstract) and that "simple aggregation of such marker genes achieves performance comparable or higher than that of machine-learning classifiers" (Abstract).  
- **Evidence pointer** Results sections 2.2–2.4, Figures 2–4, Supplementary Figs. 4–7  
- **Concern** The quantitative evidence supporting the central claims is not presented in the text. AUROC values are mentioned qualitatively (e.g., "0.8-0.9" for SF marker sets in section 2.4), but exact numbers, confidence intervals, and statistical comparisons across methods and datasets are not provided. The figures that would substantiate these claims are not available for review. Without these data, the magnitude and significance of the reported improvements cannot be assessed.  
- **Why it matters** The central contribution of the manuscript is the demonstration that marker gene selection and aggregation outperform alternative approaches. If the quantitative evidence is not clearly presented, the claims are not verifiable, and the practical recommendations cannot be evaluated.  
- **Resolution test** Provide exact AUROC values (with standard deviations or confidence intervals) for all methods, marker sets, and datasets in the main text or a supplementary table. Include statistical tests comparing the best marker set approach to machine learning classifiers. Make the relevant figures available for review.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The authors state that they "trained a deep neural network to predict chromatin accessibility from only DNA sequence" (Abstract) and describe a custom CNN with a Basset-like architecture (section 2.7).  
- **Evidence pointer** Section 2.7, Figure 5, Methods section "Sequence analysis of accessible sites with deep learning"  
- **Concern** The deep learning model is described at a high level, but critical details are missing: the exact architecture (number of layers, filter sizes, pooling, etc.) is partially given, but hyperparameters, training procedure, data preprocessing, and evaluation metrics are incomplete. The claim of improved performance over DeepSEA (AUPR 0.539 vs 0.444) is stated without error bars or statistical significance. The connection between the deep learning predictions and the marker gene analysis is not clearly established.  
- **Why it matters** The deep learning component is presented as a key resource and a demonstration of the utility of the re-annotated data. Without full methodological details and rigorous evaluation, the model cannot be reproduced or its performance independently verified.  
- **Resolution test** Provide a complete description of the model architecture, training details, hyperparameter selection, and evaluation protocol. Include confidence intervals for AUPR values and a comparison to appropriate baselines. Clarify how the deep learning predictions are integrated with the marker gene analysis.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Generalizability  
- **Claim pointer** The authors claim that their approach is applicable "beyond the heterogeneity of scATAC-seq data" (Key points) and that the marker gene sets are robust across datasets.  
- **Evidence pointer** Sections 2.3–2.4, Supplementary Fig. 5  
- **Concern** The generalizability of the findings is limited by the focus on mouse brain data. The authors do not discuss how the approach might perform on other tissues, species, or data generated with different protocols. The variability in performance across datasets (e.g., low correlation for Cusanovich and Zhu datasets) is noted but not explained or addressed.  
- **Why it matters** The practical utility of the proposed method depends on its applicability beyond the specific datasets tested. Without evidence of generalizability, the claims of broad utility are not supported.  
- **Resolution test** Discuss the potential limitations of the approach for other tissues or data types. Provide an analysis of why certain datasets show lower performance and whether the method can be adapted to improve robustness.

- **Minor Comments**

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Section 2.2, Figure 2B  
- **Evidence pointer** Section 2.2, Figure 2B  
- **Issue** The statement "fewer than 200 genes achieved an AUROC greater than 0.625 for each cell-type" is ambiguous. It is unclear whether this refers to the number of genes exceeding the threshold in each cell type separately or in total.  
- **Required correction** Clarify the statement to specify the exact criterion and whether the count is per cell type or across all cell types.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Section 2.4, Figure 3  
- **Evidence pointer** Section 2.4, Figure 3  
- **Issue** The Jaccard index is defined in the text, but the normalization procedure is not fully described. It is unclear how the indices are normalized "within the range (0, 1) across three cell types."  
- **Required correction** Provide a clear description of the normalization procedure, including the formula and any edge cases.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Methods section "Mouse brain scATAC-seq datasets"  
- **Evidence pointer** Methods section "Mouse brain scATAC-seq datasets"  
- **Issue** The methods for converting read counts to gene activities are described, but the exact parameters (e.g., the window size for summing reads around the TSS) are not specified.  
- **Required correction** Specify the exact parameters used for gene activity estimation, including the window size and any filtering criteria.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Section 2.7, Figure 5  
- **Evidence pointer** Section 2.7, Figure 5  
- **Issue** The description of the TF-MoDISCo analysis is brief, and it is unclear how the "enrichment of motifs nearby meta-analytic marker genes" was quantified.  
- **Required correction** Provide a more detailed description of the TF-MoDISCo analysis, including the input data, parameters, and how enrichment was defined.

- **Technical failings that need to be addressed before the case is established**  
  - R1-M1: Quantitative evidence for central claims is missing from the text.  
  - R1-M2: Deep learning model details are incomplete, and performance claims lack statistical rigor.  
  - R1-M3: Generalizability of the approach is not demonstrated beyond mouse brain data.

- **Assessment against Nature-style criteria**  
  - **Originality** The idea of using meta-analytic marker genes with redundancy for scATAC-seq annotation is a novel contribution, building on prior work in scRNA-seq. The systematic benchmarking across seven datasets adds value. However, the conceptual advance is incremental rather than transformative.  
  - **Scientific importance** The problem of robust cell-type annotation in scATAC-seq is important, and the findings could have practical implications for the field. The public resource is a valuable contribution. However, the importance is moderate, as the method is an extension of existing approaches rather than a fundamentally new paradigm.  
  - **Interdisciplinary readership** The work will appeal to computational biologists and bioinformaticians working on single-cell data, as well as experimentalists using scATAC-seq. The deep learning component may attract a broader machine learning audience, but the presentation is likely too specialized for a general readership.  
  - **Technical soundness** The methodological approach is sound in principle, but the evidence as presented is incomplete. The lack of quantitative details and the unavailability of figures and supplementary materials prevent a full assessment of technical rigor.  
  - **Readability for nonspecialists** The manuscript is written in a technical style that assumes familiarity with single-cell genomics and machine learning. The abstract is accessible, but the results and methods sections are likely challenging for nonspecialists. The key findings could be communicated more clearly with additional context and explanation.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses a relevant problem and presents a plausible approach, but the central claims are not fully supported by the available material. The authors should provide the missing quantitative data, complete the methodological details, and make the figures and supplementary materials available for review. If these concerns are addressed, the work could be a valuable contribution to the field.