## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors present the EN-TEx resource, comprising 1,635 open-access datasets from four donors across ~30 tissues and ~15 assays, mapped to matched diploid genomes with long-read phasing and structural variants. They construct a catalog of >1 million allele-specific loci, show coordinated allele-specific activity across assays, and develop three applications: decorating ENCODE cCREs with tissue and allele-specific information, a transferQTL model to predict eQTL activity in hard-to-obtain tissues, and a transformer model predicting allele-specific effects from local sequence context.
- **Visible evidence base** Main text figures (Figures 1–7), supplementary figures (S1–S7), supplementary data files (Data S1–S37), and STAR Methods sections
- **Missing materials affecting confidence** No raw data files, no code repository contents, no full figure panels, no supplementary tables with detailed statistics, no external validation dataset details beyond those mentioned

## Reviewer
- **Overall assessment** This manuscript describes a substantial community resource with broad potential utility. The scale of data generation and uniform processing is commendable, and the allele-specific catalog represents a significant advance over previous efforts. The three applications are well-motivated and generally well-executed, with the transferQTL model and transformer model offering practical tools. However, several technical concerns need to be addressed, particularly regarding the statistical rigor of allele-specific calling, the interpretation of the transformer model's attention mechanism, and the generalizability claims of the transferQTL model. The manuscript is dense and at times difficult to follow, which may limit accessibility for nonspecialists.
- **Who would be interested in the results, and why** Researchers in functional genomics, regulatory genomics, and statistical genetics would find this resource valuable. Those working on variant interpretation, eQTL mapping, and personal genome analysis would benefit from the allele-specific catalog and the transferQTL model. The transformer model for predicting allele-specific effects from sequence context would interest computational biologists developing deep learning approaches for genomics. The resource's integration with GTEx and ENCODE annotations makes it relevant to a broad community studying gene regulation and disease-associated variants.
- **Major strengths** 1) The scale and uniformity of data generation across four individuals and ~30 tissues is a major achievement, enabling consistent cross-tissue comparisons. 2) The construction of a diploid personal genome for each individual, with long-read phasing and structural variant identification, is technically rigorous and addresses a key limitation of reference-genome-based analyses. 3) The allele-specific catalog, with >1 million loci, is an order of magnitude larger than previous collections, providing a valuable resource for the community. 4) The three applications are well-chosen and demonstrate the utility of the resource beyond descriptive annotation. 5) The transferQTL model's ability to predict eQTL activity in hard-to-obtain tissues using chromatin features is practically useful and well-validated. 6) The transformer model's performance in predicting allele-specific effects from sequence alone is surprising and potentially important, though it requires careful interpretation.
- **Major Concerns** 1) The statistical framework for allele-specific calling needs more detail. The manuscript mentions a standardized pipeline but does not fully describe the model, the handling of technical biases, or the false discovery rate control. 2) The claim that the transformer model can predict allele-specific activity from local sequence context alone is striking, but the interpretation is unclear. The attention analysis is descriptive, and the causal relationship between sequence features and allele-specific effects is not established. 3) The transferQTL model's validation against external eQTL catalogs is mentioned but not fully described. The manuscript states >75% identification of eQTLs in pancreas, skeletal muscle, and skin, but the details of this validation, including the number of eQTLs tested and the statistical significance, are not provided. 4) The manuscript claims that the EN-TEx catalog covers 76% of common AS SNVs in the European population, but this estimate relies on assumptions about the distribution of AS events that are not fully justified. 5) The decorrelation of allele-specific activity with conservation is interesting but the analysis appears to be purely correlational. The manuscript does not address potential confounding factors such as local sequence context or mutation rate variation.
- **Minor Comments** 1) The manuscript is very long and dense, with many technical details in the main text that could be moved to supplementary materials. 2) The figures are referenced frequently, but the main text does not always clearly explain what is shown in each panel. 3) The description of the "stringent" annotation set is brief, and the rationale for using the top 1% of H3K27ac signals is not fully explained. 4) The discussion of the buffering hypothesis is interesting but somewhat speculative. The authors should clarify what additional evidence would be needed to support this hypothesis more strongly. 5) The manuscript mentions that the EN-TEx portal provides access to data and tools, but the specific URLs and access procedures are not described in the main text. 6) The authors should consider providing a more accessible summary of the resource for nonspecialist readers, perhaps in the form of a graphical abstract or a plain-language summary.
- **Technical failings that need to be addressed before the case is established** 1) The allele-specific calling pipeline needs a more detailed statistical description, including the model, the handling of overdispersion, and the control of false discoveries. 2) The transformer model's performance should be compared against simpler sequence-based models to establish that the transformer architecture is necessary. 3) The transferQTL model's validation should include a clear description of the external datasets, the matching of tissues, and the statistical significance of the predictions. 4) The claim of 76% coverage of common AS SNVs in Europeans needs a more rigorous justification, including a discussion of the assumptions and potential biases.
- **Assessment against Nature-style criteria** Originality: The EN-TEx resource is original in its integration of diploid personal genomes with multi-tissue functional genomics data, and the allele-specific catalog is a significant new contribution. The transferQTL and transformer models are novel applications of existing methods to a new problem. Scientific importance: The resource has high potential importance for the field of functional genomics and variant interpretation, providing a foundation for many future studies. The allele-specific catalog and the models built on it could have broad impact. Interdisciplinary readership: The work is primarily of interest to genomics and computational biology researchers, but the resource could also be valuable to geneticists and clinicians working on variant interpretation. The manuscript is likely to be accessible to specialists but may be challenging for nonspecialists. Technical soundness: The data generation and processing appear technically sound, but the statistical details of several analyses need to be clarified. The transformer model's interpretation is a concern. Readability for nonspecialists: The manuscript is dense and technical, with a steep learning curve for readers not familiar with the field. The authors should consider providing more context and explanation for key concepts.
- **Recommendation posture** Supportive if technical concerns are resolved. The resource is valuable and the applications are promising, but the statistical rigor of the allele-specific calling, the interpretation of the transformer model, and the validation of the transferQTL model need to be strengthened. Once these concerns are addressed, the manuscript would be suitable for publication.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims the detection of >1 million allele-specific loci using a standardized pipeline, but the statistical framework is not fully described.
- **Evidence pointer** STAR Methods "AS Calling" section; Results section "Construction of the AS Catalog"
- **Concern** The allele-specific calling pipeline is described as "standardized" but the underlying statistical model is not detailed. The manuscript does not specify the distributional assumptions, the handling of overdispersion in count data, the method for combining information across replicates, or the procedure for controlling the false discovery rate. Without this information, it is difficult to assess the reliability of the allele-specific calls.
- **Why it matters** The allele-specific catalog is a central contribution of the resource. If the calling pipeline is not statistically rigorous, the catalog may contain a substantial number of false positives, which would undermine the validity of downstream analyses and applications.
- **Resolution test** Provide a complete description of the statistical model, including the likelihood, the prior (if Bayesian), the method for estimating the false discovery rate, and the sensitivity analyses demonstrating the robustness of the calls to model assumptions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that a transformer model can predict allele-specific activity from local sequence context alone, with AUROC values of 0.69 for CTCF and 0.80 for H3K27ac.
- **Evidence pointer** Results section "Application 3"; STAR Methods "Transformer Model" section; Figure 7
- **Concern** The transformer model's performance is presented as "surprisingly good," but the manuscript does not provide a comparison against simpler sequence-based models, such as k-mer-based logistic regression or convolutional neural networks. Without such a comparison, it is unclear whether the transformer architecture is necessary or whether the performance is driven by simple sequence features. Additionally, the interpretation of the attention mechanism is descriptive, and the causal relationship between the attended sequence positions and allele-specific effects is not established.
- **Why it matters** The claim that local sequence context is sufficient to predict allele-specific effects is strong and has implications for understanding the mechanisms of variant impact. If the model's performance is not compared against simpler baselines, the claim is not fully supported. The attention analysis, while interesting, does not provide mechanistic insight without additional validation.
- **Resolution test** Compare the transformer model against simpler baselines, such as k-mer frequency models or convolutional neural networks, using the same training and test data. Provide a more rigorous analysis of the attention mechanism, such as perturbation experiments or comparison to known motif positions, to support the claim that the model is learning meaningful sequence features.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that the transferQTL model achieves 0.86 balanced accuracy in predicting eQTL activity in target tissues and correctly identifies >75% of eQTLs in external catalogs for pancreas, skeletal muscle, and skin.
- **Evidence pointer** Results section "Application 2"; STAR Methods "transferQTL Model" section; Figure 5
- **Concern** The validation of the transferQTL model against external eQTL catalogs is mentioned but not fully described. The manuscript does not specify the number of eQTLs tested, the criteria for matching tissues between datasets, the handling of overlapping samples, or the statistical significance of the predictions. Additionally, the model's performance is reported as balanced accuracy, but the manuscript does not provide confidence intervals or a comparison against a null model.
- **Why it matters** The transferQTL model is a key application of the resource, with potential practical utility for extending eQTL annotations to tissues that are difficult to profile. Without a rigorous validation, the model's generalizability is not established.
- **Resolution test** Provide a detailed description of the external validation, including the number of eQTLs tested, the tissue matching criteria, the statistical significance of the predictions, and a comparison against a null model or a simpler baseline.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The manuscript claims that the EN-TEx catalog covers 76% of common AS SNVs in the European population.
- **Evidence pointer** Results section "Construction of the AS Catalog"; STAR Methods "AS Catalog" section
- **Concern** The estimate of 76% coverage is based on an extrapolation from the four EN-TEx individuals to the European population. The manuscript does not fully justify the assumptions underlying this extrapolation, such as the representativeness of the four individuals and the distribution of allele frequencies at AS loci.
- **Why it matters** The coverage estimate is used to argue for the comprehensiveness of the catalog. If the estimate is not well-justified, the claim of comprehensiveness is weakened.
- **Resolution test** Provide a more detailed justification of the coverage estimate, including a discussion of the assumptions and potential biases, or soften the claim to reflect the uncertainty.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Main text
- **Evidence pointer** Throughout
- **Issue** The manuscript is very dense and technical, with many details that could be moved to supplementary materials. The main text would benefit from a clearer structure and more accessible explanations of key concepts.
- **Required correction** Consider moving some technical details to the STAR Methods or supplementary materials, and provide more context and explanation for nonspecialist readers.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Figure 7
- **Evidence pointer** Figure 7
- **Issue** The attention analysis in Figure 7 is descriptive, and the manuscript does not provide a quantitative assessment of the attention patterns.
- **Required correction** Provide a quantitative analysis of the attention patterns, such as a comparison to known motif positions or a statistical test for enrichment of attention at functional sites.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** STAR Methods "AS Calling" section
- **Evidence pointer** STAR Methods "AS Calling" section
- **Issue** The description of the allele-specific calling pipeline is brief, and the manuscript does not specify the software tools or parameters used.
- **Required correction** Provide a more detailed description of the pipeline, including the software tools, parameters, and any quality control steps.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of the buffering hypothesis is interesting but speculative. The manuscript does not provide a clear test of the hypothesis.
- **Required correction** Clarify what additional evidence would be needed to support the buffering hypothesis, or present the discussion as a hypothesis-generating observation.

## Risk / unsupported claims
- The claim that the transformer model's attention mechanism "re-discovers" key motifs is not quantitatively supported.
- The claim of 76% coverage of common AS SNVs in the European population relies on assumptions that are not fully justified.
- The claim that the transferQTL model can identify "likely" eQTLs that are not in the GTFC catalog is not validated against an independent dataset.
- The claim that the EN-TEx resource enables "more accurate" quantification of differential expression and regulatory activity compared to reference-genome-based approaches is not directly tested with a quantitative comparison.