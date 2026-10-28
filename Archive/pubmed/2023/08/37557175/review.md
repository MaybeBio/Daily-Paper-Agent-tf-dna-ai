## Review setup
- **Input scope** Full manuscript text including summary, introduction, results, discussion, limitations, and methods sections. Figures, tables, and supplementary materials are referenced but not provided.
- **Assessment boundary** Evaluation is limited to the scientific claims, methodology, and evidence as presented in the provided text. Experimental data, figures, and supplementary files are not directly assessable.
- **Shared manuscript claim summary** The authors propose that chromatin accessibility in the early Drosophila embryo is established through two distinct mechanisms: pioneering by the TF Zelda, which opens chromatin in proportion to motif affinity, and enhancer activation by patterning TFs, which further increases accessibility in a context-dependent manner. This is supported by deep learning models (BPNet and ChromBPNet) applied to ChIP-nexus and ATAC-seq data, with genetic validation in zld−, gd7, and cic6 mutant embryos.
- **Visible evidence base** Text descriptions of ChIP-nexus, ATAC-seq, MNase-seq, ChIP-seq, and protein-binding microarray experiments; model training and interpretation procedures; differential accessibility analyses; and referenced figures (Figures 1–6, S1–S6) and tables (Table S1). No raw data, numerical results, or figure panels are directly visible.
- **Missing materials affecting confidence** All figures, supplementary figures, tables, and datasets are absent. Quantitative results (e.g., correlation coefficients, fold changes, p-values) are described but not shown. Detailed model performance metrics and validation statistics are not directly verifiable.

## Reviewer
- **Overall assessment** This manuscript addresses a fundamental question in gene regulation: how transcription factors establish and modulate chromatin accessibility during development. The combination of high-resolution TF binding data, interpretable deep learning, and genetic validation is powerful and timely. The central claim that pioneering and enhancer activation represent separable processes with distinct sequence rules is well-motivated and supported by the described analyses. However, the absence of visible figures and quantitative data prevents full verification of the strength of the evidence. The distinction between Zelda's pioneering role and patterning TFs' activation-linked contributions is compelling, but the generalizability beyond Drosophila and the mechanistic details of how activation increases accessibility remain underexplored. The manuscript is well-written and accessible, though some technical aspects of the deep learning interpretation require careful reading.
- **Who would be interested in the results, and why** Researchers in gene regulation, developmental biology, chromatin biology, and computational biology would find this work highly relevant. Those studying pioneer factors, enhancer function, and zygotic genome activation would benefit directly. The methodological approach of combining interpretable deep learning with genetic validation will interest computational biologists developing models of cis-regulatory logic. The conceptual framework of two-tiered accessibility (pioneering vs. activation) has broad implications for understanding how TFs read out regulatory DNA across species.
- **Major strengths** The study integrates multiple high-quality genomic datasets (ChIP-nexus, ATAC-seq, MNase-seq, ChIP-seq) with state-of-the-art deep learning models to derive interpretable sequence rules. The use of genetic mutants (zld−, gd7, cic6) provides causal validation of the computational predictions. The distinction between pioneering and activation as separate contributors to accessibility is conceptually novel and well-supported by the described differential analyses. The inclusion of motif affinity as a quantitative predictor of pioneering strength is a notable advance. The manuscript is clearly written and the logic is easy to follow.
- **Major Concerns** The most significant concern is the lack of visible quantitative evidence. Key claims about correlation strengths, effect sizes, and statistical significance are described but not shown. The reliance on deep learning model interpretations without full details of model validation and potential biases is a concern. The generalizability of the two-tier model to other developmental contexts or organisms is not addressed experimentally. The mechanistic link between transcriptional activation and increased accessibility is inferred but not directly demonstrated. The exclusion of promoter-proximal regions from the accessibility model may limit the completeness of the conclusions.
- **Minor Comments** The manuscript would benefit from a clearer explanation of the "motif island" approach and its parameters. The distinction between "pioneering" and "activation" could be more precisely defined operationally. The limitations section is brief and could be expanded to address potential confounding factors in the differential accessibility analyses. The role of GAF as a pioneer is mentioned but not deeply explored, which may be a missed opportunity.
- **Technical failings that need to be addressed before the case is established** The absence of visible figures and quantitative data is a major technical failing in the context of this review. Without access to the actual data, the strength of the correlations, the magnitude of the effects, and the robustness of the model interpretations cannot be assessed. The description of the ChromBPNet bias correction is incomplete and relies on a separate unpublished manuscript, which is problematic for reproducibility. The validation of the deep learning models, particularly the cross-validation and stability analyses, is described but not demonstrated.
- **Assessment against Nature-style criteria** 
  - Originality: High. The two-tier model of accessibility (pioneering vs. activation) is a novel conceptual framework that challenges simpler views of TF-driven chromatin opening.
  - Scientific importance: High. Understanding how TFs establish accessibility is central to gene regulation; the findings have implications for development and disease.
  - Interdisciplinary readership: Moderate to high. The work bridges developmental biology, genomics, and machine learning, appealing to a broad audience.
  - Technical soundness: Moderate. The experimental design and computational approach are sound in principle, but the lack of visible data and incomplete method details prevent full assessment.
  - Readability for nonspecialists: Good. The manuscript is clearly written, with logical flow and accessible explanations of complex concepts, though the deep learning sections may be challenging for some readers.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual advance and experimental rigor are promising, but the evidence base must be fully visible and the methodological details clarified before the claims can be considered established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The authors claim that "Zelda consistently pioneers chromatin accessibility proportional to motif affinity" and that "patterning TFs augment chromatin accessibility in sequence contexts where they mediate enhancer activation."
