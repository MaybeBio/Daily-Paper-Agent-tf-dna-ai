## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodological soundness, validity of claims, and presentation quality as presented in the provided text
- **Shared manuscript claim summary** The authors present SATORI, a self-attention based deep learning model that infers cooperativity between regulatory features (specifically transcription factor motifs) in genomic sequences. The model combines convolutional layers with a multi-head self-attention mechanism to capture interactions between regulatory elements without requiring a computationally expensive post-processing step. The authors claim that SATORI detects statistically significant TF-TF interactions, many previously reported, and outperforms existing methods (specifically FIS/DFIM) in the number of experimentally verified interactions detected, while being 8-20 times faster.
- **Visible evidence base** Abstract, Introduction, Materials and Methods (model architecture, training, motif extraction, interaction quantification, background selection, FIS comparison), Results and Discussion (four benchmarks: simulated data, TAL-GATA ChIP-Seq, human promoters, Arabidopsis), Conclusions, Data Availability
- **Missing materials affecting confidence** Supplementary figures and tables (F1-F8, S1-S7) referenced but not provided; specific hyperparameter values; detailed dataset statistics; code repository not inspected; full experimental details for benchmark datasets

## Reviewer

- **Overall assessment** The manuscript presents a novel and potentially valuable approach to inferring regulatory element interactions using self-attention mechanisms. The core idea of leveraging attention weights to directly infer feature interactions is conceptually sound and addresses a real limitation of existing attribution-based methods. The authors provide a comprehensive evaluation across simulated and real datasets, and the reported overlap with existing methods and databases is encouraging. However, the manuscript has several significant weaknesses that need to be addressed. The evaluation methodology lacks critical details, particularly regarding the statistical testing procedure, the handling of multiple testing, and the comparison with FIS. The claim of detecting "higher numbers of experimentally verified TF-TF interactions than existing methods" is not fully substantiated with quantitative comparisons. The biological interpretation of attention weights as direct evidence of cooperativity requires more careful justification. The writing is generally clear but some sections, particularly the description of the attention mechanism and the interaction quantification, could be more precise. Overall, the work is promising but requires substantial revisions to fully establish its claims.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on deep learning interpretability for genomics would be the primary audience. Researchers studying transcriptional regulation, particularly those interested in combinatorial TF interactions and enhancer biology, would find the method useful for generating hypotheses. The work is also relevant to the broader machine learning community interested in attention mechanisms for biological sequence analysis. The method's generalizability to other feature interaction problems could attract researchers working on chromatin structure, epigenomics, and potentially non-biological sequence data.

- **Major strengths**
  1. Novel application of self-attention to infer regulatory element interactions directly from model weights, avoiding expensive post-processing.
  2. Comprehensive evaluation across multiple datasets, including simulated data with known ground truth and real biological datasets.
  3. Demonstrated overlap with existing methods (FIS) and known biological databases (TRRUST, HIPPIE), providing some validation.
  4. Computational efficiency advantage over FIS is clearly demonstrated.
  5. The method is generalizable and not limited to TF-TF interactions, as stated by the authors.
  6. Code and data are made publicly available.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validity
