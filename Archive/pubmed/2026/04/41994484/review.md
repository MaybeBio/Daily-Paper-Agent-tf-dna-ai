## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors state that integrating molecular and epigenomic annotations with a deep learning framework predicts cell type–specific regulatory effects of PCOS-risk variants, identifies enhancer-disrupting activity in approximately 20% of risk variants, links disrupted androgen-mediated transcription factor binding to hyperandrogenemia, and demonstrates that model-prioritized variants are more pleiotropic and exert stronger regulatory effects, with the IRX3-FTO locus serving as a case study for cross-tissue mechanisms.
- **Visible evidence base** Abstract text only; no quantitative results, model architecture details, validation statistics, or experimental data are available
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, supplementary data, model training and validation details, reporter assay descriptions, variant annotation pipelines, and statistical analyses

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially valuable computational framework for interpreting PCOS risk variants, with a clear focus on regulatory mechanisms and cell type specificity. However, the current evidence base is insufficient to evaluate the technical soundness of the deep learning model, the robustness of the variant effect predictions, or the strength of the biological conclusions. The claims are broad and mechanistically ambitious, but the abstract alone does not provide the necessary detail to assess whether they are supported. The case study of IRX3-FTO is intriguing but presented without specific data. The work could be of interest to the PCOS genetics and functional genomics communities, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in reproductive endocrinology, particularly those studying PCOS genetics and androgen signaling, would be interested in the potential link between regulatory variants and hyperandrogenemia. The functional genomics and deep learning community would also find value in the application of DL to cell type–specific regulatory variant prioritization. Clinicians with an interest in the molecular basis of PCOS heterogeneity may find the cross-tissue mechanisms relevant, though the translational implications are not yet clear.
- **Major strengths** The abstract addresses a significant gap in PCOS research by moving beyond variant association to mechanistic interpretation. The integration of epigenomic annotations with a deep learning framework is a modern and appropriate approach. The focus on cell type–specific effects and transcription factor disruption is biologically meaningful. The use of a concrete locus, IRX3-FTO, to illustrate cross-tissue regulatory effects is a strength that grounds the computational findings in a specific example.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** The abstract does not provide any quantitative validation metrics for the deep learning model, such as area under the curve, precision, recall, or comparison to baseline methods. The claim of strong concordance with reporter assay data is unverifiable without specific correlation coefficients or effect sizes. The proportion of risk variants with enhancer-disrupting activity is stated as approximately 20%, but no confidence intervals or statistical significance are given. The prioritization of variants as more pleiotropic and having stronger regulatory effects lacks any supporting statistics. The IRX3-FTO case study is described qualitatively without data on specific variants, affected transcription factors, or functional outcomes.
- **Assessment against Nature-style criteria**  
  - Originality: The approach of applying deep learning to PCOS risk variant interpretation is not entirely novel, as similar frameworks exist for other traits, but the specific application to PCOS and the focus on androgen-mediated signaling may offer a new angle. The originality is moderate but cannot be fully assessed without the full manuscript.  
  - Scientific importance: The potential to link regulatory variants to hyperandrogenemia and cross-tissue mechanisms in PCOS is scientifically important, given the high prevalence and complex etiology of the condition. However, the importance is contingent on the robustness of the predictions, which is not yet demonstrated.  
  - Interdisciplinary readership: The work bridges genomics, computational biology, and reproductive endocrinology, which could attract a broad readership. The abstract is written in a way that is accessible to nonspecialists, though some terms such as "pleiotropic" and "epigenomic annotations" may require background knowledge.  
  - Technical soundness: Not assessable from the abstract. The deep learning framework, validation approach, and statistical methods are not described in sufficient detail.  
  - Readability for nonspecialists: The abstract is generally clear and logically structured, but the density of transcription factor names and cell types may be challenging for readers outside the field. The key message, that regulatory variants disrupt androgen signaling, is communicated effectively.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising framework and plausible biological insights, but the lack of methodological detail and quantitative support means the core claims cannot be evaluated. A supportive posture would require access to the full manuscript with model validation, statistical analyses, and detailed case study results.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The deep learning model showed strong concordance with reporter assay data and identified enhancer-disrupting activity in approximately 20% of risk variants.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract claims strong concordance with reporter assay data but provides no quantitative metrics, such as correlation coefficients, sensitivity, specificity, or the number of variants tested. The 20% proportion of enhancer-disrupting variants is presented without confidence intervals or a description of how this was derived.  
