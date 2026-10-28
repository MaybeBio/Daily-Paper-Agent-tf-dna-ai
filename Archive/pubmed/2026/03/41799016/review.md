## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, supplementary data references)
- **Assessment boundary** Technical soundness, methodological rigor, validity of claims relative to presented evidence, and suitability for the stated scope of the journal
- **Shared manuscript claim summary** The authors present a systematic comparison of deep learning architectures and data augmentation strategies for modeling TF–DNA binding affinities from SELEX-seq data, with a focus on low-affinity binding sites. They report that reverse-complement weight-sharing CNNs and SA models trained with RC-augmented data outperform other approaches, that ISM is more robust to hyperparameter variation than other interpretation methods, and that their models recover known low-affinity Exd-Ubx binding in the svb enhancer.
- **Visible evidence base** Main text figures (Figs 1–5), supplementary figures and tables referenced (S1–S14), GitHub repository and figshare data availability statement
- **Missing materials affecting confidence** Supplementary figures and tables not provided in the submitted material; figure images not available; exact hyperparameter values for final models not fully specified in text; statistical significance testing details for model comparisons not fully described

## Reviewer

- **Overall assessment** This manuscript addresses a relevant and timely question in computational regulatory genomics: how to systematically handle DNA strand orientation and choose interpretation methods for deep learning models of TF–DNA binding, particularly for low-affinity sites. The study design is sensible, and the comparison across architectures, augmentation strategies, and interpretation methods is useful for the community. However, the manuscript as presented has several technical gaps that prevent full evaluation of the claims. The absence of the supplementary material, which contains key performance tables and additional analyses, makes several central claims difficult to verify. The mechanistic interpretation regarding YR stacking, while interesting, is presented with limited statistical or experimental support. The work is likely of interest to computational biologists working on TF binding specificity, but the current evidence base is insufficient to fully establish the central claims.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing or applying deep learning models to regulatory genomics problems would be the primary audience. Researchers studying TF binding specificity, particularly those working with SELEX-seq or similar in vitro binding data, would benefit from the systematic comparison of strand-handling strategies and interpretation methods. The case study on Exd-Hox heterodimers and the svb enhancer would also be of interest to Drosophila developmental biologists studying Hox target specificity. The practical recommendations regarding ISM robustness and RC-augmentation strategies could inform model design choices in future studies.

- **Major strengths**
  1. The systematic comparison of three strand-handling strategies (Raw, Double, RC-augmented) across two architecture families (CNN, SA) is a useful contribution, as this design choice is often made ad hoc in the field.
  2. The evaluation of interpretation method robustness to hyperparameter variation is a practical and underappreciated issue; the finding that ISM is more stable than gradient-based methods is actionable.
  3. The use of a well-characterized biological system (Exd-Hox heterodimers, svb enhancer) grounds the computational analysis in a concrete biological context.
  4. The authors are appropriately cautious in the Discussion about limitations, including the narrow TF family coverage and sequence length constraints.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that CNN-RC and SA-double models outperform other approaches, and that ISM is the most robust interpretation method, with quantitative support from supplementary tables and figures.
