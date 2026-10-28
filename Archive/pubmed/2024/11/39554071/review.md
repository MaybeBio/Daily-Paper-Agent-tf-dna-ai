## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided; no figures, tables, or supplementary material were available for inspection.
- **Assessment boundary** This review evaluates the scientific claims, methodological soundness, and evidentiary support based solely on the text supplied. Figures, tables, and supplementary files referenced in the text were not provided and therefore could not be independently assessed.
- **Shared manuscript claim summary** The authors present a multiomic single-nucleus ATAC-seq and RNA-seq atlas of systemic sclerosis-associated interstitial lung disease (SSc-ILD) and control lungs. They use ChromBPNet to infer transcription factor (TF) binding at single-base-pair resolution and a novel algorithm, HALO, to construct TF-regulatory element-gene networks. They report altered chromatin accessibility and enhanced binding of AP-1, RUNX, and EGR TFs in fibrotic fibroblasts, and bHLH-ZIP and AP-1 TFs in SPP1hi macrophages, implicating these TFs in driving profibrotic gene programs.
- **Visible evidence base** Text descriptions of results, including cell clustering statistics, differential accessibility counts, TF motif enrichment analyses, pathway enrichment results, and network construction details. Methods sections describe computational pipelines in reasonable detail.
- **Missing materials affecting confidence** All figures, supplementary figures, supplementary tables, and supplementary methods. Specific quantitative results (e.g., effect sizes, confidence intervals, validation metrics for ChromBPNet and HALO) are referenced but not shown. The independent scRNA-seq dataset (17 SSc, 13 control) is cited as previously published but not described in this manuscript.

## Reviewer
- **Overall assessment** This manuscript addresses an important gap in pulmonary fibrosis research by providing a chromatin-level view of TF dynamics in SSc-ILD. The combination of ChromBPNet and HALO is methodologically ambitious and potentially valuable. However, the current text does not provide sufficient evidence to fully evaluate the validity of the key claims. Critical validation steps, quantitative comparisons, and figure-based evidence are missing. The claims of "driving" fibrosis are not supported by functional experiments, and the causal language exceeds what the descriptive, correlative data can establish. The manuscript is promising but requires substantial additional evidence and revision before the central conclusions can be considered established.
- **Who would be interested in the results, and why** Researchers studying pulmonary fibrosis, systemic sclerosis, and fibrotic diseases more broadly would be interested in the chromatin-level regulatory map. Computational biologists developing or applying deep learning methods for TF binding inference would also find the ChromBPNet application relevant. Those interested in macrophage-fibroblast crosstalk and the transcriptional control of profibrotic states would benefit from the proposed TF networks. The resource value of a multiomic lung atlas could attract a wider community of lung biologists.
- **Major strengths**
  - Addresses a significant gap: limited understanding of transcriptional regulatory mechanisms in fibrotic lung disease at single-cell resolution.
  - Integrates multiple state-of-the-art computational tools (ChromBPNet, HALO, DIRECT-NET) in a coherent analytical framework.
  - Focuses on clinically relevant cell populations (myofibroblasts, SPP1hi macrophages) with established roles in fibrosis.
  - Provides a publicly available resource (atlas) that could enable downstream hypothesis generation.
  - The discussion thoughtfully contextualizes findings within existing literature on AP-1, RUNX, and EGR in fibrosis.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract and results state that ChromBPNet inferred "increased TF binding at single base pair resolution" and that this reflects "altered TF dynamics" in disease.
