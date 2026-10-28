## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and figure legends (as provided)
- **Assessment boundary** Scientific content, methodological rigor, data interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors report that acute pharmacological inhibition of BAF chromatin remodeling complexes in GM12878 lymphoblastoid cells causes rapid, widespread loss of chromatin accessibility, particularly at primed enhancers (H3K4me1+/H3K27ac-). Using machine learning on ChIP-seq data, they identify AP-1 factors and lineage-specific TFs as predictors of BAF dependence. They further show that BAF inhibition suppresses chromatin and transcriptional responses to interferon gamma and dexamethasone, concluding that continuous BAF activity is required for stimulus-responsive gene regulation.
- **Visible evidence base** Main text figures (Figure 1-6 as referenced), supplemental figures and tables (as referenced), methods section
- **Missing materials affecting confidence** Actual figure images and data values are not provided; only figure legends and text descriptions. Statistical details (exact p-values, effect sizes, confidence intervals) are partially reported. No raw data or code output is visible for independent verification.

## Reviewer

### Overall assessment
This manuscript addresses an important and timely question in chromatin biology: what determines differential sensitivity of cis-regulatory elements to BAF complex activity? The authors present a systematic, multi-omic approach combining acute pharmacological inhibition with ATAC-seq, machine learning, and stimulus-response assays. The finding that primed enhancers are particularly BAF-dependent is novel and mechanistically interesting, with potential implications for understanding BAF-related diseases. However, several technical concerns and interpretive gaps need to be addressed before the conclusions are fully supported.

### Who would be interested in the results, and why
Chromatin biologists studying enhancer regulation and remodeling complexes; researchers interested in stimulus-responsive gene regulation; clinicians and scientists studying SWI/SNF-related developmental disorders and BAF-mutant cancers; computational biologists developing predictive models of chromatin dynamics.

### Major strengths
1. The use of acute pharmacological inhibition (BRM014) with short time courses (30 min) is well-designed to capture primary effects of BAF loss, minimizing secondary transcriptional confounds.
2. The integration of over 100 ChIP-seq datasets with machine learning is a powerful approach to identify predictive features, and the consistency between random forest and ridge regression results strengthens confidence.
3. The identification of primed enhancers as particularly BAF-dependent is a conceptually interesting finding that connects chromatin state to functional sensitivity.
4. The use of two orthogonal stimuli (IFN-γ and dexamethasone) with distinct signaling pathways strengthens the generalizability of the stimulus-response findings.
5. The PCHi-C analysis linking BAF-dependent cREs to genes with suppressed induction provides a mechanistic bridge between chromatin and transcriptional phenotypes.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "primed enhancers are distinctly sensitive to BAF inhibition" based on differential accessibility loss.
- **Evidence pointer** Figure 3B-E, Supplemental Figure 3A-C
- **Concern** The classification of enhancers into "primed" vs "active" relies on H3K4me1 and H3K27ac overlap, but the manuscript does not adequately address potential confounding by chromatin state stability. Primed enhancers may have lower baseline accessibility or different nucleosome density, which could independently affect sensitivity to BAF inhibition. The authors state they controlled for H3K4me1 enrichment and baseline accessibility (Figure 3E), but the details of this analysis are not fully described. Specifically, how was "controlling" performed? Was it a stratified analysis, regression adjustment, or matching? The residual confounding from unmeasured features (e.g., nucleosome positioning, DNA methylation) cannot be excluded.
- **Why it matters** If the primed enhancer sensitivity is an artifact of other correlated features, the central mechanistic claim of the paper is weakened. The distinction between primed and active enhancers is a key conceptual contribution, and the robustness of this distinction to confounding is critical.
- **Resolution test** Provide a more detailed description of the confounding control analysis, including the exact statistical method used. Consider performing a matched analysis where primed and active enhancers are matched on baseline accessibility and H3K4me1 levels, then comparing BAF sensitivity. Alternatively, use a multivariate regression model that includes continuous measures of H3K4me1, H3K27ac, and baseline accessibility as covariates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "BAF inhibition was sufficient to prevent both chromatin and transcriptional responses to interferon gamma and dexamethasone."
- **Evidence pointer** Figure 4C-F, Figure 5B-D
- **Concern** The manuscript reports that "a majority of inducible genes showed significantly reduced expression" (87/155 for IFN-γ, 183/359 for Dex), but the criteria for "reduced expression" are not clearly defined. The threshold of FDR < 0.05 and log2FC < -log2(1.5) is stated, but it is unclear whether this is relative to the stimulus-only condition or to the BAFinh-only condition. Additionally, the analysis appears to focus on genes that are induced by stimulus in the absence of BAFinh; it is not clear how many genes show partial versus complete abrogation. The claim of "prevented" responses implies near-complete blockade, but the data may show only partial suppression for many genes.
- **Why it matters** The strength of the conclusion depends on the magnitude of the effect. If many genes show only modest suppression, the claim of a "requirement" for BAF is overstated. The distinction between complete dependence and partial contribution has implications for the proposed model.
- **Resolution test** Provide a more detailed quantitative analysis, including the distribution of fold-changes for inducible genes with and without BAFinh. Report the proportion of genes showing >50%, >75%, or >90% suppression of induction. Consider presenting a scatter plot or heatmap showing the full range of responses rather than binary classification.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors conclude that "defective signal responsiveness may be a pathogenic mechanism in disease states caused by loss-of-function mutations in BAF subunits."
- **Evidence pointer** Discussion section
- **Concern** This is a speculative extrapolation from the data. The manuscript does not provide direct evidence linking impaired stimulus responses to disease phenotypes. While the speculation is reasonable, it is presented as a conclusion rather than a hypothesis. The connection between the observed phenotypes in a lymphoblastoid cell line and developmental disorders or cancers is not established.
- **Why it matters** Overstating the disease relevance could mislead readers and future research directions. The manuscript would be stronger if this were clearly framed as a hypothesis requiring direct testing.
- **Resolution test** Revise the discussion to clearly distinguish between findings supported by the data and speculative implications. Consider adding a paragraph explicitly stating the limitations of extrapolating from a single cell type to disease contexts.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "we mapped chromatin accessibility changes following acute pharmacologic BAF inhibition" and use these data to define BAF-dependent peaks.
- **Evidence pointer** Figure 1B-C, Supplemental Figure 1A-E
- **Concern** The manuscript uses a single inhibitor (BRM014) for most experiments, with ACBI1 as a confirmatory tool. However, the specificity of BRM014 is not fully addressed. While the authors cite prior work showing similar effects to genetic systems, the manuscript does not include a direct comparison of BRM014 effects with genetic depletion (e.g., SMARCA4 degradation) in the same cell line and time course. Off-target effects of BRM014 could confound the identification of BAF-dependent peaks.
- **Why it matters** The entire analysis of BAF-dependent cREs rests on the assumption that BRM014 specifically inhibits BAF. If there are off-target effects, the identified peaks and downstream conclusions could be affected.
- **Resolution test** Include a direct comparison of BRM014 and ACBI1 effects at matched time points, showing correlation of affected peaks. If feasible, include a genetic validation (e.g., SMARCA4 degron) for a subset of key conclusions, particularly the primed enhancer sensitivity and stimulus response findings.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Figure 1A
- **Evidence pointer** Figure 1A
- **Issue** The schematic in Figure 1A is described but not shown in the text. The description is brief and may not be sufficient for readers to understand the experimental design without seeing the figure.
- **Required correction** Ensure the figure legend provides a complete and self-contained description of the experimental workflow, including time points, doses, and assays.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Differential accessibility analysis"
- **Evidence pointer** Methods section
- **Issue** The normalization approach using "invariant genes" is creative but relies on the assumption that promoter accessibility at these genes reflects sequencing depth. This assumption may not hold if BAF inhibition affects promoter accessibility at a subset of invariant genes. The manuscript does not report how many genes were used for normalization or the stability of the normalization factors across conditions.
- **Required correction** Report the number of invariant genes used, the distribution of normalization factors, and a sensitivity analysis showing that results are robust to the choice of invariant gene set.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Random forest and ridge regression modelling"
- **Evidence pointer** Methods section
- **Issue** The manuscript reports AUROC values but does not report other performance metrics such as precision, recall, or F1 score. Given the class imbalance (BAF-dependent vs. independent peaks), AUROC alone may be misleading.
- **Required correction** Report additional performance metrics, particularly precision-recall curves, which are more informative for imbalanced datasets.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of AP-1 factors is somewhat dense and assumes familiarity with the AP-1 literature. A brief explanation of what AP-1 factors are and their general role in stimulus responses would improve accessibility.
- **Required correction** Add a sentence or two providing context on AP-1 factors for readers outside the immediate field.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, "Cell Culture"
- **Evidence pointer** Methods section
- **Issue** The manuscript does not specify the sex or karyotype of the GM12878 cell line, which is known to be female (XX). This is a minor omission but could be relevant for reproducibility.
- **Required correction** Add the sex and any relevant karyotypic information for the cell lines used.

