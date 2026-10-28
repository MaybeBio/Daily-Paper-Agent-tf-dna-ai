## Review setup

- **Input scope** Full manuscript text (abstract, main text, results, methods, figure legends not provided, supplementary tables referenced but not provided)
- **Assessment boundary** Scientific content, experimental design, data interpretation, and technical soundness as presented in the provided text. Figures, supplementary tables, and extended data figures are referenced but not directly assessable.
- **Shared manuscript claim summary** The authors develop ChIP-ISO, a high-throughput assay to measure FOXA1 binding to thousands of synthetic sequences integrated at a fixed genomic locus. They report that FOXA1 binding is strongly enhanced by co-binding of AP-1 and CEBPB, that FOXA1 and AP-1 exhibit binding cooperativity in vitro, that local sequence features rather than chromatin context (including heterochromatin) primarily determine FOXA1 binding, and that AP-1 contributes to cell-type-specific FOXA1 binding.
- **Visible evidence base** Abstract, main text narrative, methods descriptions, in-text references to figures (Fig. 1a-d, 2a-i, 3a-g, 4a-k, 5a-i, 6a-g, 7a-e), extended data figures (1-10), and supplementary tables (S1, S3). Actual figure images, numerical data, and statistical analyses are not provided.
- **Missing materials affecting confidence** Figure panels and their data, supplementary tables (S1, S2, S3), extended data figures, exact statistical test results, effect sizes, confidence intervals, and raw data. The absence of these materials limits quantitative verification of the claims.

## Reviewer