- **Evidence pointer** Results section "Enhanced binding of AP-1, RUNX and EGR transcription factors by fibrotic fibroblasts"; Figure 3 (not provided)
- **Concern** The central claim of altered TF binding rests entirely on ChromBPNet contribution scores. No validation is presented to show that these inferred binding changes correspond to actual TF occupancy. The text does not report any orthogonal validation (e.g., ChIP-seq, ATAC-seq footprinting with independent methods, or perturbation experiments). The manuscript also does not provide quantitative metrics for ChromBPNet model performance (e.g., AUC, correlation with held-out data) on these specific cell types.
- **Why it matters** ChromBPNet is a predictive model, and its outputs are inferences, not direct measurements. Without validation, the claim that AP-1, RUNX, and EGR binding is "enhanced" in disease cannot be distinguished from model artifact or bias. This is the foundational claim of the paper, and if it is not robust, the downstream network construction and biological interpretations are compromised.
- **Resolution test** Provide orthogonal validation of at least a subset of predicted TF binding changes, such as ChIP-seq for AP-1 (e.g., JUN or FOS) and RUNX family members in sorted fibroblast populations from SSc-ILD and control lungs. Alternatively, perform CRISPR-based perturbation of candidate TFs in fibroblast or macrophage models and show that chromatin accessibility and target gene expression change as predicted. Report ChromBPNet performance metrics on held-out chromosomes or cell types.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The title states that altered TF dynamics "drive" fibrotic lung disease, and the discussion claims these TFs are "regulating the transition of fibroblasts and macrophages to profibrotic states."
- **Evidence pointer** Title; Discussion section
- **Concern** The study is entirely descriptive and correlative. No functional experiments are presented to demonstrate that AP-1, RUNX, or EGR activity is necessary or sufficient for the profibrotic phenotype. The word "drive" implies causation, which cannot be established from observational chromatin accessibility data alone. The discussion acknowledges the need for "functional validation" but the title and framing overstate the current evidence.
- **Why it matters** Causal language in the title and abstract will influence how the broader community interprets and cites this work. Overstating causal relationships from correlative data can mislead subsequent research directions and clinical reasoning. The distinction between correlation and causation is fundamental to scientific integrity.
- **Resolution test** Either temper the language throughout to reflect the descriptive nature of the findings (e.g., "associated with" or "implicated in"), or add functional experiments such as TF knockdown or overexpression in primary lung fibroblasts or macrophages, followed by assessment of profibrotic gene expression, collagen production, and myofibroblast differentiation. In vivo validation in a fibrosis model (e.g., bleomycin) with TF modulation would strengthen the causal claim.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validation
- **Claim pointer** The manuscript states that HALO "confirmed AP-1, RUNX, and EGR TF activity controlling profibrotic gene programs and established TF-regulatory element-gene networks."
- **Evidence pointer** Results section "Gene regulatory network construction"; Figure 6 (not provided)
- **Concern** HALO is described as a "novel algorithm," but no details are provided on its architecture, training procedure, hyperparameters, or validation against existing methods. The claim that it "confirmed" findings from ChromBPNet is circular if both methods rely on the same underlying data and similar assumptions. No comparison to established network inference tools (e.g., SCENIC, Pando) is presented.
- **Why it matters** A novel algorithm must be rigorously benchmarked to establish its reliability. Without such validation, the network predictions cannot be trusted, and the claim of "confirmation" is misleading. The field needs to know whether HALO provides genuine advances or merely recapitulates existing approaches with different branding.
- **Resolution test** Provide a detailed description of HALO's architecture and training. Benchmark HALO against at least two established methods on the same data, reporting quantitative metrics such as precision, recall, and reproducibility. Show that HALO's predictions are robust to parameter choices and that the "confirmation" of ChromBPNet results is not an artifact of shared methodology.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Sample size and generalizability
- **Claim pointer** The study uses 3 SSc-ILD and 2 control samples for scRNA-seq/snATAC-seq, and 6 SSc-ILD and 7 control samples for multiome analysis.
- **Evidence pointer** Results section "Epigenomic markers of healthy and SSc-ILD lung cell populations"; Supplementary Table 1 (not provided)
- **Concern** The sample sizes are small, and the manuscript does not report biological or technical replicates within individuals. SSc-ILD is a heterogeneous disease, and the observed chromatin changes may reflect a subset of patients or specific disease stages. The text does not discuss how patient heterogeneity (e.g., disease duration, immunosuppressive treatment, smoking history) might affect the results.
- **Why it matters** Small sample sizes increase the risk of false positives and limit generalizability. If the findings are to inform therapeutic development, they must be robust across the spectrum of SSc-ILD. The lack of clinical metadata makes it impossible to assess confounding factors.
- **Resolution test** Report detailed clinical characteristics of all patients and donors. Perform power calculations to justify sample sizes. If possible, validate key findings in an independent cohort or in publicly available datasets. Discuss how disease heterogeneity might influence the results and whether the findings are consistent across patients.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor
- **Claim pointer** The results describe "6,002 DARS more accessible in SSc vs 6,693 in control fibroblasts" and "42 DARS" in a specific comparison, but no statistical thresholds, effect sizes, or confidence intervals are reported in the text.
- **Evidence pointer** Results section "Altered Chromatin accessibility of fibrotic mesenchymal cell populations in SSc-ILD"; Supplementary Tables 2 and 3 (not provided)
- **Concern** The manuscript does not report adjusted p-values, false discovery rates, or effect sizes for the differential accessibility and expression analyses. The text mentions "adjusted p-value <0.05" in the methods but does not present the actual numbers in the results. Without these, the reader cannot assess the strength of the evidence.
- **Why it matters** Quantitative rigor is essential for reproducibility. The field has moved toward reporting effect sizes and uncertainty measures, and the absence of these details weakens the manuscript's credibility.
- **Resolution test** Include a supplementary table with all differential accessibility and expression results, including log2 fold changes, adjusted p-values, and confidence intervals. Report the number of tests performed and the FDR threshold used. Consider adding volcano plots or MA plots as figures.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "limited insight into transcriptional control of profibrotic gene programs" but does not specify what the study adds beyond this. The phrase "TF action atlas" is vague.
- **Required correction** Clarify the specific novel contributions, such as the identification of particular TF binding changes at base-pair resolution and the construction of cell-type-specific regulatory networks.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, ChromBPNet Analysis
- **Evidence pointer** Methods section "ChromBPNet Analysis"
- **Issue** The description of ChromBPNet training is brief. Key parameters such as genome build, sequence length, number of training epochs, and computational resources are not specified.
- **Required correction** Provide a complete description of the training procedure, including all hyperparameters, to enable replication.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, macrophage section
- **Evidence pointer** Results section "Altered Chromatin accessibility of macrophage populations in SSc-ILD"
- **Issue** The text states that bHLH-ZIP TFs were "mildly increased" in SSc macrophages, but the biological significance of a mild increase is unclear.
- **Required correction** Provide quantitative data on the magnitude of the change and discuss whether this is likely to be biologically meaningful.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion does not address potential limitations of the computational approach, such as the inability of ATAC-seq to distinguish between TF binding and nucleosome positioning, or the challenges of motif-based inference when TFs share binding sites.
- **Required correction** Add a limitations paragraph that acknowledges these issues and explains how they might affect the conclusions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Data availability
- **Evidence pointer** Methods section
- **Issue** No statement is provided regarding data availability or code availability.
- **Required correction** Add a data and code availability statement, including accession numbers for raw sequencing data and links to software repositories.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of validation for ChromBPNet predictions
  - R1-M2: Causal language not supported by experimental evidence
  - R1-M3: HALO not adequately described or benchmarked
  - R1-M4: Small sample size without clinical metadata or power analysis
  - R1-M5: Missing quantitative statistics for key results

