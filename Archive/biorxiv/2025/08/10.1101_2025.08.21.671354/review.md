## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, methods, and supplementary figure/table references
- **Assessment boundary** Scientific content, methodological rigor, data interpretation, and claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present a comprehensive deep mutational scanning dataset of all 54 human bZIP domains, measuring interactions against all 54 wild-type partners, totaling approximately 2 million quantitative measurements. They report that mutation effects are largely additive near each wild-type sequence but diverge across the family, that a global additive model performs moderately (R² = 0.47), that per-bZIP models perform better (R² = 0.88 pooled), and that a convolutional neural network can predict binding from sequence alone. They also demonstrate design of synthetic bZIPs with high target specificity.
- **Visible evidence base** Abstract, Introduction, Results (partial), Methods, figure legends referenced but figures not provided, supplementary tables referenced but not provided
- **Missing materials affecting confidence** Figures 1-5, Supplementary Figures S1-S9, Supplementary Tables S1-S8, raw data, model training details, validation metrics, synthetic bZIP experimental results

## Reviewer
- **Overall assessment** This manuscript presents a large and potentially valuable dataset for the study of protein-protein interaction landscapes. The experimental scale is impressive, and the combination of comprehensive mutagenesis with quantitative interaction measurements across an entire family is a significant technical achievement. However, the current manuscript text provides insufficient detail to fully evaluate the key claims. The results section is incomplete, figures are not available, and several methodological aspects require clarification. The central conceptual claim regarding local simplicity versus global complexity is interesting but requires more rigorous statistical support and comparison with alternative models. The practical demonstration of synthetic bZIP design is promising but needs more detailed experimental validation.
- **Who would be interested in the results, and why** Researchers in protein engineering, computational biology, and evolutionary genetics would find this dataset valuable. The comprehensive mutagenesis data across a full protein family provides a resource for understanding sequence-function relationships, training predictive models, and exploring the evolutionary constraints on protein-protein interactions. The comparison of additive models with neural network approaches addresses fundamental questions about the predictability of protein function from sequence.
- **Major strengths** 1) The scale and comprehensiveness of the dataset, covering all 54 human bZIP domains with all single amino acid substitutions at 35 positions. 2) The systematic comparison of global versus per-bZIP additive models, providing quantitative estimates of context dependency. 3) The demonstration that a CNN can predict binding from sequence, with practical application to synthetic bZIP design. 4) The identification of neofunctionalizing mutations that rewire interaction specificity.
- **Major Concerns**
- **Minor Comments**
- **Technical failings that need to be addressed before the case is established** The incomplete results section, missing figures, and insufficient methodological detail for the CNN and thermodynamic models prevent full evaluation of the central claims.
- **Assessment against Nature-style criteria** Originality: The comprehensive family-wide mutagenesis approach is novel and addresses an important gap in the field. Scientific importance: The dataset and findings have broad implications for understanding protein evolution and improving predictive models. Interdisciplinary readership: The work bridges molecular biology, computational biology, and protein engineering, with relevance to multiple disciplines. Technical soundness: The experimental approach appears sound, but the incomplete presentation prevents full assessment. Readability for nonspecialists: The manuscript is generally well-written, but the incomplete results section and missing figures hinder comprehension.
- **Recommendation posture** Supportive if technical concerns are resolved and the complete results are provided for evaluation

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim summary** The manuscript claims comprehensive coverage of all 54 human bZIP domains with approximately 2 million quantitative interaction measurements, but the results section is incomplete and figures are not provided
- **Evidence pointer** Results section, Figures 1-5, Supplementary Figures S1-S9
- **Concern** The results section as provided is truncated after the first subsection, and none of the figures or supplementary materials are available for review. This prevents evaluation of the primary data quality, the distribution of mutation effects, the model fits, and the synthetic bZIP validation results. The claims about model performance (R² values) and the identification of neofunctionalizing mutations cannot be verified without the corresponding figures and tables.
- **Why it matters** The central conclusions of the manuscript depend on the quality and interpretation of the experimental data and model fits. Without access to the figures and supplementary materials, it is impossible to assess whether the claims are supported by the evidence.
- **Resolution test** Provide the complete results section with all figures and supplementary materials for review. Include representative examples of the data quality, model fits, and validation experiments.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim summary** The manuscript claims that mutation effects are largely additive near each wild-type sequence but diverge across the family, supported by the difference between global (R² = 0.47) and per-bZIP (R² = 0.88) model performance.
- **Evidence pointer** Results section, Figure 2, Figure 4, Supplementary Figures S6-S8
- **Concern** The interpretation of the difference between global and per-bZIP model performance as evidence for context dependency requires more rigorous statistical analysis. The authors should provide confidence intervals for the R² values, demonstrate that the difference is not due to overfitting or differences in data quality, and quantify the contribution of context dependency relative to measurement noise. Additionally, the claim that "local simplicity coexists with global complexity" needs a more formal definition and statistical test.
- **Why it matters** The central conceptual claim of the manuscript rests on the interpretation of model performance differences. Without proper statistical treatment, the conclusion that the genetic architecture is locally simple but globally complex is not fully supported.
- **Resolution test** Provide confidence intervals for all R² values, perform cross-validation or bootstrap analysis, and include a formal statistical test for the difference between global and per-bZIP model performance. Quantify the variance explained by context dependency relative to measurement noise.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation
- **Claim summary** The manuscript claims that a convolutional neural network accurately predicts binding scores from sequence alone, and that this model enabled design of synthetic bZIPs with high target specificity.
- **Evidence pointer** Results section, Figure 5, Table S2, Table S3
- **Concern** The description of the CNN architecture and training is incomplete. The manuscript mentions a "preliminary version" of the CNN was used for synthetic bZIP design, but the relationship between this preliminary model and the final model is unclear. The validation of synthetic bZIPs needs more detail, including the number of designs tested, the success rate, and the comparison with natural bZIPs. The claim that the model "extrapolates to novel regions of sequence space" requires demonstration that the designed sequences are truly novel and not close to natural sequences.
- **Why it matters** The practical application of the model to synthetic bZIP design is a key claim of the manuscript. Without detailed validation, the utility of the approach for bioengineering purposes is not established.
- **Resolution test** Provide complete details of the CNN architecture, training procedure, and hyperparameter selection. Include the number of synthetic bZIPs tested, the experimental validation results, and a comparison with natural bZIP sequences to demonstrate novelty.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Data quality assessment
- **Claim summary** The manuscript reports that 82,485 out of 1,601,098 variants showed significant effects (5.2%), with predominantly negative effects, and that most positive-effect mutations enable new interactions.
- **Evidence pointer** Results section, Figure 1, Figure 3, Supplementary Figures S3-S4
- **Concern** The criteria for calling significant effects (absolute mutation effect > 2, FDR = 5%) need justification. The manuscript should provide information on the dynamic range of the assay, the reproducibility of measurements, and the relationship between the chosen threshold and the noise level of the assay. The claim that "the majority of bZIP pairs are on the edge of binding" is interesting but needs more quantitative support, including the distribution of wild-type binding scores and the statistical significance of the enrichment of positive-effect mutations enabling new interactions.
- **Why it matters** The biological conclusions about the evolvability of the bZIP family depend on the reliability of the mutation effect measurements and the appropriateness of the significance thresholds.
- **Resolution test** Provide a detailed characterization of the assay noise, including replicate correlations, the distribution of mutation effects for synonymous or neutral mutations, and a justification for the chosen significance thresholds. Include a statistical test for the enrichment of neofunctionalizing mutations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "generative biology holds the promise to transform our ability to design and understand living systems" but the connection between this framing and the specific findings of the manuscript is not immediately clear. The abstract could more directly state the key findings and their implications.
- **Required correction** Revise the abstract to more directly connect the framing of generative biology to the specific findings about the genetic architecture of bZIP interactions and the implications for predictive modeling.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results section
- **Evidence pointer** Results, first subsection
- **Issue** The term "bindingPCA" is used without a clear definition of what the acronym stands for. While the method is described in the methods section, a brief definition in the results would improve readability.
- **Required correction** Define the acronym at first use, e.g., "bindingPCA (binding-based protein-fragment complementation assay)".

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and materials availability
- **Evidence pointer** Data and materials availability section
- **Issue** The accession code for the GEO deposit is listed as "XXX" and the Zenodo DOI is provided, but the GitHub links are present. The manuscript should provide the actual GEO accession code.
- **Required correction** Provide the actual GEO accession code for the raw sequencing data.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Typographical errors
- **Affected element** Methods and Data availability
- **Evidence pointer** Methods, Data and materials availability
- **Issue** Several typographical errors are present, including "avilable" (should be "available") in the Data and materials availability section, and "Fundation" (should be "Foundation") in the Funding section.
- **Required correction** Correct the typographical errors throughout the manuscript.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Methods, deep learning model training
- **Evidence pointer** Methods, deep learning model training
- **Issue** The description of the ESM fine-tuning mentions "a single fold" was used for training, but it is unclear how this compares to the CNN training which used 10-fold cross-validation. This discrepancy should be clarified.
- **Required correction** Clarify the training and evaluation procedure for the ESM model and explain why a single fold was used.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The manuscript references Figure 1C showing the bPCA assay schematic, but the figure is not available for review. The schematic should clearly illustrate the assay workflow.
- **Required correction** Ensure Figure 1C clearly illustrates the bPCA assay workflow, including the barcoding strategy and the competition step.

## Risk / unsupported claims
- The claim that "the genetic architecture of protein function is more complex than previously anticipated" is not directly supported by the data presented, as the comparison with previous studies is not quantified.
- The claim that the CNN "extrapolates to novel regions of sequence space" is not fully supported without demonstration that the designed sequences are substantially different from natural bZIPs.
- The claim that "capturing family-wide diversity is essential" for training accurate models is not directly tested, as the authors do not compare model performance with and without family-wide data.
- The statement that "the majority of bZIP pairs are on the edge of binding" is an interpretation that requires more quantitative support regarding the distribution of binding scores and the definition of "edge of binding."
- The claim that the dataset "captures both conserved and divergent context-dependencies" is not fully supported without a formal analysis of which mutations show context-dependent effects and how these relate to sequence or structural features.