### Technical failings that need to be addressed before the case is established
1. The confounding analysis for primed vs. active enhancer sensitivity (R1-M1) needs to be more rigorous and clearly described.
2. The quantitative extent of transcriptional suppression by BAIF inhibition needs to be more thoroughly characterized (R1-M2).
3. The specificity of BRM014 should be more directly validated, ideally with genetic approaches (R1-M4).

### Assessment against Nature-style criteria
- **Originality** High. The systematic identification of primed enhancers as BAF-dependent and the link to stimulus responsiveness is a novel contribution. The machine learning framework applied to predict BAF dependence is also innovative.
- **Scientific importance** Moderate to high. The findings have implications for understanding enhancer regulation and BAF-related diseases, but the direct disease relevance is speculative and not tested.
- **Interdisciplinary readership** Moderate. The topic is of interest to chromatin biologists, transcription researchers, and computational biologists, but may be less accessible to a broader biomedical audience.
- **Technical soundness** Moderate. The experimental design is generally sound, but the concerns about confounding, quantitative effect sizes, and inhibitor specificity need to be addressed.
- **Readability for nonspecialists** Moderate. The manuscript is well-written but assumes significant background knowledge in chromatin biology and genomics.

### Recommendation posture
Supportive if technical concerns are resolved. The core findings are potentially important, but the manuscript requires additional analyses to fully support the claims, particularly regarding the specificity of primed enhancer sensitivity and the quantitative extent of transcriptional suppression.

## Risk / unsupported claims
1. The claim that "defective signal responsiveness may be a pathogenic mechanism in disease states" is speculative and not directly supported by the data.
2. The statement that "BAF inhibition was sufficient to prevent" stimulus responses may overstate the effect, as the data show only a majority of genes with significant suppression, not complete blockade.
3. The generalizability of the findings to other cell types and stimuli is asserted but not tested beyond the three cell lines and two stimuli examined.
4. The claim that the machine learning framework "has the potential for broad applicability" is reasonable but not demonstrated beyond the specific context of BAF inhibition.