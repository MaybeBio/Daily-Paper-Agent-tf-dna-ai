## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, data availability, and code availability sections.
- **Assessment boundary** Scientific validity, technical soundness, novelty, and significance of the claims presented. The review is based solely on the provided manuscript text; no external data, figures, or supplementary materials were examined.
- **Shared manuscript claim summary** The authors present DNA-Diffusion, a conditional diffusion model that generates 200-bp synthetic regulatory elements with cell-type-specific activity. They claim the model recapitulates endogenous transcription factor binding grammar, produces sequences with enhanced cell-type specificity, and demonstrates functional activity in both episomal (STARR-seq) and endogenous (EXTRA-seq) contexts. They further claim superior performance over existing methods in balancing activity, specificity, and sequence diversity.
- **Visible evidence base** The manuscript text includes descriptions of in silico analyses (sequence similarity, motif composition, ChromBPNet, Enformer), STARR-seq experiments (5,850 elements, three cell lines), EXTRA-seq experiments (AXIN2 locus, MEC-1 cells), and benchmarking against other generative methods. Specific quantitative results are referenced but not fully detailed in the text provided.
- **Missing materials affecting confidence** Figures, supplementary figures, supplementary tables, and supplementary notes are referenced but not provided. Detailed experimental protocols, full statistical analyses, and raw data are not available for independent verification. The benchmarking methodology and specific performance metrics are only partially described.

## Reviewer
- **Overall assessment** The manuscript presents a potentially valuable contribution to the field of synthetic regulatory element design. The use of a diffusion model conditioned on cell type is a reasonable and timely approach, and the combination of in silico predictions with both episomal and endogenous experimental validation is commendable. However, the current text does not provide sufficient detail to fully assess the technical soundness of the model, the robustness of the experimental validations, or the strength of the benchmarking claims. Several key claims, particularly regarding "enhanced cell-type specificity" and "superior performance," require more rigorous quantitative support and clearer presentation of the underlying data.
- **Who would be interested in the results, and why** Researchers in synthetic biology, gene therapy, and regulatory genomics would be interested. The ability to design compact, cell-type-specific regulatory elements has direct applications in therapeutic gene expression control, particularly for viral delivery systems with limited cargo capacity. The work also contributes to the growing field of generative AI for biological sequence design.
- **Major strengths**
    1.  The use of a conditional diffusion model is a modern and appropriate methodological choice for generating regulatory sequences.
    2.  The validation strategy is multi-faceted, combining computational predictions with both high-throughput (STARR-seq) and targeted endogenous (EXTRA-seq) experimental assays.
    3.  The demonstration of endogenous gene reactivation (AXIN2) in a disease-relevant context is a significant step beyond typical episomal reporter assays.
    4.  The exploration of the trade-off between signal intensity and specificity via the classifier-free guidance parameter is an interesting and potentially useful feature.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness
    - **Claim pointer** The claim that DNA-Diffusion generates sequences with "enhanced cell-type specificity" compared to endogenous elements.
    - **Evidence pointer** Results sections "DNA-Diffusion-generated sequences demonstrate cell-type-specificity, accessibility, and cell-type-specific activation of cis genes in silico" and "Using STARR-seq to evaluate the regulatory activity of DNA-Diffusion sequences"; Figures 3, 4, 5 (not provided).
    - **Concern** The manuscript states that DNA-Diffusion sequences show "enhanced cell-type specificity" and that top-ranked sequences "outperformed the strongest validated genomic sequences experimentally." However, the specific metrics used to define and quantify "specificity" and "outperform" are not clearly defined in the text. The comparison to endogenous elements is described qualitatively. The statistical significance and effect sizes of these improvements are not reported in the provided text.
    - **Why it matters** The central claim of the paper is that the generated sequences are not only functional but superior to natural sequences in terms of specificity and activity. Without a clear, quantitative definition of these metrics and a rigorous statistical comparison, this claim is not established. The reader cannot assess the magnitude of the improvement or its practical significance.
    - **Resolution test** The authors must provide a clear operational definition of "cell-type specificity" (e.g., a specificity index based on the ratio of activity in the target cell type to the maximum activity in non-target cell types). They must report the distribution of this metric for generated vs. endogenous sequences, with appropriate statistical tests (e.g., Wilcoxon rank-sum) and effect sizes. For the benchmarking, they must specify the exact comparison (e.g., top-100 generated vs. top-100 endogenous by predicted activity) and report the relevant statistics for the experimental readouts.
    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness
    - **Claim pointer** The claim that DNA-Diffusion outperforms existing methods in balancing activity, specificity, and diversity.
    - **Evidence pointer** Results section "Benchmarking DNA-Diffusion against state-of-the-art methods for the generation of synthetic regulatory elements"; Figure 7 (not provided).
    - **Concern** The benchmarking section describes comparing against GANs and CNN-based regressors (CODA, DeepMEL). The text mentions a "unified performance metric" based on a radar plot, but the specific components of this metric, the exact comparison protocol, and the statistical significance of the differences are not described. The choice of the TNFSF18 locus for benchmarking and the potential for bias in this selection are not discussed.
    - **Why it matters** A key claim of the paper is the superiority of the proposed method. Without a transparent and statistically sound benchmarking protocol, this claim is unverifiable. The reader cannot determine if the observed performance is due to the model architecture, the training data, the evaluation metrics, or the specific locus chosen.
    - **Resolution test** The authors must provide a detailed description of the benchmarking protocol, including the exact metrics used for activity, specificity, and diversity. They should report the performance of all methods on all metrics, with measures of variance and statistical tests for pairwise comparisons. They should also discuss the choice of benchmarking locus and perform sensitivity analyses, if applicable.
    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Technical Soundness
    - **Claim pointer** The claim that the EXTRA-seq experiment demonstrates successful reactivation of AXIN2 in its native genomic context.
    - **Evidence pointer** Results section "DNA-Diffusion sequences can reactivate a human leukemia protective gene in an endogenous context"; Figure 6 (not provided).
    - **Concern** The text states that DNA-Diffusion sequences "effectively reactivated endogenous AXIN2 expression" and that "multiple sequences surpassed the activity of the natural protective variant." However, the magnitude of the effect, the number of replicates, the statistical significance of the reactivation compared to negative controls, and the variability between sequences are not reported. The text also notes that DNase I accessibility predictions showed little correlation with activation, which raises questions about the predictive power of the model in this context.
    - **Why it matters** This is the most direct demonstration of the therapeutic potential of the approach. The claim of "successful reactivation" must be supported by robust quantitative data. The lack of detail makes it impossible to assess the reliability and significance of the finding.
    - **Resolution test** The authors must report the effect size (e.g., log2 fold change in AXIN2 expression relative to negative controls) for each tested sequence, with error bars and statistical significance. They should also report the number of independent replicates and the criteria used to define "successful reactivation." A comparison of the activity of the best synthetic sequences to the natural protective variant, with appropriate statistics, is essential.
- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and Reproducibility
    - **Affected element** Methods section "Training process"
    - **Evidence pointer** Methods section "Training process"
    - **Issue** The description of the training process is brief. Key hyperparameters (e.g., number of diffusion steps, learning rate schedule, batch size) are not fully specified.
    - **Required correction** Provide a more detailed description of the training procedure, including all relevant hyperparameters, to ensure reproducibility.
    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Clarity and Reproducibility
    - **Affected element** Methods section "In-Silico Validation"
    - **Evidence pointer** Methods section "In-Silico Validation"
    - **Issue** The description of the "oracle" models (ChromBPNet, Enformer, MPRA predictor) is brief. The specific versions and configurations used are not stated.
    - **Required correction** Specify the exact model versions and any relevant configuration details for the oracle models used in the study.
    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Data Presentation
    - **Affected element** Results section "DNA-Diffusion-generated sequences demonstrate cell-type-specificity, accessibility, and cell-type-specific activation of cis genes in silico"
    - **Evidence pointer** Results section "DNA-Diffusion-generated sequences demonstrate cell-type-specificity, accessibility, and cell-type-specific activation of cis genes in silico"
    - **Issue** The text mentions "p < 0.01, Wilcoxon rank-sum test" for the comparison of accessibility scores, but the number of sequences compared and the exact distribution of scores are not shown.
    - **Required correction** Include the number of sequences in each group and a visual representation of the score distributions (e.g., box plots) in the main figures.
    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Interpretation
    - **Affected element** Results section "DNA-Diffusion sequences can reactivate a human leukemia protective gene in an endogenous context"
    - **Evidence pointer** Results section "DNA-Diffusion sequences can reactivate a human leukemia protective gene in an endogenous context"
    - **Issue** The finding that DNase I accessibility predictions showed little correlation with activation is interesting but not discussed in detail. The authors should comment on why this might be the case and what it implies for the model's utility.
    - **Required correction** Add a brief discussion of the discrepancy between predicted accessibility and functional activation, and its implications for the design pipeline.
- **Technical failings that need to be addressed before the case is established**
    - R1-M1: Lack of quantitative definition and statistical support for the claim of "enhanced cell-type specificity."
    - R1-M2: Lack of a transparent and statistically sound benchmarking protocol.
    - R1-M3: Insufficient quantitative detail for the EXTRA-seq results to support the claim of "successful reactivation."
- **Assessment against Nature-style criteria**
    - **Originality** The application of a conditional diffusion model to the design of cell-type-specific regulatory elements is a novel contribution. The combination of in silico prediction with both episomal and endogenous validation is a strong and relatively uncommon approach in this field.
    - **Scientific importance** The ability to design compact, specific regulatory elements has significant implications for gene therapy and synthetic biology. The demonstration of endogenous gene reactivation is an important step toward therapeutic applications. The work addresses a central challenge in the field.
    - **Interdisciplinary readership** The work is likely to appeal to researchers in genomics, synthetic biology, computational biology, and gene therapy. The writing is generally accessible, but the lack of detail in the results sections may limit its impact on a broader audience.
    - **Technical soundness** The technical soundness is currently not fully established due to the lack of quantitative detail and statistical rigor in the key claims. The model architecture and validation strategy are reasonable, but the evidence presented is insufficient to fully support the conclusions.
    - **Readability for nonspecialists** The abstract and introduction are clear and accessible. However, the results sections are dense and rely heavily on references to figures and supplementary materials that are not provided, making it difficult for a nonspecialist to follow the key findings.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea and validation strategy are promising, but the manuscript in its current form does not provide sufficient quantitative evidence to support its central claims of enhanced specificity and superior performance. A revised manuscript with detailed statistical analyses, clear definitions of metrics, and a transparent benchmarking protocol would be necessary to establish the case.

## Risk / unsupported claims
- The claim of "enhanced cell-type specificity" is not quantitatively supported in the provided text.
- The claim of "superior performance" in benchmarking is not supported by a detailed and transparent protocol.
- The claim of "successful reactivation" of AXIN2 is not supported by sufficient quantitative data.
- The claim that the model "recapitulates endogenous transcription factor binding grammar" is based on motif analysis, but the specific metrics and comparisons are not fully described.
- The generalizability of the model to other cell types beyond the three tested is not demonstrated.