- **Overall assessment** This manuscript addresses an important question in gene regulation: how pioneer factors achieve binding specificity despite their ability to access nucleosomal DNA. The development of ChIP-ISO is a potentially valuable technical contribution that allows systematic dissection of sequence features in a controlled genomic context. The finding that AP-1 is a major determinant of FOXA1 binding, with evidence for cooperative binding in vitro and in vivo, is interesting and potentially significant. However, the manuscript as presented has several technical concerns that need to be addressed. The claim that chromatin context plays a minor role in FOXA1 binding is based on a limited set of comparisons and may be overstated given the complexity of chromatin states. The neural network analyses are described but their interpretability and the strength of the conclusions drawn from them require closer scrutiny. The in vitro cooperativity data, while suggestive, need more rigorous quantitative analysis to support the claim of direct protein-protein interactions. Overall, the work is promising but the current evidence does not fully establish all the major claims.
- **Who would be interested in the results, and why** Researchers studying transcription factor binding specificity, pioneer factor biology, enhancer regulation, and the mechanisms underlying cell-type-specific gene expression. The ChIP-ISO method itself will be of interest to the genomics and gene regulation communities as a tool for high-throughput dissection of sequence determinants of TF binding. The finding of FOXA1-AP-1 cooperativity has implications for understanding how pioneer factors function in development and disease, particularly in cancers where both factors are implicated.
- **Major strengths** 1) The development of ChIP-ISO is a novel and potentially powerful approach that addresses a key limitation in the field, namely the difficulty of dissecting individual genetic determinants of TF binding in the native genome. 2) The combination of in vivo (ChIP-ISO, ChIP-seq), in vitro (EMSA-seq, EMSA), and in silico (CNN, Bichrom) approaches provides multiple lines of evidence. 3) The finding that AP-1 is a major co-factor for FOXA1 binding, with evidence for cooperativity, is biologically significant and may explain cell-type-specific FOXA1 binding. 4) The systematic analysis of motif features, including the importance of motif strength and co-factor proximity, provides quantitative insights.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that ChIP-ISO accurately measures FOXA1 binding to integrated synthetic sequences, with a correlation coefficient of 0.76 between biological replicates.
- **Evidence pointer** Fig. 1b, Fig. 1c, Fig. 1d, Methods section "Amplicon Sequencing for ChIP-ISO"
- **Concern** The correlation coefficient of 0.76 between biological replicates is relatively modest for a high-throughput assay. The manuscript does not report the dynamic range of the ChIP-ISO signal, the number of sequences with low read counts, or the criteria for excluding sequences from analysis. The bimodal distribution shown in Fig. 1c suggests a population of low-binding sequences, but the threshold for defining "bound" versus "unbound" is not clearly stated. The validation with ChIP-qPCR (Fig. 1d) is described for only three sequences, which is a very small sample size to establish the accuracy of the method across the full range of binding affinities. Additionally, the manuscript does not report whether the ChIP-ISO signal is normalized for copy number of the integrated sequence, which could vary between cells and affect the measurements.
- **Why it matters** The entire study relies on the accuracy and reproducibility of ChIP-ISO measurements. If the assay has high noise or systematic biases, all downstream conclusions about sequence features affecting FOXA1 binding could be compromised. The modest replicate correlation and limited validation raise concerns about the quantitative reliability of the data.
- **Resolution test** The authors should report the full distribution of ChIP-ISO signals, the number of sequences passing quality filters, and the criteria for these filters. They should validate the assay with a larger number of sequences (e.g., 10-20) across a range of binding affinities using an independent method. They should also describe how copy number variation of the integrated sequences is controlled for, and report the signal-to-noise ratio of the assay.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for conclusions
- **Claim pointer** The authors claim that "FOXA1 binding is determined more by local sequences than chromatin context, including eu-/heterochromatin" and that "chromatin context plays only a minor role, if any, in FOXA1 binding."
- **Evidence pointer** Fig. 6a-g, Extended Data Fig. 8a-d, Methods section "Neural network training"
- **Concern** This is a strong claim that contradicts a substantial body of literature showing that chromatin context, including nucleosome positioning, histone modifications, and higher-order chromatin structure, can influence TF binding. The evidence presented has several limitations. First, the comparison of native vs. AAVS1 locus binding is based on a limited number of sequences (56 from H3K9me3 regions, and a similar number from H3K27me3 regions), which may not be representative of the diversity of chromatin states. Second, the CRISPRi experiment (Fig. 6i-j) only tests one locus (CCND1e) and one time point (48 hours), which may not capture the full effect of heterochromatin formation. Third, the Bichrom neural network analysis shows that adding H3K9me3 does not improve prediction, but this could be because the model is not sensitive enough to capture the effect, or because the training data is limited. The correlation coefficient of 0.69 between native and AAVS1 binding (Fig. 6g) actually suggests that there is substantial variation (about 50% of the variance) that is not explained by local sequence, which could be due to chromatin context.
- **Why it matters** The claim that chromatin context plays a minor role in FOXA1 binding is a major conclusion of the paper and has implications for understanding pioneer factor function. If this claim is overstated, it could mislead the field. The evidence presented is not sufficient to rule out a significant role for chromatin context.
- **Resolution test** The authors should expand the analysis to include a larger and more diverse set of sequences from different chromatin states. They should perform time-course experiments for the CRISPRi-mediated H3K9me3 deposition to assess whether longer-term heterochromatin formation has an effect. They should also report the variance explained by local sequence vs. chromatin features in their models, and discuss the limitations of their approach in detecting chromatin context effects.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "FOXA1 and AP-1 show binding cooperativity in vitro" and that "there may be protein-protein interactions between these two factors that allow one to be tethered by the other."
- **Evidence pointer** Fig. 5f-i, Methods section "FOXA1 and AP-1 Co-Binding Electrophoretic Mobility Shift Assays (EMSAs)"
- **Concern** The EMSA experiments are described as showing cooperativity, but the quantitative analysis is limited. The manuscript reports that "the presence of AP-1 moderately promotes the binding of FOXA1, and vice versa" but does not provide the magnitude of the effect, the number of replicates, or statistical significance. The claim that cooperativity is observed even in the absence of one factor's motif (Fig. 5h-i) is interesting but the experimental design needs clarification. Specifically, it is not clear how the authors distinguish between true protein-protein interactions and non-specific DNA binding effects. The concentrations of FOXA1 and AP-1 used in the EMSA are not reported in the text, and it is unclear whether the observed effects are within a physiologically relevant range.
- **Why it matters** The claim of direct protein-protein interactions between FOXA1 and AP-1 is a key mechanistic finding. If the evidence is not rigorous, the conclusion is not well supported. The observation of cooperativity without a binding site for one factor is unusual and needs careful validation.
- **Resolution test** The authors should provide quantitative EMSA data with multiple replicates, including the concentrations of all components, and report the fold-change in binding with and without the partner factor. They should also perform control experiments to rule out non-specific effects, such as using a mutant AP-1 that cannot bind DNA or a competitor DNA. Ideally, they should use an independent method (e.g., pull-down assays, surface plasmon resonance) to confirm direct protein-protein interactions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Support for conclusions
- **Claim pointer** The authors claim that "AP-1 is partially responsible for differential binding of FOXA1 in different cell types" based on analysis of A549, HepG2, and MCF-7 cells.
- **Evidence pointer** Fig. 7a-e, Extended Data Fig. 9a-b, Methods section "Cell Type-Specific FOXA1 and AP-1 Motifs, Binding, and Expression"
- **Concern** The evidence for this claim is largely correlative. The authors show that AP-1 expression is higher in A549 cells and that A549-specific FOXA1 peaks are enriched for AP-1 motifs. However, the causal relationship is not directly tested. The A-FOS experiment (Fig. 4) shows that inhibiting AP-1 in A549 cells reduces FOXA1 binding at AP-1-associated sites, but this does not demonstrate that differences in AP-1 expression between cell types cause the differential FOXA1 binding. The analysis of HepG2 and MCF-7 cells is based on published data, and the comparison may be confounded by other differences between cell lines (e.g., genetic background, culture conditions, chromatin state). The statement that AP-1 is "partially responsible" is vague and not quantified.
- **Why it matters** The claim of cell-type-specific regulation by AP-1 is an important implication of the study. If the evidence is only correlative, the conclusion is not strongly supported. The manuscript would benefit from a more direct test of causality.
- **Resolution test** The authors should perform experiments to directly test whether manipulating AP-1 expression in HepG2 or MCF-7 cells (e.g., overexpression) can shift FOXA1 binding toward AP-1-associated sites. Alternatively, they could use a more systematic approach, such as comparing FOXA1 binding in multiple cell types with varying AP-1 expression levels and controlling for other confounding factors.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors use neural network models (CNN and Bichrom) to analyze FOXA1 binding and claim that "AP-1 and CEBPB are the most prominent co-factor motifs" and that "incorporation of H3K9me3 in the neural network analyses does not improve FOXA1 binding prediction."
- **Evidence pointer** Fig. 3f-g, Fig. 6h, Methods section "Neural network architectures" and "Neural network training"
- **Concern** The neural network analysis is described but the details are insufficient for evaluation. The manuscript does not report the hyperparameters used, the training procedure, the number of training epochs, or the performance on validation sets. The claim that AP-1 and CEBPB are the most prominent co-factor motifs is based on TF-MoDISco analysis, but the significance of these motifs is not quantified. The Bichrom model comparison (Fig. 6h) shows that adding H3K9me3 does not improve performance, but the baseline performance and the statistical significance of the differences are not reported. The negative result with H3K9me3 could be due to the model architecture or the limited training data.
- **Why it matters** The neural network analyses are used to support several key claims in the paper. If the models are not properly trained or evaluated, the conclusions drawn from them are not reliable. The lack of detail makes it impossible to assess the validity of the approach.
- **Resolution test** The authors should provide full details of the neural network training and evaluation, including hyperparameters, training curves, and performance metrics. They should report the statistical significance of the motif enrichment analyses. They should also perform ablation studies to test the contribution of different features to the model performance.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, statement 2
- **Issue** The abstract states "FOXA1 binding is strongly affected by co-binding TFs AP-1 and CEBPB" but does not specify the direction of the effect (enhancement vs. inhibition). The main text clarifies that AP-1 enhances binding, but the abstract should be more precise.
- **Required correction** Revise to "FOXA1 binding is strongly enhanced by co-binding TFs AP-1 and CEBPB" for clarity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section
- **Evidence pointer** Results section, "ChIP-ISO assay allows highly parallel measurements" paragraph
- **Issue** The manuscript states that the library contains 3,203 sequences but does not describe the full composition of the library in the main text. The breakdown is only in Table S1, which is not provided.
- **Required correction** Provide a summary of the library composition in the main text, including the number of sequences in each category (e.g., CCND1e variants, native sequences, controls).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Fig. 2c, Fig. 3c-e
- **Evidence pointer** Fig. 2c, Fig. 3c-e
- **Issue** The manuscript reports significant effects of mutating AP-1 and CEBPB motifs on FOXA1 binding but does not report effect sizes or confidence intervals. The number of biological replicates for the ChIP-ISO experiments is not stated.
- **Required correction** Report the number of replicates, effect sizes, and confidence intervals for the key comparisons. Consider adding a statistical methods subsection.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph 3
- **Issue** The discussion of the "soft motif syntax" model is interesting but speculative. The authors should clarify which of their data directly supports this model versus which parts are speculative.
- **Required correction** Clearly distinguish between data-supported conclusions and speculative interpretations in the discussion.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Neural network training"
- **Evidence pointer** Methods, "Neural network training"
- **Issue** The methods for neural network training do not specify the random seed or the number of independent training runs. This is important for reproducibility.
- **Required correction** Report the random seed and the number of independent runs, and report the mean and standard deviation of performance metrics across runs.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Fig. 4
- **Evidence pointer** Fig. 4a-k
- **Issue** The description of the A-FOS experiment is clear, but the figure legend is not provided. The text refers to "lost" and "gained" peaks, but the criteria for these categories are not defined in the text.
- **Required correction** Define the criteria for "lost" and "gained" peaks in the text or figure legend.

## Risk / unsupported claims

- The claim that "chromatin context plays only a minor role, if any, in FOXA1 binding" is not fully supported by the evidence presented. The limited number of sequences tested and the potential insensitivity of the neural network approach do not rule out a significant role for chromatin context.
- The claim of direct protein-protein interactions between FOXA1 and AP-1 is based on EMSA data that are not quantitatively rigorous. The observation of cooperativity without a binding site for one factor needs further validation.
- The claim that "AP-1 is partially responsible for differential binding of FOXA1 in different cell types" is based on correlative evidence and lacks direct causal testing.
- The neural network analyses are described without sufficient detail to assess their validity, and the conclusions drawn from them (e.g., the prominence of AP-1 and CEBPB motifs) are not quantified with statistical significance.
- The manuscript states that "FOXA1 binding is determined more by local sequences than chromatin context" but the correlation coefficient of 0.69 between native and AAVS1 binding suggests that a substantial fraction of variance is unexplained, and the source of this variance is not addressed.