## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Discussion, Methods, Supplementary table legends)
- **Assessment boundary** Scientific content, methodological rigor, and claims as presented in the provided text. No line numbers were provided; references to specific locations are by section or figure/table name.
- **Shared manuscript claim summary** The authors present a comprehensive reanalysis of 74 bHLH transcription factor induction ChIP-seq datasets covering 17 factors, integrated with chromatin accessibility, methylation, nucleosome positioning, transcriptomics, and structural modeling. They claim to define a unified DNA-binding syntax for bHLH factors, identify subclass-specific E-box usage associated with chromatin remodeling capacity, and propose a methylation-driven model for MYC enhancer invasion in cancer.
- **Visible evidence base** Abstract, Introduction, Results (section headings and narrative), Discussion, Methods, and supplementary table legends. No figures or tables were provided for direct inspection.
- **Missing materials affecting confidence** All figures (Fig. 1-5, Fig. S1-S8) and supplementary tables (Table S1-S6) are referenced but not provided. Statistical details, effect sizes, and quality control metrics for the ChIP-seq datasets are not visible. The exact composition of the 74 datasets and the criteria for dataset inclusion beyond the described K-S test are not fully assessable.

## Reviewer
- **Overall assessment** This manuscript addresses a significant and timely question in transcription factor biology: how bHLH factors achieve specificity in DNA binding and chromatin remodeling. The authors have assembled a substantial dataset and propose a framework that could be of broad interest. However, the current presentation, based on the text alone, does not fully establish the central claims. The reliance on reanalyzed public data without visible quality metrics, the correlational nature of the analyses, and the absence of direct experimental validation for the proposed mechanistic models (particularly the methylation-driven MYC model) leave key conclusions under-supported. The manuscript is ambitious and the conceptual framework is appealing, but the evidence as presented is insufficient to fully substantiate the claims of a unified and predictive model.
- **Who would be interested in the results, and why** Researchers studying transcription factor biology, chromatin structure and remodeling, cell fate determination and reprogramming, and cancer genomics. The proposed framework for linking DNA-binding syntax to chromatin engagement could be of interest to computational biologists developing predictive models of TF function. The specific findings on MYC and HEY family behavior in methylated contexts may be relevant to cancer biologists studying enhancer deregulation.
- **Major strengths**
  1. The assembly and integration of a large number of induction ChIP-seq datasets (74 experiments, 17 factors) is a valuable resource and represents a significant analytical effort.
  2. The study addresses a fundamental question with broad implications, moving beyond single-factor analyses to a family-wide comparison.
  3. The integration of multiple data types (ChIP-seq, ATAC-seq, methylation, RNA-seq, structural modeling) is a comprehensive approach.
  4. The proposed framework, if validated, could provide a predictive basis for understanding bHLH factor behavior in development and disease.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness / Data quality
  - **Claim pointer** The authors claim to have identified 74 high-quality ChIP-seq datasets based on "significant E-box centrality compared to a uniform distribution" and retained these for analysis.
  - **Evidence pointer** Results section "Collection of bHLH ChIP-seq data from induction experiments"; Fig. S1A
  - **Concern** The quality control metric for dataset inclusion is described only as a K-S test for E-box centrality. This is a necessary but not sufficient criterion for ChIP-seq data quality. The text does not provide details on the number of peaks per dataset, the fraction of reads in peaks (FRiP), signal-to-noise ratios, or how batch effects across the many different source laboratories were handled. The exclusion of the bottom 15 experiments based on this single metric is arbitrary without further justification. The robustness of all downstream conclusions depends on the quality and comparability of these input datasets.
  - **Why it matters** If the input datasets are of variable quality or contain systematic biases, the derived conclusions about E-box usage, chromatin remodeling capacity, and transcriptional outcomes could be artifacts of data quality differences rather than genuine biological properties of the TFs.
  - **Resolution test** Provide a supplementary figure showing the distribution of key quality metrics (e.g., number of peaks, FRiP scores, or similar) for all 89 identified datasets, with the 74 retained and 15 excluded clearly marked. Demonstrate that the retained datasets are of comparable quality and that the exclusion does not bias the results. Show that the K-S test statistic correlates with other quality measures.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance / Support for central model
  - **Claim pointer** The authors propose a "methylation-driven model explaining MYC enhancer invasion" where DNA methylation redirects MYC binding from CAC-CAC to CAT-CAC motifs in highly methylated enhancer regions.
  - **Evidence pointer** Results section "bHLH interaction with methylated DNA"; Fig. 3A, 3B, Fig. S5A, S5B
  - **Concern** The causal direction of this model is not established. The data presented are correlational: MYC binding in highly methylated regions is associated with CAT-CAC motif usage. The claim that methylation "drives" this shift requires demonstrating that methylation directly alters MYC's intrinsic DNA-binding preference. The in vitro methyl-SELEX data (Fig. 3A) are critical here, but the text does not describe the experimental conditions or whether the shift observed in vitro quantitatively matches the in vivo observations. Furthermore, the possibility that other factors (e.g., chromatin state, cofactor availability) are responsible for the observed correlation is not addressed.
  - **Why it matters** This is a central mechanistic claim of the paper and has implications for understanding MYC function in cancer. If the causal link is not established, the model remains speculative and the broader conclusions about MYC enhancer invasion are weakened.
  - **Resolution test** Provide a clear description of the methyl-SELEX experimental design and results, including whether the methylation-induced shift in motif preference is specific to MYC/HEY or general. Perform a statistical test to show that the enrichment of CAT-CAC in methylated regions is not explained by confounding variables (e.g., motif density, chromatin state). Consider a direct experimental test, such as in vitro binding assays with methylated versus unmethylated DNA substrates, to demonstrate causality.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness / Support for conclusions
  - **Claim pointer** The authors state that "CAT- and CAG-preferring bHLH factors—including proneural and myogenic regulators—display robust pioneer-like behavior" and that this is a shared property of these subclasses.
  - **Evidence pointer** Results sections "DNA binding features vary with chromatin accessibility" and "Global chromatin-remodeling capacity across bHLH subclasses"; Fig. 2A, 2B, Fig. 5A
  - **Concern** The definition of "pioneer-like behavior" is operationalized as binding to low-accessibility chromatin and inducing chromatin remodeling. However, the analysis appears to be entirely correlational, based on pre- and post-induction accessibility data. The text does not describe how the authors distinguish between direct pioneer activity (binding to closed chromatin and initiating opening) and indirect effects (e.g., binding to nucleosome-free regions that become accessible due to other factors). The multivariate regression framework is mentioned, but the specific results, effect sizes, and model fit statistics are not presented. The claim that this is a "shared property" of the entire subclass is a strong generalization that requires demonstrating consistency across all factors within the subclass and across all cellular contexts.
  - **Why it matters** The concept of pioneer activity is central to the paper's framework. If the evidence is only correlational and does not distinguish direct from indirect effects, the claim of a "shared property" is overstated and the proposed model of pioneer activity may be incorrect.
  - **Resolution test** Provide the full results of the multivariate regression models, including coefficients, confidence intervals, and p-values for all factors and motifs. Show that the association between motif usage and remodeling is not confounded by baseline accessibility. Discuss how the analysis distinguishes direct pioneer activity from indirect effects, or acknowledge this limitation explicitly. Consider analyzing a subset of factors with known pioneer activity (e.g., ASCL1, NEUROG2) as positive controls and factors without pioneer activity as negative controls.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interdisciplinary readership / Readability for nonspecialists
  - **Claim pointer** The manuscript claims to provide a "unified framework" and "mechanistic principles" for bHLH function.
  - **Evidence pointer** Abstract; Discussion
  - **Concern** The manuscript is dense and assumes significant prior knowledge of the bHLH field, ChIP-seq analysis, and chromatin biology. The Results section is presented as a series of section headings without a clear narrative flow or a summary of the key findings at the end of each subsection. The Discussion introduces new concepts (e.g., "breathing mode") and references to prior work without sufficient context. A nonspecialist reader would struggle to understand the significance of the findings and the validity of the proposed model.
  - **Why it matters** For a journal with a broad readership, the manuscript must be accessible to scientists outside the immediate field. The current presentation limits the impact and reach of the work.
  - **Resolution test** Restructure the Results to include a brief summary paragraph at the end of each subsection. Expand the Discussion to provide more context for the proposed model and its implications. Define all specialized terms (e.g., "pioneer factor," "breathing mode") on first use. Consider adding a schematic figure that summarizes the proposed model of bHLH DNA-binding syntax and chromatin remodeling.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and precision
  - **Affected element** Abstract; Results section "E-box usage and motif centrality across bHLH subfamilies"
  - **Evidence pointer** Abstract; Fig. 1A
  - **Issue** The term "exact hexanucleotide–based approach" is used but not defined. It is unclear whether this refers to a k-mer-based approach, a position weight matrix approach, or something else.
  - **Required correction** Define the approach clearly in the Methods and briefly in the Results or Abstract.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results section "Motif clustering, spacing and local cooperativity"
  - **Evidence pointer** Fig. 1C, Fig. S3A
  - **Issue** The comparison of motif clustering in ChIP-seq peaks versus "size-matched peak flanking regions" is mentioned, but the statistical test used to assess significance is not described.
  - **Required correction** Specify the statistical test used for the comparison and report the relevant statistics (e.g., p-values, effect sizes).
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods section "Transcriptomic Analysis"
  - **Evidence pointer** Methods
  - **Issue** The description of the RNA-seq analysis is brief. Details on the alignment parameters, quantification method, and differential expression thresholds are not provided.
  - **Required correction** Provide a more detailed description of the RNA-seq analysis pipeline, including software versions and parameters.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data presentation
  - **Affected element** Results section "Global chromatin-remodeling capacity across bHLH subclasses"
  - **Evidence pointer** Fig. 5A, Fig. S6A
  - **Issue** The claim that "CAT- and CAG-preferring factors...exert detectable chromatin-remodeling activity across all cellular contexts tested" is a strong statement. It is unclear how many cellular contexts were tested and whether the effect size was consistent.
  - **Required correction** Provide a summary of the number of cellular contexts and the range of effect sizes observed. Consider softening the claim if the effect sizes are variable.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Discussion section "A reevaluation of the model of bHLH nucleosome interaction"
  - **Evidence pointer** Discussion
  - **Issue** The discussion of the "breathing mode" and its relevance to bHLH factors would benefit from a more explicit description of the model and its predictions.
  - **Required correction** Provide a brief explanation of the "breathing mode" model and how the current results support or challenge it.
