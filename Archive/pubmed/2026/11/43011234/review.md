## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, and supplementary statements) as provided.
- **Assessment boundary** Scientific and technical evaluation of the scMINA workflow as described, including benchmarking claims, biological findings, and interpretability features. No evaluation of code execution, data availability beyond stated accessions, or reproducibility beyond what is described.
- **Shared manuscript claim summary** The authors present scMINA, a modular and interpretable workflow for paired scRNA-seq and scATAC-seq multiome integration and regulatory prioritization. They benchmark three integration methods (scPair, MultiVI, MOFA+) on a four-donor subset of the SEA-AD dataset, select scPair as the default, and apply the workflow to glial cells from 26 SEA-AD donors to identify AD-associated cell states, differentially expressed genes, and candidate regulatory networks. They further apply XAI-based feature attribution (Integrated Gradients, Path-Explainer) to prioritize genes and transcription factors in AD-enriched microglial and astrocyte subclusters.
- **Visible evidence base** Abstract; Introduction; Materials and Methods (dataset description, sample selection, benchmarking setup, model parameters); Results (benchmarking outcomes, glial cell clustering, DGE counts, subclustering, XAI prioritization, TF-DORC networks); Discussion; Conflict of interest; Funding; Data availability; Acknowledgements. No figures, tables, or supplementary materials were provided.
- **Missing materials affecting confidence** Figures 1–5 are referenced but not available. Supplementary tables, detailed benchmarking metric values, statistical test outputs, and code/configuration files are not provided. The full SEA-AD analysis parameters (e.g., Harmony parameters, clustering resolution, DGE model details) are only partially described.

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful modular workflow for paired single-cell multiome analysis, with a sensible emphasis on interpretability. The benchmarking of three integration methods on a well-defined subset is a reasonable contribution, and the application to SEA-AD glial cells demonstrates practical utility. However, the current evidence base is insufficient to fully evaluate the claims. Key figures and quantitative results are missing, the benchmarking is limited to a single dataset subset, and the biological findings are presented as candidate associations without validation. The workflow's novelty relative to existing tools is not clearly established. The manuscript is technically sound in its described methods but requires substantial additional evidence and clarification before the claims can be considered fully supported.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing or applying single-cell multiomic integration methods would be the primary audience. Researchers studying Alzheimer's disease at the single-cell level, particularly those interested in glial cell states and regulatory mechanisms, would also find the application relevant. The workflow's modular design and interpretability features may appeal to users seeking transparent alternatives to black-box deep learning approaches.
- **Major strengths**
  1. The workflow is modular and flexible, allowing users to substitute integration methods and enter at different analysis stages, which addresses a practical need in the field.
  2. The benchmarking of three distinct classes of integration methods (supervised deep learning, unsupervised deep learning, factorization) on a controlled subset is a systematic approach.
  3. The integration of XAI-based attribution with correlation-based regulatory inference (FigR) provides a multi-layered strategy for prioritizing candidate genes and TFs, which is a thoughtful design.
  4. The application to a large, publicly available dataset (SEA-AD) with balanced disease and sex representation lends practical credibility.
  5. The authors are appropriately cautious in framing findings as candidate associations rather than causal relationships.
