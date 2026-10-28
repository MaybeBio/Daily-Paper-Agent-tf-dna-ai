## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, acknowledgments)
- **Assessment boundary** Scientific content, methodological soundness, validity of claims, and presentation quality as presented in the provided text
- **Shared manuscript claim summary** The authors present a LASSO-regularized logistic regression framework to model gene-specific transcriptional repression and activation by the leukemogenic fusion protein AML1-ETO, using RNA-Seq and ChIP-Seq data from Kasumi-1 cells. They claim the model accurately predicts transcriptional outcomes, identifies rate-limiting factors (notably p300 and histone acetylation), and reveals coordinated chromatin interaction networks, including an unexpected role for E-proteins in AML1-ETO-p300 interactions.
- **Visible evidence base** RNA-Seq and ChIP-Seq data (described, not shown in full), model performance metrics (AUC, ACC, TNR, TPR), feature importance rankings, clustering and network analyses, and comparative algorithm evaluations
- **Missing materials affecting confidence** Figures and tables referenced (Figs. 1-8, Tables 1-2) are not provided; raw data, code, and detailed parameter settings are not available; validation details (e.g., cross-validation splits, hyperparameter tuning) are partially described but not fully reproducible

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely question in transcriptional regulation, applying a well-established machine learning method to a clinically relevant system. The conceptual framing, particularly the simultaneous modeling of activation and repression and the focus on rate-limiting factors, is commendable. However, the current evidence base is insufficient to fully evaluate the robustness of the claims. Key figures and tables are missing, several methodological details are ambiguous, and the causal interpretations drawn from correlational data require stronger experimental or analytical support. The manuscript has potential but needs substantial revision and additional validation before the conclusions can be considered established.
- **Who would be interested in the results, and why** Researchers in transcriptional regulation, chromatin biology, leukemia biology, and computational biology would find this work relevant. The methodological framework could interest those applying machine learning to genomic data, and the biological findings on AML1-ETO and E-proteins would appeal to the leukemia research community.
- **Major strengths** 1) The study addresses a gap in the field by modeling both repression and activation simultaneously rather than focusing on one outcome. 2) The use of LASSO-regularized logistic regression is appropriate for high-dimensional genomic data and provides interpretable feature selection. 3) The iterative modeling approach to identify rate-limiting factors is thoughtful and goes beyond simple classification. 4) The integration of multiple ChIP-Seq datasets and the focus on chromatin interactions is comprehensive. 5) The authors acknowledge limitations and propose future directions.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** The absence of all figures and tables, lack of code or data availability statements, insufficient detail on data preprocessing and feature construction, and the correlational nature of the causal claims are critical gaps.
- **Assessment against Nature-style criteria** 
  - **Originality** Moderate. The application of LASSO to this specific problem is not entirely novel, but the simultaneous modeling of activation and repression and the focus on rate-limiting factors provide some originality.
  - **Scientific importance** High. Understanding AML1-ETO-mediated transcriptional regulation has direct implications for leukemia biology and therapy.
  - **Interdisciplinary readership** Moderate. The work bridges computational and biological domains, but the presentation may be too specialized for a broad audience.
  - **Technical soundness** Currently not fully assessable due to missing figures, tables, and methodological details. The described approach is generally sound, but reproducibility is a concern.
  - **Readability for nonspecialists** The manuscript is dense and assumes significant background knowledge. The abstract is clear, but the methods and results sections would benefit from more accessible explanations.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising, but the manuscript requires major revisions, including the provision of all data and figures, clarification of methods, and tempering of causal claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims accurate prediction of transcriptional outcomes and identification of rate-limiting factors, supported by Figures 1-8 and Tables 1-2.