- **Technical failings that need to be addressed before the case is established**
  1. Lack of visible quality metrics for the 74 ChIP-seq datasets (R1-M1).
  2. The causal claim for the methylation-driven MYC model is not supported by the presented evidence (R1-M2).
  3. The operationalization of "pioneer-like behavior" is not clearly distinguished from indirect effects (R1-M3).
  4. The statistical framework for the multivariate regression is described but results are not presented (R1-M3).
- **Assessment against Nature-style criteria**
  - **Originality** The manuscript presents a novel synthesis of existing data and proposes a unified framework for bHLH DNA-binding syntax. The concept of linking specific E-box variants to chromatin remodeling capacity across a family of TFs is original and goes beyond previous single-factor studies. The proposed methylation-driven model for MYC enhancer invasion is a new hypothesis.
  - **Scientific importance** The question of how TFs achieve specificity in chromatin engagement is of fundamental importance. A validated framework for predicting bHLH factor behavior would have significant implications for developmental biology, reprogramming, and cancer research. The potential clinical relevance of the MYC findings adds to the importance.
  - **Interdisciplinary readership** The topic is of interest to molecular biologists, developmental biologists, cancer biologists, and computational biologists. However, the current presentation is not accessible to a broad readership and requires significant background knowledge.
  - **Technical soundness** The analytical approach is ambitious and integrative, but the lack of visible quality control metrics and the correlational nature of the key analyses are significant weaknesses. The causal claims, particularly for the methylation model, are not supported by the evidence presented.
  - **Readability for nonspecialists** The manuscript is dense and assumes significant prior knowledge. The Results section lacks a clear narrative flow, and the Discussion introduces new concepts without sufficient context.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important question and presents a potentially valuable framework. However, the current evidence is insufficient to fully establish the central claims. The authors must provide a more rigorous demonstration of data quality, clarify the distinction between direct and indirect effects in the pioneer activity analysis, and provide stronger evidence for the causal role of DNA methylation in MYC enhancer invasion. The manuscript would also benefit from improved accessibility for a broader readership.

## Risk / unsupported claims
- The claim that "CAT- and CAG-preferring bHLH factors...display robust pioneer-like behavior" is not fully supported by the presented evidence, as the analysis does not clearly distinguish direct pioneer activity from indirect effects.
- The claim that "DNA methylation drives a systematic shift from the canonical CAC–CAC motif toward CAT–CAC E-boxes" is presented as a mechanistic model, but the causal direction is not established by the correlational data.
- The claim that "nearly all factors disfavored a T in this position" is a general statement that may not hold for all factors and contexts; the data supporting this are not shown.
- The claim that the "expansion" of the binding landscape after overexpression is "mediated by binding to their cognate E-box motifs" is not fully supported, as the text does not rule out non-specific or off-target binding contributing to the expansion.
- The statement that the framework will "serve to predict, model, and potentially modulate bHLH–chromatin interactions" is a forward-looking claim that is not directly supported by the data presented.