- **Why it matters** Without validation metrics, the reliability of the model predictions is unknown. The 20% figure is a central quantitative claim that could be an artifact of the model threshold or the variant selection process. If the model is not well calibrated, the downstream biological interpretations, including the androgen signaling link, would be compromised.  
- **Resolution test** Provide the full validation results, including the number of reporter assay comparisons, the correlation or agreement statistics, and the criteria for defining enhancer-disrupting activity. Report confidence intervals for the 20% estimate and describe the variant selection and thresholding procedures.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence strength  
- **Claim pointer** Many of these variants disrupt transcription factors involved in androgen-mediated signaling, providing molecular insights into hyperandrogenemia in PCOS.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract states that many variants disrupt transcription factors involved in androgen-mediated signaling, but no specific transcription factors, variants, or cell types are named in this context. The link to hyperandrogenemia is asserted rather than demonstrated with data.  
- **Why it matters** The connection between regulatory variant effects and hyperandrogenemia is a key biological conclusion. Without specific examples or statistical enrichment analysis, the claim is speculative. The abstract does not show whether the enrichment of androgen-related transcription factor disruption is significant relative to background or other pathways.  
- **Resolution test** Provide a list of the specific transcription factors and variants involved, along with an enrichment analysis against a null model or other pathway sets. Include data on the cell types where these effects are predicted and, if possible, functional validation of at least one variant affecting androgen signaling.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence strength  
- **Claim pointer** Variants prioritized by the model were more pleiotropic and exerted stronger regulatory effects on gene expression compared with other risk variants.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The claim that prioritized variants are more pleiotropic and have stronger regulatory effects is presented without any quantitative comparison. No effect sizes, p-values, or definitions of "pleiotropic" and "stronger" are given.  
- **Why it matters** This claim is central to the utility of the model as a prioritization tool. If the model does not actually enrich for variants with greater functional impact, its practical value is diminished. The lack of statistics makes it impossible to judge whether the difference is meaningful or due to chance.  
- **Resolution test** Provide a statistical comparison between prioritized and non-prioritized variants, including effect size distributions, significance tests, and a clear definition of pleiotropy (e.g., number of tissues or cell types affected). Show that the difference is robust to confounders such as linkage disequilibrium or variant frequency.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** Using the IRX3-FTO locus as a case study, we demonstrate how regulatory disruptions in tissues such as the fetal brain, pancreas, adipocytes, and endothelial cells may link obesity-associated mechanisms to PCOS pathogenesis.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The case study is described only in qualitative terms. No specific variants, predicted regulatory effects, or functional data are provided. The link between the IRX3-FTO locus and PCOS pathogenesis is asserted without evidence.  
- **Why it matters** The case study is intended to illustrate the broader utility of the framework. Without concrete details, it serves as an anecdote rather than a demonstration. The claim of linking obesity and PCOS mechanisms is significant and requires specific data to be credible.  
- **Resolution test** Provide detailed results for the IRX3-FTO locus, including the specific risk variants, the predicted transcription factor disruptions, the cell types involved, and any experimental validation. Show how these findings connect to known obesity and PCOS pathways with supporting data.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract, first sentence  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The phrase "limited understanding of how susceptibility loci drive molecular mechanisms across diverse phenotypes" is vague. It is not clear what "diverse phenotypes" refers to in the context of PCOS.  
- **Required correction** Specify the phenotypes, such as hyperandrogenemia, anovulation, or metabolic dysfunction, to clarify the scope of the problem.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Deep learning framework description  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract does not name the deep learning architecture or the training data. This limits the reader's ability to assess the approach or reproduce it.  
- **Required correction** Include the model type (e.g., convolutional neural network, transformer) and a brief description of the training data and features in the abstract or refer to a methods section.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Precision  
- **Affected element** Transcription factor list  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract lists NR4A1/2, NHLH2, FOXA1, and WT1 as key transcription factors but does not specify which cell types or variants are associated with each.  
- **Required correction** Provide a brief mapping of transcription factors to cell types or variants, or indicate that this detail is in the full manuscript.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** "Enhancer-disrupting activity"  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The term "enhancer-disrupting activity" is used without a definition. It is unclear whether this refers to reduced enhancer activity, altered transcription factor binding, or a change in chromatin state.  
- **Required correction** Define the term operationally, such as a predicted decrease in enhancer activity based on the model output, and state the criteria used.

## Risk / unsupported claims
- The claim of strong concordance with reporter assay data is unsupported because no validation statistics are provided.
- The claim that approximately 20% of risk variants have enhancer-disrupting activity is unsupported without confidence intervals or a description of the calculation.
- The claim that many variants disrupt androgen-mediated transcription factors is unsupported without specific examples or enrichment analysis.
- The claim that prioritized variants are more pleiotropic and have stronger regulatory effects is unsupported without quantitative comparisons.
- The IRX3-FTO case study is described qualitatively and does not provide evidence for the claimed cross-tissue mechanisms.
- The overall conclusion that the framework refines mechanistic understanding of PCOS is not evaluable from the abstract alone.