- **Evidence pointer** Figures 2E, 2F, 3D–3G, 4D; location not provided for specific data points
- **Concern** The central claims rely on quantitative comparisons (e.g., correlation coefficients between motif affinity and accessibility contributions, fold-changes in accessibility upon genetic perturbation) that are described in the text but not visible in the provided material. Without access to the actual figures and numerical results, it is impossible to verify the magnitude and statistical significance of the reported effects. For example, the Pearson correlations for Zelda (0.59–0.64) are mentioned, but the scatter plots and confidence intervals are not shown. Similarly, the differential accessibility analyses in zld−, gd7, and cic6 mutants are described, but the effect sizes and significance thresholds are not presented.
- **Why it matters** The strength of the conclusions depends entirely on the quality and magnitude of the quantitative evidence. If the correlations are weak or the effect sizes are small, the claims of a two-tier model would be substantially weakened. The absence of visible data prevents the reader from assessing whether the evidence supports the conclusions.
- **Resolution test** Provide all figures and supplementary figures with clear annotations of statistical tests, effect sizes, and confidence intervals. Include the numerical values for all key comparisons (e.g., correlation coefficients, fold-changes, p-values) either in the main text or in accessible supplementary tables.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The authors state that ChromBPNet "predicts ATAC-seq data bias-free at base-resolution" and that the model was trained with a "frozen, pre-trained model that has already learned Tn5 sequence bias."
- **Evidence pointer** Methods section "ChromBPNet model training and optimization"; location not provided
- **Concern** The description of the ChromBPNet bias correction is incomplete. The authors refer to a "separate manuscript" for details, which is not available to the reader. This is a critical methodological component, as the interpretation of the accessibility model depends on the successful removal of Tn5 sequence bias. Without a full description of the bias model training, validation, and integration, the reproducibility of the approach is compromised.
- **Why it matters** The validity of the accessibility predictions and the subsequent interpretation of motif contributions hinge on the adequacy of the bias correction. If the bias model is not properly trained or validated, the inferred sequence rules could be artifacts of Tn5 bias rather than genuine regulatory logic.
- **Resolution test** Provide a complete description of the ChromBPNet bias correction, including the architecture, training data, validation metrics, and a demonstration that the bias model does not learn motif-related features. If the details are published elsewhere, provide a preprint or supplementary methods section that is self-contained.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors conclude that "chromatin accessibility occurs in two tiers: one through pioneering, which makes enhancers accessible but not necessarily active, and the second when the correct combination of TFs leads to enhancer activation."
- **Evidence pointer** Discussion section; location not provided
- **Concern** The two-tier model is derived from studies in the early Drosophila embryo, where Zelda is a dominant pioneer. The authors do not address whether this model applies to other developmental contexts, organisms, or TF families. The distinction between pioneering and activation may be specific to the rapid, synchronous zygotic genome activation in Drosophila, and the generalizability of the framework is unclear.
- **Why it matters** The claim of a general principle of the cis-regulatory code is ambitious. Without evidence from other systems, the model may be overgeneralized. The authors acknowledge this in the limitations but do not provide a clear path for testing the model's generality.
- **Resolution test** Add a discussion of how the two-tier model could be tested in other systems, or temper the claim to be specific to the Drosophila embryo. If possible, include preliminary analyses from other developmental contexts or TFs to support the generalizability.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic insight
- **Claim pointer** The authors propose that patterning TFs increase accessibility "through transactivation" and that this is distinct from pioneering.
- **Evidence pointer** Results section "Patterning TFs contribute to accessibility when mediating activation"; location not provided
- **Concern** The mechanistic link between transcriptional activation and increased accessibility is inferred from correlations (e.g., accessibility changes at activated vs. repressed enhancers) but not directly demonstrated. The authors do not show whether the increase in accessibility is a cause or consequence of transcriptional activation, nor do they identify the molecular mechanisms (e.g., recruitment of chromatin remodelers, histone modifications) by which activation leads to accessibility changes.
- **Why it matters** The claim that activation and pioneering are "functionally separable processes" requires mechanistic evidence. If the accessibility increase is simply a byproduct of transcription, the two-tier model would be less compelling.
- **Resolution test** Provide additional experiments or analyses that directly test the causal relationship between activation and accessibility, such as time-resolved measurements or perturbations that decouple TF binding from transcriptional activation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section "Motif extraction, motif curation, and motif island generation"
- **Evidence pointer** Location not provided
- **Issue** The "motif island" approach is described briefly, and the parameters for defining islands (e.g., initial 200-bp window, merging criteria) are not fully specified. The rationale for this approach and its potential limitations are not discussed.
- **Required correction** Provide a more detailed description of the island generation algorithm, including the criteria for merging and the sensitivity of the results to these parameters.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section "Patterning TFs contribute to accessibility when mediating activation"
- **Evidence pointer** Figure 5F; location not provided
- **Issue** The comparison of accessibility and gene expression at the tld and sog enhancers is compelling, but the interpretation could be strengthened by including additional enhancers or a more systematic analysis of the relationship between accessibility and expression across all enhancers.
- **Required correction** Consider adding a genome-wide analysis of the correlation between accessibility changes and expression changes in the mutant conditions to support the conclusions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion section
- **Evidence pointer** Location not provided
- **Issue** The discussion of the role of GAF is brief, and the authors do not fully explore why GAF does not promote the binding of other TFs despite being a pioneer. This is an interesting observation that could be discussed in more depth.
- **Required correction** Expand the discussion of GAF's distinct behavior and its implications for the two-tier model.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section "Data and code availability"
- **Evidence pointer** Location not provided
- **Issue** The availability of trained models and interpretation scripts is mentioned, but the specific versions and dependencies are not listed. This could hinder reproducibility.
- **Required correction** Provide a detailed list of software versions, dependencies, and a clear guide for reproducing the model training and interpretation steps.

## Risk / unsupported claims
- The claim that "Zelda consistently pioneers chromatin accessibility proportional to motif affinity" is supported by described analyses but not directly verifiable without figures and quantitative data.
- The claim that "patterning TFs augment chromatin accessibility in sequence contexts where they mediate enhancer activation" is inferred from differential accessibility analyses but the causal link to activation is not directly demonstrated.
- The claim that "chromatin accessibility occurs in two tiers" is presented as a general principle, but the evidence is limited to the Drosophila embryo and may not be generalizable.
- The claim that ChromBPNet predicts ATAC-seq data "bias-free" is not fully verifiable due to incomplete methodological details.
- The claim that "the thermodynamic differences between high and low-affinity sequences are very small at approximately −3 kcal/mol" is presented without a citation or direct measurement in this study.