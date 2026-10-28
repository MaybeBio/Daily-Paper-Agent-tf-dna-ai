## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability)
- **Assessment boundary** Scientific content, methodological rigor, claims versus evidence, and presentation quality as presented in the provided text
- **Shared manuscript claim summary** The authors benchmark PWM-, SVM-, and deep learning-based models for transcription factor binding site prediction using human ChIP-seq data from ENCODE, evaluating the impact of training dataset size, sequence length, kernel functions, and synthetic versus biological background data, and provide a database of pretrained SVM models.
- **Visible evidence base** Text descriptions of methods and results; references to figures (Figs 1–5), supplementary figures, and supplementary tables; no actual data values, figures, or supplementary material were provided
- **Missing materials affecting confidence** All figures, supplementary files, tables with numerical results, and the actual database contents; no quantitative results are visible in the provided text

## Reviewer
- **Overall assessment** This manuscript addresses a relevant and timely question in regulatory genomics: how do different classes of TFBS prediction models perform under varying data conditions? The study design is thoughtful, covering multiple factors (dataset size, sequence length, kernel choice, background type) and using both synthetic and biological negatives. The authors also provide a practical resource in the form of a pretrained SVM model database. However, the manuscript as provided is largely descriptive, with no quantitative results visible in the text. The claims of performance differences and practical guidance cannot be evaluated without the actual data. The novelty is moderate, as benchmarking studies of this type exist, though the systematic comparison across three model classes with a focus on background data effects adds value. The writing is generally clear but contains some redundancy and minor errors. The main limitation is that the evidence base is not visible in the provided material, making it impossible to assess whether the conclusions are supported.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory genomics, transcription factor binding prediction, and motif discovery. Practitioners who need to choose between PWM, SVM, or deep learning approaches for their specific datasets would benefit from the practical guidance. The pretrained SVM model database could be useful for researchers who want to apply SVM-based TFBS prediction without training their own models. The study is also relevant to method developers who want to understand the strengths and limitations of existing approaches.

- **Major strengths**  
  1. Systematic benchmarking across three model classes (PWM, SVM, DL) with multiple controlled experimental conditions  
  2. Use of both synthetic and biologically relevant (DNase-seq) background data, addressing a practical concern in model evaluation  
  3. Inclusion of a needle-in-the-haystack scenario to test robustness under class imbalance  
  4. Provision of a practical resource (pretrained SVM model database) that could lower the barrier for adoption  
  5. Consideration of computational cost as a factor in model selection