- **Claim pointer** "Our approach combines convolutional layers with a self-attention mechanism that helps us capture a global view of the landscape of interactions between regulatory elements in a sequence. A comprehensive evaluation demonstrates the ability of SATORI to detect numerous statistically significant TF-TF interactions"
- **Evidence pointer** Section "Quantifying feature interactions", "Background selection", "Results and Discussion"
- **Concern** The statistical methodology for determining significant interactions is inadequately described. The authors state that the Mann-Whitney U Test is used to calculate significance of motif interactions, comparing attention profiles to background data. However, several critical details are missing: (1) How are attention profiles aggregated across multiple test sequences for a given filter pair? (2) What is the exact null distribution? The background selection is described as "biologically relevant" but the specific construction of background sets is not detailed in the main text. (3) How is the multiple testing problem addressed when testing thousands of potential filter-filter interactions? The Benjamini-Hochberg correction is mentioned but the total number of tests performed is not stated. (4) The threshold for discarding interactions (maximum attention value below 0.10 or 0.08) appears arbitrary and its impact on the results is not discussed. Without a clear and rigorous statistical framework, the claim of "statistically significant" interactions is not fully supported.
- **Why it matters** The core contribution of the paper is the inference of statistically significant TF-TF interactions. If the statistical methodology is flawed or inadequately described, the validity of all reported interactions is called into question. This is the central claim of the paper and must be rigorously established.
- **Resolution test** The authors should provide a detailed description of the statistical testing procedure, including: (1) exact formulation of the null hypothesis, (2) construction of background sets, (3) number of tests performed, (4) multiple testing correction procedure, and (5) sensitivity analysis of the attention threshold. Ideally, the authors should also provide a validation of their statistical approach on simulated data with known ground truth, demonstrating appropriate false discovery rates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative evaluation
- **Claim pointer** "Our method is able to detect higher numbers of experimentally verified TF-TF interactions than existing methods"
- **Evidence pointer** Section "Comparison: SATORI and FIS-based interactions", Figure 5, Supplementary Table S7
- **Concern** The claim that SATORI detects "higher numbers of experimentally verified TF-TF interactions than existing methods" is not quantitatively substantiated in the provided text. The authors state that there is "very high overlap" between the top 15 interactions detected by SATORI and FIS, but do not provide the actual numbers of experimentally verified interactions detected by each method. The comparison appears to be based on overlap of top predictions, not on the total number of verified interactions detected. Furthermore, the definition of "experimentally verified" is not clear. Is this based on the TRRUST and HIPPIE databases? If so, how many of the 123 (human) and 687 (Arabidopsis) interactions are verified? The authors report that 4 and 9 interactions are supported by TRRUST and HIPPIE respectively, but do not state how many of these were also detected by FIS. Without a direct quantitative comparison, the claim of superiority over existing methods is not established.
- **Why it matters** The claim of outperforming existing methods is a key selling point of the paper. If this claim is not properly supported, the advantage of SATORI over existing approaches is reduced to computational efficiency alone, which may not be sufficient to justify adoption.
- **Resolution test** The authors should provide a direct quantitative comparison: for each dataset, report the total number of statistically significant interactions detected by SATORI and by FIS, the number of these that are supported by external databases (TRRUST, HIPPIE), and the overlap between the two methods. This should be presented in a clear table format. The definition of "experimentally verified" should be explicitly stated.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** "SATORI, a Self-ATtentiOn based model to detect Regulatory element Interactions" and "The self-attention layer then captures potential interactions between those features"
- **Evidence pointer** Section "Model architecture", "Multi-head self-attention", "Quantifying feature interactions"
- **Concern** The interpretation of attention weights as direct evidence of cooperativity between regulatory features requires more careful justification. While attention mechanisms are designed to capture dependencies between positions, the mapping from attention weights to biological cooperativity is not straightforward. The authors do not discuss potential confounding factors, such as: (1) attention weights may reflect correlations in sequence composition rather than functional cooperativity, (2) the aggregation of attention across multiple heads and positions may obscure the signal, (3) the relationship between attention strength and biological relevance is assumed but not validated. The authors do provide some validation through overlap with known databases, but this is limited. A more rigorous approach would involve demonstrating that the inferred interactions are predictive of functional outcomes, such as gene expression changes, or that they are enriched for known regulatory mechanisms beyond simple database overlap.
- **Why it matters** The biological validity of the inferred interactions is the ultimate test of the method's utility. If attention weights do not reliably reflect functional cooperativity, the method's outputs could be misleading for biologists using it to generate hypotheses.
- **Resolution test** The authors should provide additional validation of the biological relevance of their inferred interactions. This could include: (1) comparison with independent experimental data on TF cooperativity, (2) demonstration that inferred interactions are enriched for TFs known to co-bind in specific regulatory contexts, (3) analysis of whether the strength of attention correlates with the strength of cooperative effects, or (4) experimental validation of a small number of novel predictions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical clarity
- **Claim pointer** "The final output is then collapsed along the hidden (attention) layer dimensions through addition and normalized by the mean and the standard deviation of the result. Empirically we find that this final step is not only computationally efficient but also leads to better model accuracy in comparison to flattening the attention layer output. For explicit details, please refer to the Supplementary Material."
- **Evidence pointer** Section "Multi-head self-attention"
- **Concern** The description of the attention mechanism and the subsequent processing steps is insufficient for reproducibility. The authors refer to the Supplementary Material for details, but the main text should provide a clear and complete description of the architecture. Specifically, the following are unclear: (1) How are the attention heads combined? The authors mention taking the maximum at each position to collapse heads, but this is described in the context of interaction inference, not the model output. (2) What is the dimensionality of the attention layers? (3) How is the output of the attention layer used for classification? The description of "collapsed along the hidden dimensions through addition" is vague. (4) The role of the optional RNN layer is not clearly explained in the context of the attention mechanism. A clear architectural diagram and a precise mathematical description are needed.
- **Why it matters** Reproducibility is a fundamental requirement for scientific publications. Without a clear description of the model architecture, other researchers cannot implement or build upon the method.
- **Resolution test** The authors should provide a complete and precise description of the model architecture in the main text, including all equations, tensor dimensions, and the flow of data through the network. The Supplementary Material should contain the full details, but the main text should be self-contained enough for a knowledgeable reader to understand the method.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "Our method is able to detect higher numbers of experimentally verified TF-TF interactions than existing methods" but does not specify which existing methods are being compared. The abstract also does not mention the computational efficiency advantage, which is a key selling point.
- **Required correction** Specify the comparison method (FIS/DFIM) in the abstract and briefly mention the computational advantage.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of reporting
- **Affected element** Results and Discussion, Benchmark 1
- **Evidence pointer** Section "Benchmark 1: embedded motif interactions in simulated genomic sequences"
- **Issue** The authors state that "all the significant interactions returned by our model involve SIX5 and ELF1 as expected" but do not report the number of significant interactions found, nor the false positive rate. Given that the dataset has a known ground truth, this is a missed opportunity to quantify the method's precision and recall.
- **Required correction** Report the number of true positive, false positive, and false negative interactions in the simulated dataset, along with precision and recall metrics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results and Discussion, Benchmark 2
- **Evidence pointer** Section "Benchmark 2: inferring TAL-GATA motif interactions from ChIP-Seq data"
- **Issue** The authors report AUC values for model performance but do not provide confidence intervals or standard deviations. It is unclear if the reported AUC values are from a single train/test split or averaged over multiple runs.
- **Required correction** Report the mean and standard deviation of AUC across multiple runs or provide confidence intervals.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Biological interpretation
- **Affected element** Results and Discussion, Human promoters
- **Evidence pointer** Section "The TF interaction landscape across human promoters"
- **Issue** The authors report that 4 out of 123 interactions are supported by TRRUST and 9 by HIPPIE. This is a very small fraction. The authors should discuss the potential reasons for this low overlap, such as the incompleteness of these databases or the possibility that many inferred interactions are false positives.
- **Required correction** Add a discussion of the low overlap with existing databases and its implications for the method's precision.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Materials and Methods, Background selection
- **Evidence pointer** Section "Background selection"
- **Issue** The section on background selection is incomplete. The authors state that "we use a biologically relevant background depending on the experiment" but do not describe what these backgrounds are. This is critical for understanding the statistical testing.
- **Required correction** Provide a detailed description of the background selection for each dataset in the main text or clearly refer to the specific supplementary section.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figures
- **Evidence pointer** Figures 3, 4, 5
- **Issue** The figures are referenced but not described in the text. The authors should provide a brief description of what is shown in each figure in the text.
- **Required correction** Add a sentence or two describing the key findings shown in each figure.