- **Evidence pointer** Supplementary Tables S1–S7, Supplementary Figures S1–S14
- **Concern** The central quantitative results supporting the main claims are contained entirely in supplementary materials that were not provided for review. Without access to the performance tables (e.g., R² values for all models across all TFs), the hyperparameter search results, and the robustness quantification for interpretation methods, the claims of superiority for specific architectures and methods cannot be independently assessed.
- **Why it matters** The main contribution of this work is comparative: the authors claim certain strategies are better than others. Without the underlying data, these comparisons are unverifiable, and the reader cannot judge whether observed differences are meaningful or within noise.
- **Resolution test** Provide the supplementary materials in full, including all performance metrics, hyperparameter search results, and statistical significance tests for the reported differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript states that CNN and SA models "significantly outperformed" the MLR model, and that certain augmentation strategies led to "statistically significant" improvements.
- **Evidence pointer** Figure 2C, Figure 3A, Supplementary Table S5
- **Concern** The statistical testing methodology is not described. It is unclear what test was used, how many replicates or seeds were used for model training, whether the same train/test splits were used across models, and whether multiple testing corrections were applied when comparing across eight TFs and multiple model variants. The phrase "statistically significant" appears without supporting methodology.
- **Why it matters** Deep learning model performance can vary substantially with random initialization and data splitting. Without a clear description of the statistical framework, the reader cannot determine whether the reported differences are robust or artifacts of a single run.
- **Resolution test** Describe the statistical testing procedure in detail, including the number of independent training runs, the specific test used, how variance across runs was handled, and whether corrections for multiple comparisons were applied.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Claim support
- **Claim pointer** The authors state: "we suggest that YR stacking might be a driving force for Exd-Ubx to bind to DNA, whereas the functional groups of DNA nucleotides fine-tune high-affinity TFBSs and differentiate them from low-affinity TFBSs."
- **Evidence pointer** Figure 5D, Results section "Recovery of functional Exd-Ubx binding at low-affinity binding sites"
- **Concern** The YR stacking hypothesis is presented as a possible mechanistic explanation, but the evidence provided is limited to a visual comparison of YR-encoded logos between high- and low-affinity sequences. No quantitative measure of YR step enrichment, no comparison to a null model, and no direct test of the stacking hypothesis (e.g., through structural analysis or mutagenesis) is provided. The claim that YR stacking is a "driving force" goes beyond what the data can support.
- **Why it matters** The mechanistic interpretation is a potentially interesting contribution, but as presented it is speculative. Overstating the support for this hypothesis could mislead readers into treating it as established.
- **Resolution test** Either soften the language to clearly frame this as a hypothesis requiring further testing, or provide quantitative evidence (e.g., statistical enrichment of YR steps in low-affinity sites, comparison to shuffled controls, or structural modeling support).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical completeness
- **Claim pointer** The manuscript describes the CNN-RC architecture as a "reverse-complement weight-sharing" model and states it showed the best consistency and performance.
- **Evidence pointer** Materials and methods section "Model architecture and training process of CNN model", Supplementary Figure S1
- **Concern** The description of the CNN-RC architecture is brief and relies on a reference to a previous publication. The specific implementation details relevant to this work, such as how the weight-sharing constraint is enforced, how the constrained scanner handles the reverse-complement input, and how the weighted sum layer is trained, are not fully described. This limits reproducibility.
- **Why it matters** Reproducibility is a core requirement for computational work. If the architecture is not described in sufficient detail, other researchers cannot implement or build upon it.
- **Resolution test** Provide a complete architectural description, including layer dimensions, weight-sharing constraints, and any modifications relative to the original implementation, or make the code fully available and referenced in the text.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, last sentence
- **Issue** The abstract states the findings "will be relevant for" future applications, which is vague. The specific nature of the relevance, or the most immediate implication, is not stated.
- **Required correction** Consider specifying the most direct implication, e.g., that the recommended model and interpretation pipeline can be applied to other SELEX-seq datasets or to predict low-affinity binding in other TF families.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Hyperparameter specification
- **Evidence pointer** Materials and methods, "Model architecture and training process of CNN model" and "Model architecture and training process of SA models"
- **Issue** The final hyperparameter values for the models used in the main results are not stated in the text. The authors mention hyperparameter search but do not report the selected values.
- **Required correction** Report the final hyperparameter values for all model types in the main text or in a table.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Figure 5C
- **Evidence pointer** Figure 5C, Results section
- **Issue** The text states that increased relative binding affinity of Exd-Scr was observed on mutated sequences, but the magnitude of this increase and its biological relevance are not discussed. It is unclear whether the predicted increase is large enough to be functionally meaningful.
- **Required correction** Provide quantitative values for the predicted affinity changes and discuss whether these are consistent with the phenotypic observations from the original study.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scope
- **Affected element** Discussion, limitations
- **Evidence pointer** Discussion section
- **Issue** The authors acknowledge the limitation of testing on a single TF family, but do not discuss how their findings might generalize to other TF families with different DNA-binding domains or to datasets generated by different experimental protocols.
- **Required correction** Add a brief discussion of expected generalizability and any known differences in binding mechanisms that might affect the transferability of the recommended pipeline.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1A–C
- **Issue** The figure is described in the text but the figure itself was not available for review. The description of the three augmentation strategies in the text is clear, but the relationship between panels A, B, and C could be clarified.
- **Required correction** Ensure the figure legend clearly explains the relationship between the augmentation strategies, the model architectures, and the interpretation methods.

## Risk / unsupported claims
- The claim that CNN-RC and SA-double models outperform other approaches is not verifiable without the supplementary performance tables.
- The claim that ISM is the most robust interpretation method is not fully verifiable without the quantitative robustness analysis in the supplementary materials.
- The mechanistic claim regarding YR stacking as a "driving force" for low-affinity binding is speculative and not quantitatively supported.
- The claim that the models "recover" in vivo phenotypic evidence is based on qualitative agreement with prior observations and lacks quantitative comparison to the original experimental data.
- The statement that the findings "will be relevant for" TF–DNA binding specificity guided protein design is an assertion without demonstrated evidence in this manuscript.