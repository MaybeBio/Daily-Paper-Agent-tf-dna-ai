## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) as provided by the user.
- **Assessment boundary** The review is limited to the content of the provided manuscript text. No external data, code, or supplementary materials were available for verification.
- **Shared manuscript claim summary** The authors propose iEnhancer-EBLSTM, a two-layer deep learning framework using ensembles of bidirectional long short-term memory (LSTM) networks with 3-mer sequence encoding, to identify enhancers and classify their strength (strong vs. weak) from DNA sequence alone. They report performance improvements over existing methods on a benchmark dataset.
- **Visible evidence base** The manuscript includes descriptions of the benchmark dataset, encoding scheme, model architecture, ensemble strategy, and performance comparisons (reported in Tables 1-10, not all values shown in the provided text). Figures 1-5 are referenced but not visible.
- **Missing materials affecting confidence** The actual performance values in Tables 1-10 are not provided in the text. Figures 1-5 are not available. No code, hyperparameters, training details, or statistical significance tests are provided. The dataset is described but not accessible for independent verification.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in regulatory genomics, namely enhancer identification and strength classification, using a modern deep learning approach. The core idea of applying bidirectional LSTM with 3-mer encoding is reasonable and the authors demonstrate systematic comparisons of encoding schemes, architectures, and ensemble methods. However, the manuscript has significant technical and presentational weaknesses. The results are reported without numerical values in the provided text, making the claimed improvements impossible to verify. The methodological description lacks critical details on hyperparameters, training procedures, and model selection. The comparison with state-of-the-art methods is incomplete and the discussion of biological implications is superficial. The writing contains informal language and unclear statements. The case for novelty and scientific impact is not convincingly established from the provided evidence.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on regulatory element prediction, particularly those interested in deep learning applications to genomics. The method could be of interest to researchers developing tools for functional annotation of non-coding regions. However, the interest would be contingent on the method demonstrating clear and reproducible performance gains over existing tools.
- **Major strengths**
  - The problem is well-motivated and of practical importance in genomics.
  - The use of bidirectional LSTM is a sensible choice for sequence data, and the systematic comparison of encoding schemes and architectures is a positive aspect.
  - The two-layer framework for identification and classification is a logical design.
  - The authors compare their method against several established tools.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality and reproducibility
  - **Claim pointer** The authors claim that iEnhancer-EBLSTM demonstrates efficiency and improved performance over existing methods (Abstract, Results, Discussion).
  - **Evidence pointer** Tables 1-10, Figures 1-5 (location not provided in the text)
  - **Concern** The manuscript does not provide the actual numerical results for any of the reported experiments. Tables 1-10 are referenced but their contents are not included in the provided text. Without these values, the central claims of improved performance (e.g., ACC, SN, SP, MCC, AUC) cannot be assessed. The figures are also not available. This is a fundamental issue that prevents any evaluation of the method's effectiveness.
  - **Why it matters** The core contribution of the paper is a new predictive model. The evidence for its utility rests entirely on quantitative comparisons. Without the data, the claims are unverifiable and the scientific case is not established.
  - **Resolution test** The authors must provide the full content of all tables and figures, including all performance metrics for all compared methods, in the revised manuscript.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness and reproducibility
  - **Claim pointer** The authors describe the model architecture and training process (Materials and Methods, Sections "BLSTM Architecture" and "Ensemble Model").
  - **Evidence pointer** Section "BLSTM Architecture", Section "Ensemble Model" (location not provided)
  - **Concern** The methodological description is insufficient for replication. Key details are missing, including: the number of LSTM units, the number of layers in the final model, the embedding dimension, the optimizer, learning rate, batch size, number of epochs, early stopping criteria, and the specific implementation of the ensemble (e.g., how many base learners, how they are trained on subsamples). The description of the "relu" layer is ambiguous, as ReLU is typically an activation function, not a layer. The threshold of 0.5 is mentioned but the rationale is not given.
  - **Why it matters** Reproducibility is a cornerstone of scientific method. Without these details, other researchers cannot build upon or validate the proposed approach, limiting its utility and impact.
  - **Resolution test** The authors must provide a complete and precise description of the model architecture and training procedure, including all hyperparameters, in the methods section or as supplementary material.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Comparison fairness and rigor
  - **Claim pointer** The authors state that iEnhancer-EBLSTM performs best in enhancer identification and classification compared to existing methods (Results, Section "Comparison With Existing State-of-the-Art Methods").
  - **Evidence pointer** Tables 9, 10 (location not provided)
  - **Concern** The comparison with existing methods is described qualitatively. It is unclear if the same training and test splits were used for all methods, if hyperparameters for the competing methods were optimized, or if the comparisons are statistically significant. The text mentions that iEnhancer-EBLSTM has lower AUC than iEnhancer-ECNN in some cases but higher SN, without a clear discussion of the trade-offs.
  - **Why it matters** A fair and rigorous comparison is essential to support the claim of superiority. Without controlling for these factors, the reported improvements could be due to artifacts of the experimental setup rather than the method itself.
  - **Resolution test** The authors should clarify the experimental protocol for all compared methods, including whether they were retrained and tuned, and provide statistical significance tests (e.g., confidence intervals or p-values) for the performance differences.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific context and interpretation
  - **Claim pointer** The authors state that the differences in DNA sequence can be used to distinguish enhancers, non-enhancers, strong enhancers, and weak enhancers (Materials and Methods, Section "Benchmark Dataset").
  - **Evidence pointer** Figure 2 (location not provided)
  - **Concern** The biological interpretation of the results is superficial. The authors do not discuss what sequence features or motifs the model might be learning, nor do they relate their findings to known enhancer biology. The claim that sequence differences can distinguish these classes is supported only by a reference to a figure that is not available.
  - **Why it matters** For a Nature-style audience, the biological insight derived from a predictive model is as important as the predictive performance. The current manuscript does not provide any such insight, limiting its broader scientific impact.
  - **Resolution test** The authors should include an analysis of the learned features or sequence motifs, and discuss the biological implications of their findings in the context of enhancer regulation.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and presentation
  - **Affected element** Abstract and Introduction
  - **Evidence pointer** Abstract, Introduction (location not provided)
  - **Issue** The writing contains informal and imprecise language. For example, "In our view, it has great improvements in many metrics" is subjective. The abstract states "the experimental results from the datasets demonstrate the efficiency of our proposed model" without specifying which datasets or metrics.
  - **Required correction** Rewrite these sections to be more formal and specific, clearly stating the datasets used and the key quantitative results.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical accuracy
  - **Affected element** Materials and Methods, Section "BLSTM Architecture"
  - **Evidence pointer** Section "BLSTM Architecture" (location not provided)
  - **Issue** The text mentions "the rectified linear unit (relu)" as a layer. ReLU is an activation function, not a layer. This is technically incorrect.
  - **Required correction** Correct the description to specify that ReLU is used as an activation function within the network, and clarify where it is applied.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Results, Section "Comparison of Different Architectures"
  - **Evidence pointer** Tables 5, 6 (location not provided)
  - **Issue** The text states that "the results of these four experiments were added to the table" but does not discuss them. It is unclear if the two-layer architectures performed worse or better and why.
  - **Required correction** Provide a brief discussion of the results for all architectures tested, including the two-layer variants, to justify the final model choice.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Data availability
  - **Affected element** Data Availability Statement
  - **Evidence pointer** Data Availability Statement (location not provided)
  - **Issue** The statement says "further inquiries can be directed to the corresponding author/s." This is vague and does not meet modern standards for data and code availability.
  - **Required correction** Provide a clear statement on where the data and code can be accessed, or explicitly state that they are available upon request with a clear process for doing so.