- **Technical failings that need to be addressed before the case is established**
  1. Incomplete statistical methodology description (R1-M1)
  2. Lack of quantitative comparison with FIS (R1-M2)
  3. Insufficient architectural details for reproducibility (R1-M4)
  4. Incomplete background selection description (R1-m5)

- **Assessment against Nature-style criteria**
  - **Originality**: The application of self-attention to infer regulatory element interactions is novel. While attention mechanisms have been used in genomics, the specific focus on extracting interaction information from attention weights is a new contribution. The idea is a natural extension of existing work but has not been explicitly explored in this context.
  - **Scientific importance**: The problem of inferring cooperativity between regulatory elements is of significant importance in understanding gene regulation. The method has the potential to generate testable hypotheses. However, the biological validation is limited, and the practical impact is not yet fully demonstrated.
  - **Interdisciplinary readership**: The work is primarily of interest to computational biologists and bioinformaticians. The biological findings are not sufficiently developed to attract a broad biological audience. The method could be of interest to the machine learning community, but the presentation is not tailored to that audience.
  - **Technical soundness**: The core idea is sound, but the statistical methodology and evaluation are not rigorously described. The lack of quantitative comparison with existing methods and the incomplete description of the statistical testing procedure are significant weaknesses. The technical soundness cannot be fully assessed without the supplementary material.
  - **Readability for nonspecialists**: The manuscript is generally well-written and accessible to a computational biology audience. However, the description of the attention mechanism and the interaction inference process could be clearer for readers not deeply familiar with deep learning. The biological context is adequately introduced.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the preliminary results are encouraging. However, the statistical methodology must be rigorously described and validated, and the comparison with existing methods must be quantified. The manuscript requires major revisions before the claims are fully established.