- **Assessment against Nature-style criteria**
  - Originality: The application of ChromBPNet to fibrotic lung tissue and the integration with HALO for network construction is novel. However, the individual components (ATAC-seq, TF motif analysis, network inference) are established. The originality lies in the combination and the disease context.
  - Scientific importance: Understanding the transcriptional regulation of profibrotic cells is important for developing new therapies for SSc-ILD and other fibrotic diseases. The potential resource value of the atlas is significant. However, the importance is diminished by the lack of functional validation.
  - Interdisciplinary readership: The work bridges computational biology, genomics, and pulmonary medicine. It could appeal to researchers in each of these fields, but the technical complexity may limit accessibility to clinicians without computational training.
  - Technical soundness: The computational pipeline is sophisticated, but the lack of validation and benchmarking for the key tools (ChromBPNet, HALO) is a significant concern. The statistical reporting is incomplete.
  - Readability for nonspecialists: The manuscript is written in a technical style that assumes familiarity with single-cell genomics and deep learning. The abstract is accessible, but the results and methods would be challenging for a general scientific audience. The authors should consider adding a graphical summary or plain-language explanations of key concepts.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important question and presents a potentially valuable resource. However, the current evidence does not establish the central claims of enhanced TF binding and causal roles in fibrosis. The authors must provide validation of the computational predictions, temper the causal language, and report quantitative statistics before the case is made.