- **Major Concerns**
  - **R1-M1** (Severity: Major, Blocking: Yes, Axis: Evidence completeness)
    - **Claim pointer** The manuscript claims that scMINA "robustly resolved major glial cell populations" and that benchmarking results demonstrate scPair's superiority across "most integration metrics."
    - **Evidence pointer** Results section, Figures 1–5 referenced but not provided; benchmarking metrics described qualitatively only.
    - **Concern** All key figures are referenced but not available for review. The benchmarking results are described in qualitative terms ("ranked highest," "outperformed") without specific numerical values, confidence intervals, or statistical tests. The clustering visualizations, DGE volcano plots, and XAI scatter plots cannot be assessed.
    - **Why it matters** The central claims of the manuscript depend on these visual and quantitative results. Without them, the performance of scMINA relative to alternatives and the biological findings cannot be independently evaluated.
    - **Resolution test** Provide all figures and supplementary tables with quantitative benchmarking metrics (ARI, NMI, ASW, cLISI, batchASW, FOSCTTM, PCC, SCC, auROC, 1-BCE) for each method, including variance estimates and statistical comparisons.
  - **R1-M2** (Severity: Major, Blocking: Yes, Axis: Benchmarking validity)
    - **Claim pointer** The manuscript states that scPair was selected as the default integration method based on "its previously demonstrated performance across diverse paired scRNA-seq/scATAC-seq datasets and its performance in the SEA-AD analysis presented here."
    - **Evidence pointer** Materials and Methods, "Selection of scPair for scMultiome integration"; Results, "Benchmarking single cell multiomics integration methods."
    - **Concern** The benchmarking is performed on a single subset of four donors from one dataset. The authors cite prior work for scPair's general performance, but the selection of scPair as the default within scMINA is primarily justified by this limited comparison. The benchmarking does not include other popular integration methods beyond the three tested, and the choice of hyperparameters for each method may not be optimal.
    - **Why it matters** The default integration method is a core component of the workflow. A limited benchmarking on one dataset subset may not generalize to other datasets, tissues, or conditions, potentially limiting the workflow's broader applicability.
    - **Resolution test** Expand benchmarking to additional datasets or provide a more thorough justification for the generalizability of the current results. Include sensitivity analyses for hyperparameter choices and discuss potential limitations of the single-dataset evaluation.
  - **R1-M3** (Severity: Major, Blocking: No, Axis: Biological validation)
    - **Claim pointer** The manuscript identifies AD-enriched subclusters in microglia and astrocytes and prioritizes candidate genes and TFs, including HIF-1α and ZNF-family TFs in microglia and JUN, FOSL2, and PPARA in astrocytes.
    - **Evidence pointer** Results, "Explainable AI-based signature discovery prioritizes key genes in AD-specific cell states."
    - **Concern** The biological findings are presented as candidate associations with literature support, but no experimental validation or orthogonal confirmation is provided. The overlap between XAI and DGE/DORC results is described but not quantified. The specificity of these findings to AD versus other conditions is not addressed.
    - **Why it matters** The manuscript positions these findings as hypothesis-generating, which is appropriate, but the lack of any validation limits the strength of the biological claims. The clinical or mechanistic significance of the prioritized candidates remains unclear.
    - **Resolution test** Provide quantitative overlap statistics between XAI, DGE, and DORC results. If possible, include validation experiments (e.g., perturbation assays, independent dataset replication) or clearly state that such validation is beyond the scope of the current manuscript.
  - **R1-M4** (Severity: Major, Blocking: No, Axis: Technical reproducibility)
    - **Claim pointer** The manuscript states that the workflow is implemented using Nextflow DSL2 with Conda-managed dependencies and that random seeds were fixed "where supported."
    - **Evidence pointer** Materials and Methods, "Workflow implementation and reproducibility."
    - **Concern** The description of reproducibility measures is incomplete. It is unclear which steps support random seed fixing and which do not. The specific versions of all software packages are not listed. The statement that "the same random seed and parameter settings were used across the reported analyses" is vague.
    - **Why it matters** Reproducibility is a stated goal of the workflow, but the current description does not provide sufficient detail for users to replicate the analyses or assess the potential impact of stochastic variability.
    - **Resolution test** Provide a complete list of software versions, specify which steps use fixed seeds and which do not, and describe the potential impact of stochasticity on results. Include a configuration file or environment specification as supplementary material.
  - **R1-M5** (Severity: Major, Blocking: No, Axis: Statistical rigor)
    - **Claim pointer** DGE analysis identified specific numbers of upregulated and downregulated genes per cell type (e.g., 165 upregulated and 163 downregulated in astrocytes).
    - **Evidence pointer** Results, "Conventional downstream analysis workflow reveals glial cell diversity and cell type-specific transcriptome dysregulation in AD."
    - **Concern** The DGE analysis uses a threshold of adjusted P < .05 and |log2 fold change| > 1, but the statistical model, covariates, and multiple testing correction method are not fully described. The MAST method is mentioned, but the specific implementation and any additional covariates (e.g., sex, age, batch) are not detailed.
    - **Why it matters** The DGE results are a key output of the workflow and are used to support biological interpretations. Without clear statistical details, the reliability of these findings cannot be assessed.
    - **Resolution test** Provide full details of the DGE model, including covariates, random effects, and multiple testing correction. Report effect sizes and confidence intervals for key genes.
