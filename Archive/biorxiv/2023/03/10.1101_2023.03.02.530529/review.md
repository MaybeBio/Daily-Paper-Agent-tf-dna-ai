## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, and results sections, as provided.
- **Assessment boundary** Evaluation is limited to the scientific content, methodology, and claims presented in the provided text. No external data, code, or supplementary materials were accessed.
- **Shared manuscript claim summary** The authors introduce GrID-Net, a graph neural network that generalizes Granger causal inference to partial orderings, to infer causal locus-gene regulatory relationships from single-cell multimodal data (scATAC-seq and scRNA-seq). They apply this method to link schizophrenia-associated genetic variants to putative target genes and identify transcription factor binding disruptions as a key mechanism.
- **Visible evidence base** The manuscript provides descriptions of benchmarking against correlation-based methods and the ABC model, analyses of pseudotime lags and enhancer states, and applications to schizophrenia variant-gene linking and TF binding affinity predictions. Figures and tables are referenced but not provided.
- **Missing materials affecting confidence** The full text of the Supplementary Note, all figures (main and supplementary), Supplemental Tables 1 and 2, and the code repository were not available for review. This limits the ability to verify methodological details, statistical results, and the completeness of the data analysis.

## Reviewer
- **Overall assessment** This manuscript presents a conceptually interesting and technically ambitious approach to a significant problem in genomics: linking noncoding variants to their target genes in a cell-type-specific manner. The core idea of exploiting the temporal offset between chromatin accessibility and gene expression, termed "cell-state parallax," is a novel and potentially powerful framing. The generalization of Granger causality to partial orderings via graph neural networks is a sound and timely methodological contribution. However, the strength of the conclusions is heavily dependent on the benchmarking and validation results, which are only partially visible in the provided text. The lack of access to the figures and supplementary materials prevents a full assessment of the method's performance and the robustness of the biological findings. The claims of causal inference, while appropriately framed as hypotheses, require the benchmarking evidence to be compelling.
- **Who would be interested in the results, and why** This work will be of high interest to computational biologists and bioinformaticians developing methods for single-cell multi-omics data integration and regulatory genomics. Researchers studying the genetic architecture of complex diseases, particularly neuropsychiatric disorders like schizophrenia, will also find the application to variant-to-gene mapping relevant. The conceptual framework of "cell-state parallax" may also appeal to a broader audience interested in causal inference from observational single-cell data.
- **Major strengths**
    1.  The conceptual advance of "cell-state parallax" is a clear and compelling framing for a known biological phenomenon, providing a strong rationale for the methodological approach.
    2.  The methodological contribution of generalizing Granger causality to partial orderings using GNNs is a significant and novel theoretical step that could have applications beyond genomics.
    3.  The application to a high-impact disease like schizophrenia, with a focus on cell-type-specific mechanisms and TF binding disruptions, demonstrates the potential utility of the method for generating testable biological hypotheses.
    4.  The benchmarking strategy against multiple methods (correlation, pseudocell, ABC) and multiple datasets is a rigorous approach, provided the results are as strong as described.