## Risk / unsupported claims
- The central claim of improved performance over existing methods is unsupported because the numerical results in Tables 1-10 are not provided in the manuscript text.
- The claim that "differences in DNA sequence can be used to distinguish these four types of sequences" is not verifiable without Figure 2.
- The claim that the ensemble method (averaging) is superior is not verifiable without the data in Tables 7 and 8.
- The claim that the model is efficient is not supported by any runtime or complexity analysis.
- The biological relevance of the findings is not discussed, making any claim of biological insight unsupported.

## Assessment against Nature-style criteria
- **Originality** The application of bidirectional LSTM to enhancer prediction is not entirely novel, as similar architectures have been used in other genomic sequence classification tasks. The specific combination of 3-mer encoding with an ensemble of bidirectional LSTMs may offer incremental novelty, but this is not clearly articulated. The manuscript does not present a new biological insight or a fundamentally new computational paradigm.
- **Scientific importance** The problem of enhancer identification is important, but the manuscript does not demonstrate a significant advance over existing tools. The lack of quantitative results prevents an assessment of whether the method offers a meaningful improvement. The potential impact on the field is therefore unclear.
- **Interdisciplinary readership** The topic is of interest to computational biologists and bioinformaticians. However, the manuscript is written in a way that assumes familiarity with deep learning terminology without providing sufficient context for a broader biological audience. The lack of biological interpretation limits its appeal to a wider readership.
- **Technical soundness** The technical soundness cannot be fully assessed due to missing details on model architecture, training, and results. The description of the ensemble method and the comparison with other methods is incomplete. The use of ReLU as a "layer" suggests a lack of precision in the technical writing.
- **Readability for nonspecialists** The manuscript is not easily accessible to nonspecialists. The introduction provides some background, but the methods and results sections are dense and lack clear explanations of the key concepts. The absence of quantitative results makes it difficult for any reader to understand the significance of the work.

## Recommendation posture
Currently not established from the provided evidence. The manuscript addresses a relevant problem and the methodological approach is plausible, but the absence of the actual results (tables and figures) and critical technical details prevents any meaningful evaluation of the claims. The authors must provide the full experimental data and a complete methodological description before the case for this method can be assessed. If these are provided and the results are robust, the manuscript could be considered for publication in a specialized journal, but it would require substantial revisions to meet the standards of a high-impact general journal.