- **Evidence pointer** Figures 1-8, Tables 1-2 (not provided)
- **Concern** All figures and tables referenced in the text are absent from the provided material. Without these, the reader cannot evaluate the model performance, feature importance rankings, clustering results, or network analyses that form the basis of the central claims.
- **Why it matters** The conclusions rest entirely on these visual and tabular data. Their absence makes the manuscript impossible to assess for scientific validity and reproducibility.
- **Resolution test** Provide all figures and tables with clear legends, axis labels, and statistical annotations. Ensure they are referenced appropriately in the text.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological reproducibility
- **Claim pointer** The methods section describes the use of LASSO-regularized logistic regression, data preprocessing, and model evaluation, but lacks sufficient detail for replication.
- **Evidence pointer** Section "Machine learning", "Training algorithms used in this study"
- **Concern** Key methodological details are missing or ambiguous. Specifically, the exact feature set (97 columns) is not fully enumerated, the rationale for selecting the top two binding sites per gene is not justified, and the handling of class imbalance (232 activation vs. 247 repression sites) is not described. Additionally, the lambda selection procedure and the use of 500 independent runs are mentioned but not fully explained.
- **Why it matters** Reproducibility is a cornerstone of scientific research. Without complete methodological transparency, other researchers cannot replicate or build upon this work.
- **Resolution test** Provide a detailed description of all features, data preprocessing steps, model training and evaluation procedures, and hyperparameter selection. Consider making code and data publicly available.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The manuscript states that "LASSO correctly identified p300 as the rate-limiting factor of histone acetylation and revealed a role for E-proteins in p300 recruitment by AML1-ETO," implying causal relationships.
- **Evidence pointer** Section "Results", "p300, but not HDACs, is the rate-limiting enzyme regulating H3K18/K27 acetylation", "AML1-ETO binding results in coordinated changes of network modules"
- **Concern** The analyses are based on correlational ChIP-Seq data and model coefficients. While the authors interpret these as identifying rate-limiting factors, correlation does not establish causation. The claim that p300 is "rate-limiting" requires experimental validation (e.g., perturbation studies) that is not presented.
- **Why it matters** Overstating causal conclusions from observational data can mislead the field and lead to incorrect hypotheses being pursued.
- **Resolution test** Either provide experimental validation (e.g., p300 inhibition or knockdown) or temper the language to clearly state that these are predictive associations that require experimental confirmation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model evaluation and generalizability
- **Claim pointer** The model achieves high performance (AUC 93%, ACC 86%) on the test set, and the authors suggest the approach is generally applicable to other transcription factors.
- **Evidence pointer** Section "Overall performance", Section "Discussion", "Implications in other TFs"
- **Concern** The model is trained and tested on data from a single cell line (Kasumi-1) and a single transcription factor (AML1-ETO). The generalizability to other cell types, TFs, or conditions is asserted but not demonstrated. Additionally, the performance metrics are averaged over 500 runs, but the variance and potential overfitting are not discussed in detail.
- **Why it matters** Claims of general applicability require validation across diverse datasets. Without this, the utility of the approach beyond this specific context remains uncertain.
- **Resolution test** Validate the model on independent datasets (e.g., other AML cell lines, other TFs) or clearly state the limitations of the current scope and avoid overgeneralizing.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Section "Introduction"
- **Issue** The abstract and introduction are dense and use jargon without sufficient context for a general reader. For example, the term "rate-limiting factors" is used without a clear definition in the context of this study.
- **Required correction** Provide brief definitions or explanations of key terms and consider restructuring sentences for clarity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section
- **Evidence pointer** Section "Overall performance", Section "Acetyl-histones are among the most important features"
- **Issue** The manuscript reports p-values and significance levels but does not specify the statistical tests used for all comparisons (e.g., feature importance rankings). The multiple testing correction is mentioned but not detailed.
- **Required correction** Clearly state the statistical tests used for each comparison and describe the multiple testing correction method.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Methods section
- **Evidence pointer** Section "Materials and Methods"
- **Issue** No statement is provided regarding data and code availability, which is increasingly expected for computational studies.
- **Required correction** Add a data and code availability statement, or explicitly state why they are not available.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures (not provided)
- **Evidence pointer** Figures 1-8 (not provided)
- **Issue** Since figures are not provided, their quality and clarity cannot be assessed. However, based on the text, some figures may be overly complex (e.g., Fig. 6 and 7 showing clustering and networks).
- **Required correction** Ensure figures are self-explanatory with clear legends, and consider simplifying complex figures for readability.

## Risk / unsupported claims
- The claim that "LASSO correctly identified p300 as the rate-limiting factor" is unsupported without experimental validation; the analysis only shows statistical association.
- The claim that the approach is "generally applicable" to other TFs is unsupported by the data presented, which is limited to AML1-ETO in Kasumi-1 cells.
- The statement that "our results support a unified mechanism of transcriptional regulation by AML1-ETO" is a strong conclusion that requires more direct evidence than correlational modeling.
- The performance metrics (AUC, ACC) are reported without confidence intervals or measures of variance, making it difficult to assess robustness.
- The manuscript mentions "novel networks of chromatin interactions" but the novelty and biological significance are not fully contextualized against existing literature.