- **Minor Comments**
  - **R1-m1** (Severity: Minor, Axis: Clarity, Affected Element: Abstract, Evidence Pointer: Abstract)
    - **Issue** The abstract states that scMINA "robustly resolved major glial cell populations" but does not specify which populations or how robustness was measured.
    - **Required correction** Briefly specify the resolved populations and the metrics used to assess robustness.
  - **R1-m2** (Severity: Minor, Axis: Completeness, Affected Element: Methods, Evidence Pointer: Materials and Methods, "Dataset description")
    - **Issue** The dataset description mentions 98,601 cells from 16 normal donors and 52,755 cells from 12 dementia donors, but the final analysis used 25,054 cells from 26 donors. The filtering steps between these numbers are not fully explained.
    - **Required correction** Provide a clear flow of cell and donor numbers through each filtering step.
  - **R1-m3** (Severity: Minor, Axis: Clarity, Affected Element: Methods, Evidence Pointer: Materials and Methods, "Benchmarking scMultiome integration methods")
    - **Issue** The description of scPair hyperparameters is incomplete. The sentence "We set the learning rate to 0.001, batch size to 300, and employed batch normalization and layer normalization with GELU activation function" contains a grammatical error ("and. For the output").
    - **Required correction** Fix the grammatical error and provide a complete list of hyperparameters for all three methods.
  - **R1-m4** (Severity: Minor, Axis: Interpretation, Affected Element: Results, Evidence Pointer: Results, "Benchmarking single cell multiomics integration methods")
    - **Issue** The benchmarking results are described qualitatively. Specific values for ARI, NMI, ASW, etc., are not provided in the text.
    - **Required correction** Include a supplementary table with all metric values for each method.
  - **R1-m5** (Severity: Minor, Axis: Clarity, Affected Element: Results, Evidence Pointer: Results, "Explainable AI-based signature discovery prioritizes key genes in AD-specific cell states")
    - **Issue** The criteria for selecting "top 100 highly attributed features per method per cluster" are not described. It is unclear whether this is based on absolute attribution scores or rank.
    - **Required correction** Clarify the selection criteria and whether scores were normalized across features or clusters.
  - **R1-m6** (Severity: Minor, Axis: Completeness, Affected Element: Discussion, Evidence Pointer: Discussion)
    - **Issue** The discussion mentions that scMINA "can be adapted to other paired single-cell multiome datasets" but does not discuss potential challenges or limitations of such adaptation.
    - **Required correction** Add a brief discussion of potential challenges (e.g., dataset-specific parameter tuning, computational cost).
- **Technical failings that need to be addressed before the case is established**
  1. Missing figures and quantitative benchmarking results (R1-M1).
  2. Limited benchmarking scope and justification for scPair as default (R1-M2).
  3. Incomplete statistical details for DGE analysis (R1-M5).
  4. Insufficient reproducibility documentation (R1-M4).
- **Assessment against Nature-style criteria**
  - **Originality** Moderate. The combination of existing methods (scPair, FigR, XAI) into a modular workflow is useful but not conceptually novel. The XAI application to multiome integration is relatively underexplored, which adds some originality.
  - **Scientific importance** Moderate. The workflow addresses a real need for interpretable multiome analysis, and the SEA-AD application is relevant to a major disease. However, the biological findings are candidate-level and do not yet provide new mechanistic insights.
  - **Interdisciplinary readership** Limited. The manuscript is primarily of interest to computational biologists and bioinformaticians. The biological findings may attract AD researchers, but the technical focus may limit broader appeal.
  - **Technical soundness** Partially established. The described methods are reasonable, but the missing figures and quantitative results prevent full assessment. The benchmarking is limited in scope, and statistical details are incomplete.
  - **Readability for nonspecialists** Adequate. The manuscript is generally well-written and explains concepts clearly, but the methods section assumes familiarity with single-cell multiomic techniques and deep learning.
- **Recommendation posture** Supportive if technical concerns are resolved. The workflow has potential utility, and the authors have made a reasonable effort to address interpretability. However, the current evidence base is insufficient to fully support the claims. The authors should provide all figures and quantitative results, expand the benchmarking justification, and clarify statistical and reproducibility details. With these revisions, the manuscript could make a solid contribution to the field.

## Risk / unsupported claims
- The claim that scMINA "robustly resolved major glial cell populations" is unsupported without the referenced figures and quantitative clustering metrics.
- The claim that scPair "outperformed" MultiVI and MOFA+ is unsupported without specific metric values and statistical comparisons.
- The claim that XAI-based attribution and DGE/DORC analyses provide "complementary computational evidence" is not quantified; the degree of overlap is not reported.
- The biological significance of prioritized genes and TFs (e.g., HIF-1α, PPARA) is presented with literature support but is not validated in this study; these should be clearly framed as hypotheses.
- The generalizability of scMINA to other datasets is asserted but not demonstrated beyond the SEA-AD example.