- **Major Concerns**

  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Evidence sufficiency  
  - **Claim pointer** The manuscript claims that SVM-based models "generally outperform PWMs in most scenarios" and that specific trends exist for dataset size, sequence length, and kernel function effects on performance.  
  - **Evidence pointer** Section "Benchmarking position weight matrix, support vector machine, and deep learning motif models' performance"; Figures 2–4; Supplementary Figures 1–6; Supplementary Tables 1–3  
  - **Concern** The provided text contains no actual numerical results. All performance comparisons are described qualitatively (e.g., "AUPRC = 0.7", "AUPRC = 0.72") but no statistical tests, confidence intervals, or effect sizes are reported in the text. The figures and supplementary materials that would contain this information were not provided.  
  - **Why it matters** The central claims of the paper are about comparative performance. Without visible quantitative results and appropriate statistical analysis, the reader cannot assess whether observed differences are meaningful or within noise. The claim that SVM models "generally outperform" PWMs requires evidence of consistent, statistically significant differences across the 59 datasets.  
  - **Resolution test** Provide the actual performance values, distributions across datasets, and statistical comparisons (e.g., paired tests across datasets) in the main text or supplementary material. The claims should be supported by visible data.

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Methodological completeness  
  - **Claim pointer** The manuscript states that "we employed a systematic approach integrating model training and evaluation" and describes the training/testing split as "all sequences on chromosome 2 to the test sets."  
  - **Evidence pointer** Section "Analysis workflow for training and evaluating position weight matrix–, support vector machine–, and deep learning–based motif models"; Supplementary File Section 6  
  - **Concern** The description of the training and evaluation protocol is incomplete. Key details are missing: (1) how hyperparameters were selected for each model (e.g., SVM cost parameter, kernel parameters, motif width for PWM); (2) whether the same training/testing splits were used across all models; (3) how the DNase-seq background was matched to the ChIP-seq positives (e.g., same chromosomes, similar GC content, accessibility); (4) how the 1:10 imbalance was constructed; (5) whether any cross-validation was performed. The reference to Supplementary File Section 6 for "rationale" does not substitute for a clear description in the main text.  
  - **Why it matters** Reproducibility and fairness of comparison depend on these details. If hyperparameters were not optimized consistently across models, performance differences could reflect tuning artifacts rather than model capabilities. The construction of negative sets is particularly important for the validity of the benchmark.  
  - **Resolution test** Provide a complete description of the training protocol, hyperparameter selection, negative set construction, and evaluation procedure in the main text or a clearly referenced supplement.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Scope and generalizability  
  - **Claim pointer** The manuscript claims to provide "practical guidance for selecting and tailoring models to specific biological datasets" and that the database of 2393 SVM models "aims to facilitate broader adoption of SVM-based methods."  
  - **Evidence pointer** Abstract; Section "Discussion"; Data availability  
  - **Concern** The study uses 59 TFs from ENCODE, which is a reasonable but limited set. The guidance provided in Table 2 (not visible) appears to be based on this specific set. The generalizability of the conclusions to other TFs, other cell types, or other species is not discussed. Additionally, the deep learning component is limited to a single model (Nucleotide Transformer), which may not be representative of the broader class of DL-based methods. The claim of practical guidance may be overstated given the limited scope.  
  - **Why it matters** Readers may apply the guidance to datasets outside the tested range. If the conclusions are specific to the tested conditions, this should be stated clearly. The DL comparison is particularly limited, as many other DL architectures exist for TFBS prediction.  
  - **Resolution test** Discuss the limitations of the TF set and the DL model choice. Provide guidance on when the conclusions are likely to transfer and when they may not. Consider including additional DL models or clearly stating the scope of the comparison.

  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Interpretability and analysis depth  
  - **Claim pointer** The manuscript states that "analyzing the positional distribution of motif scores on positive test sequences" was performed for the best- and worst-performing TFs, and that "LS-GKM may incorporate additional regulatory elements into its predictions."  
  - **Evidence pointer** Section "Benchmarking position weight matrix, support vector machine, and deep learning motif models' performance"; Figure 5; Supplementary Figure 7  
  - **Concern** The analysis of positional motif scores is described only briefly. The claim that LS-GKM may capture "secondary, functionally relevant sequences" is speculative and not supported by any visible analysis. No details are provided on how the positional distributions were quantified, how "best" and "worst" performing TFs were selected, or what statistical evidence supports the interpretation.  
  - **Why it matters** This analysis could provide valuable biological insight into what different models learn. As presented, it is too superficial to support the interpretive claims. The speculation about secondary regulatory elements needs either stronger evidence or clearer framing as a hypothesis.  
  - **Resolution test** Provide quantitative analysis of the positional distributions, including statistical comparisons between models. Either provide evidence for the claim about secondary elements or reframe it as a hypothesis for future work.