- **Major Concerns**
    - **R1-M1**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Technical Soundness
        - **Claim pointer** The claim that GrID-Net "outperforms existing state-of-the-art approaches for accurately identifying noncoding locus-gene links" is central to the paper's value proposition.
        - **Evidence pointer** Figure 2a, Figure 2b, Figure S1, Figure S2
        - **Concern** The provided text states that GrID-Net exhibits "7-27% higher AUROC" in 3 of 4 datasets. However, the actual performance metrics, the statistical significance of these improvements, and the performance on the 4th dataset are not detailed. The near-random performance of correlation-based methods is surprising and warrants scrutiny. Without seeing the actual ROC curves, precision-recall curves, and error bars, it is impossible to assess the magnitude and reliability of the claimed improvement.
        - **Why it matters** The entire premise of the paper rests on the superior performance of GrID-Net. If the improvement is marginal or not statistically robust, the case for the method's utility is significantly weakened.
        - **Resolution test** Provide the full benchmarking results, including AUROC and AUPRC values for all methods and datasets, with confidence intervals and statistical tests. Show the performance on the 4th dataset and explain any discrepancies.
    - **R1-M2**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Technical Soundness
        - **Claim pointer** The claim that GrID-Net's superior accuracy is due to its ability to resolve "cell-state parallax" and detect poised enhancers.
        - **Evidence pointer** Figure 2c, Figure 2d
        - **Concern** The analysis showing that GrID-Net prioritizes pairs with longer pseudotime lags and poised enhancers is presented as evidence for the mechanism. However, the text does not provide the effect sizes or the distributions of these metrics. It is unclear if this is a strong, dominant effect or a subtle trend. The comparison to "peak-gene pairs that all methods score highly" is interesting but the definition of this set and the statistical comparison are not fully described.
        - **Why it matters** This is the key biological validation of the "cell-state parallax" concept. If the effect is weak or not specific to GrID-Net, the conceptual advance is less impactful.
        - **Resolution test** Provide quantitative data on the pseudotime lag distributions and enhancer state proportions for pairs prioritized by different methods, with appropriate statistical tests. Clarify the definition of the comparison sets.
    - **R1-M3**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Technical Soundness
        - **Claim pointer** The claim that GrID-Net links schizophrenia variants to genes and identifies TF binding disruptions as a key mechanism.
        - **Evidence pointer** Figure 3, Figure 4, Supplemental Tables 1 and 2
        - **Concern** The results section describes the output of the analysis but provides no quantitative evidence of its validity. The enrichment of the 132 genes for "genes implicated in the original SCZ GWAS study" is a weak validation, as it may reflect the input data. The correlation between TF binding affinity changes and differential expression in patient-derived cells (r=0.59) is presented, but the significance and robustness of this correlation are not discussed. The specific claims about NAB2, KCNG2, and SLC12A6 are interesting but are presented as anecdotal findings without a systematic analysis of their significance.
        - **Why it matters** The application to schizophrenia is a major selling point of the paper. Without a clear demonstration that the predicted variant-gene links are more accurate or provide new biological insight beyond existing methods, the significance of this application is unclear.
        - **Resolution test** Provide a more rigorous validation of the schizophrenia findings. This could include enrichment analyses against independent datasets, comparison with other variant-to-gene mapping methods, and a more detailed statistical analysis of the TF binding and expression correlation.
    - **R1-M4**
        - **Severity** Major
        - **Blocking** Yes
        - **Axis** Technical Soundness
        - **Claim pointer** The claim that GrID-Net is robust to data sparsity, a key challenge in scATAC-seq data.
        - **Evidence pointer** Figure S2
        - **Concern** The text states that GrID-Net "better handled sparse data" but does not provide details on how this was assessed. The specific definitions of "sparse genes" and "sparse peaks" are not given, and the performance metrics for these subsets are not shown.
        - **Why it matters** Data sparsity is a major practical challenge, and the method's ability to handle it is a key claimed advantage. Without clear evidence, this claim is unsubstantiated.
        - **Resolution test** Provide a detailed description of the sparsity analysis, including the definitions, the performance metrics for different sparsity levels, and a comparison with other methods under these conditions.
- **Minor Comments**
    - **R1-m1**
        - **Severity** Minor
        - **Axis** Readability for Nonspecialists
        - **Affected element** Introduction, "cell-state parallax" concept
        - **Evidence pointer** Introduction section
        - **Issue** The analogy to optical parallax is helpful, but the explanation of how this translates to a "partial ordering" in a graph could be clearer for a broader audience.
        - **Required correction** Consider adding a more explicit, step-by-step explanation of how the temporal offset between modalities leads to a partial ordering of cells, perhaps with a simple illustrative example.
    - **R1-m2**
        - **Severity** Minor
        - **Axis** Technical Soundness
        - **Affected element** Methods, DAG construction
        - **Evidence pointer** Methods section, "Directed acyclic graph (DAG) construction"
        - **Issue** The method for breaking cycles in the k-NN graph is only briefly mentioned ("so long as any resulting cycles are broken"). The specific algorithm used is not described.
        - **Required correction** Provide a citation or a brief description of the cycle-breaking algorithm for completeness and reproducibility.
    - **R1-m3**
        - **Severity** Minor
        - **Axis** Technical Soundness
        - **Affected element** Methods, TF binding affinity changes
        - **Evidence pointer** Methods section, "TF binding affinity changes"
        - **Issue** The text states that the effect of a variant on TF binding is evaluated by comparing FIMO p-values. It is unclear how a single "fold change" is calculated from these p-values.
        - **Required correction** Clarify the exact formula or method used to convert the FIMO p-values into the reported "fold change" in binding affinity.
    - **R1-m4**
        - **Severity** Minor
        - **Axis** Scientific Importance
        - **Affected element** Discussion
        - **Evidence pointer** Discussion section
        - **Issue** The discussion of the "cell-state parallax" concept could be expanded to more explicitly discuss its potential limitations and the types of biological systems where it might not apply.
        - **Required correction** Add a paragraph discussing potential caveats, such as systems where the temporal offset is minimal or where the relationship between epigenome and transcriptome is not strictly causal.

## Risk / unsupported claims
- The claim that GrID-Net "outperforms" other methods is not fully supported without the actual benchmarking figures and statistical analysis.
- The claim that the identified schizophrenia genes are "enriched for genes implicated in the original SCZ GWAS study" is a weak validation and may be circular.
- The specific biological mechanisms proposed for NAB2, KCNG2, and SLC12A6 are presented as findings but are not validated experimentally or through independent replication.
- The claim that GrID-Net "can be applied broadly to other domains" is speculative and not supported by any results in the manuscript.
- The overall performance of the method on the sci-CAR dataset is not described, leaving a gap in the benchmarking evidence.
- The robustness of the method to different hyperparameters or dataset sizes is not assessed.