- **Minor Comments**

  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Section "Analysis workflow for training and evaluating position weight matrix–, support vector machine–, and deep learning–based motif models"  
  - **Evidence pointer** "Supplementary File Section 6 details the rationale and highlights its minimal impact on performance impact on performance variation."  
  - **Issue** There is a duplicated phrase "impact on performance impact on performance variation." This appears to be a typographical error.  
  - **Required correction** Correct the sentence to read "highlights its minimal impact on performance variation."

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Completeness  
  - **Affected element** Section "Position weight matrix motif models"  
  - **Evidence pointer** "PWMs are often visualized as sequence logos [65], where the height of each nucleotide corresponds to its information content., PWMs have become the standard model..."  
  - **Issue** There is a grammatical error with a period followed by a comma: "information content., PWMs". This disrupts readability.  
  - **Required correction** Replace "information content., PWMs" with "information content. PWMs".

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Section "Benchmarking position weight matrix, support vector machine, and deep learning motif models' performance"  
  - **Evidence pointer** "STREME performed the worst when predicting SOX13 [95] (experiment ENCFF614IHQ) binding"  
  - **Issue** The experiment identifier ENCFF614IHQ is listed for SOX13, but the same identifier was previously used for the CTCF experiment in Figure 5a and b. This is either an error in the text or a duplicate identifier.  
  - **Required correction** Verify the correct experiment identifiers for CTCF and SOX13 and correct the text accordingly.

  - **Concern ID** R1-m4  
  - **Severity** Minor  
  - **Axis** Reproducibility  
  - **Affected element** Section "Model performance metrics"  
  - **Evidence pointer** "we evaluated model performance using precision..., recall..., and F1-score"  
  - **Issue** The manuscript states that AUPRC and AUROC were computed, but the threshold for determining positive/negative predictions for precision, recall, and F1-score is not specified. Different thresholds could lead to different conclusions.  
  - **Required correction** Specify the threshold used for computing precision, recall, and F1-score, or clarify whether these were computed at a fixed threshold or across thresholds.

  - **Concern ID** R1-m5  
  - **Severity** Minor  
  - **Axis** Presentation  
  - **Affected element** Section "Discussion"  
  - **Evidence pointer** "Table 2 discusses models' performance based on input dataset characteristics."  
  - **Issue** Table 2 is referenced but not visible in the provided material. The discussion would benefit from a summary of the key recommendations in the text itself.  
  - **Required correction** Provide a brief summary of the key recommendations from Table 2 in the text, so the main conclusions are accessible without consulting the table.

- **Technical failings that need to be addressed before the case is established**  
  R1-M1 (no visible quantitative results), R1-M2 (incomplete methodological description). These are the primary blockers. The other concerns, while important, can be addressed with additional analysis or clarification.

- **Assessment against Nature-style criteria**  
  - **Originality** Moderate. Benchmarking studies exist in this space, but the systematic comparison across PWM, SVM, and DL models with a focus on background data type and the needle-in-the-haystack scenario adds a useful dimension. The pretrained SVM database is a practical contribution.  
  - **Scientific importance** Moderate to high. TFBS prediction is a fundamental problem in regulatory genomics, and practical guidance on model selection is valuable. However, the importance depends on the robustness and generalizability of the findings, which cannot be assessed from the provided text.  
  - **Interdisciplinary readership** Moderate. The topic is of interest to computational biologists, bioinformaticians, and some experimental biologists. The writing is accessible but assumes familiarity with TFBS prediction methods.  
  - **Technical soundness** Cannot be fully assessed from the provided material. The study design is reasonable, but the lack of visible results and incomplete methodological details prevent evaluation of technical rigor.  
  - **Readability for nonspecialists** Acceptable. The manuscript is generally well-written and explains concepts clearly, though some sections assume background knowledge. The minor grammatical errors should be corrected.

- **Recommendation posture**  
  Currently not established from the provided evidence. The study addresses a relevant question with a thoughtful design, but the absence of visible quantitative results and incomplete methodological details prevent assessment of whether the claims are supported. The authors should provide the actual data, statistical analyses, and a complete description of the methods. If these are provided and the results are robust, the manuscript could be a valuable contribution. I am supportive of the overall direction but cannot endorse the manuscript in its current form.

## Risk / unsupported claims
- The claim that "SVM-based models generally outperform PWMs in most scenarios" is unsupported in the provided text, as no quantitative results are visible.
- The claim that "larger training datasets consistently improve performance" for SVM and NT models is unsupported without visible data.
- The claim that "LS-GKM may incorporate additional regulatory elements into its predictions" is speculative and unsupported by visible analysis.
- The claim that the database of 2393 SVM models "aims to facilitate broader adoption" is a reasonable goal but the utility and quality of the database cannot be assessed from the provided material.
- The statement that "homologous sequences represented <1% in nearly all experiments" is reported but the supporting analysis is in a supplementary file that was not provided.
- The overall performance comparisons and trends described in the results section are not verifiable from the provided text.