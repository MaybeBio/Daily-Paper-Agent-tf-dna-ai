## Review setup
- **Input scope** Full manuscript text including abstract, main text, figures, tables, and methods
- **Assessment boundary** Technical soundness, methodological rigor, claims versus evidence, and significance of the presented deep learning framework for HTLV-1 integration site prediction
- **Shared manuscript claim summary** The authors present DeepHTLV, described as the first deep learning framework for predicting HTLV-1 integration sites de novo from genome sequence, with capabilities for motif discovery and cis-regulatory factor identification. They report AUC values of 0.75, identification of eight consensus motif clusters, and 79 transcription factors associated with the learned motifs, 34 of which have literature support for involvement in HTLV-1 biology.
- **Visible evidence base** Main text, Figures 1-5, Table 1, methods section, supplemental figure descriptions, and data availability statements
- **Missing materials affecting confidence** Supplemental figures S1-S5 and Tables S1-S2 were referenced but not provided in the submitted material. The GitHub repository was not independently verified. No detailed hyperparameter search results or model architecture comparison tables were included in the visible text.

## Reviewer

- **Overall assessment** This manuscript describes a reasonable application of established deep learning techniques to a virological problem of interest. The work is competent but incremental, building directly on the authors' prior DeepVISP framework and applying similar methodology to HTLV-1. The central claims of novelty and biological insight are only partially supported by the evidence presented. The model performance is modest (AUC 0.75) and the biological interpretations, while plausible, rely heavily on literature correlation rather than direct experimental validation. The manuscript would benefit from clearer benchmarking against existing tools, more rigorous statistical evaluation, and tempering of some claims that exceed what the data can support.

- **Who would be interested in the results, and why** Researchers studying retroviral integration mechanisms, particularly those focused on HTLV-1 biology and pathogenesis, would find the computational approach of interest. The broader community developing deep learning methods for genomic sequence analysis may also find value in the methodological framework, though the technical novelty is limited. Clinicians and translational researchers working on HTLV-1-associated diseases such as ATL and HAM/TSP might find the identified transcription factor associations useful for generating hypotheses, though the work does not provide direct clinical utility.

- **Major strengths**
  1. The authors have assembled the largest curated dataset of HTLV-1 integration sites to date (33,845 sites), which represents a valuable community resource.
  2. The application of an attention mechanism to identify important sequence positions is a sensible approach for improving model interpretability.
  3. The bootstrapping strategy to address class imbalance is methodologically sound and well described.
  4. The work addresses a genuine need for computational tools to predict retroviral integration sites, given the limitations of experimental methods.
  5. The identification of specific transcription factors with literature support for HTLV-1 association provides some biological validation of the approach.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims DeepHTLV is "the first deep learning framework for VIS prediction de novo from genome sequence" for HTLV-1, and that it demonstrates "high accuracy" with "more efficient and interpretive feature representations."
- **Evidence pointer** Results section "DeepHTLV accuracy, robustness, and model interpretability"; Discussion section
- **Concern** The novelty claim is not adequately substantiated. The authors themselves cite DeepHINT for HIV-1 prediction and their own DeepVISP for DNA viruses. The methodological advance over these existing tools is not clearly articulated. More critically, the performance comparison is limited to traditional machine learning methods (LR, RF, DT, KNN), not against existing deep learning tools for viral integration prediction. The claim of "high accuracy" is difficult to evaluate without comparison to state-of-the-art methods. Additionally, the AUC of 0.75, while above chance, is modest and the authors do not report sensitivity, specificity, or precision-recall trade-offs at clinically relevant thresholds.
- **Why it matters** Without benchmarking against existing deep learning approaches and without more comprehensive performance metrics, the claimed advantages of DeepHTLV cannot be assessed. The novelty claim is central to the manuscript's contribution and requires stronger evidence.
- **Resolution test** The authors should benchmark DeepHTLV against DeepHINT and DeepVISP on comparable datasets, report additional metrics (sensitivity, specificity, F1 score, Matthews correlation coefficient), and provide statistical significance testing for performance differences. The novelty claim should be revised to accurately reflect the incremental nature of the contribution.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The manuscript claims that "DeepHTLV revealed interesting cis-regulatory elements in regulation of VISs that have significant association with the detected motifs" and that 34 of 79 predicted transcription factors were involved in HTLV-1-associated diseases.
- **Evidence pointer** Results section "Identifying cis-regulatory factors associated with HTLV-1 integration and associated diseases"; Figure 5; Table 1
- **Concern** The biological validation is entirely based on literature correlation. The authors do not provide any experimental validation of the predicted transcription factor binding or functional relevance. The statement that transcription factors are "involved in HTLV-1 integration" is an overstatement; the evidence only shows that some predicted TFs have been previously associated with HTLV-1 in other contexts. The direction of causality is unclear, and the analysis does not demonstrate that these TFs actually bind at the predicted sites or influence integration. Furthermore, the statistical significance of the TF-motif associations is not clearly described, and the multiple testing burden is not addressed.
- **Why it matters** The biological interpretation is a major claimed contribution of the work. Without experimental validation or at minimum stronger statistical evidence, the cis-regulatory findings remain speculative. Overstating the biological significance could mislead readers and future research directions.
- **Resolution test** The authors should either provide experimental validation (e.g., ChIP-seq, reporter assays, or CRISPR perturbation) for at least a subset of the key predictions, or substantially temper the claims to indicate that these are computational predictions requiring validation. Statistical details of the TF-motif matching should be provided, including multiple testing corrections.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The manuscript states that DeepHTLV is freely available at https://github.com/bsml320/DeepHTLV and that data are available in Table S2.
- **Evidence pointer** Data and code availability section; Methods section
- **Concern** The manuscript does not provide sufficient detail for reproduction. Key hyperparameters from the Hyperband optimization are not reported. The exact architecture dimensions (number of filters, kernel sizes, pooling sizes, dense layer sizes) are not specified. The threshold for maximum activation score is described only as "the maximum of the MASs per class," which is ambiguous. The GitHub repository was not accessible for verification during review. The training/validation/test split is described but the random seed and stratification approach are not specified.
- **Why it matters** Reproducibility is a core requirement for computational biology papers. Without complete methodological details, other researchers cannot build upon or verify this work. The claim of a freely available tool cannot be verified without repository access.
- **Resolution test** The authors should provide complete architecture specifications, all hyperparameters, the exact data splitting procedure, and ensure the GitHub repository is publicly accessible with clear documentation and a working example. The threshold definition should be clarified.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that "DeepHTLV outperformed other deep learning architectures and four traditional machine learning models, reaching AUC and AUPR values of 0.75 and 0.72."
- **Evidence pointer** Results section "DeepHTLV accuracy, robustness, and model interpretability"; Figure 3; Figure S2
- **Concern** The comparison with other deep learning architectures is only described in the supplemental material (Figure S2), which was not provided. The performance differences are described as "modest improvement of 3%–10%" over traditional methods, but no statistical significance testing is reported. The AUPR value of 0.72 is reported without context regarding the baseline prevalence of integration sites, which is critical for interpreting AUPR. The independent test set results are reported as a single AUC value without confidence intervals.
- **Why it matters** Without statistical rigor in performance comparisons, the claimed superiority of DeepHTLV cannot be established. The AUPR value is difficult to interpret without knowing the class distribution in the test set.
- **Resolution test** The authors should provide confidence intervals for all performance metrics, statistical tests for performance differences, and report the class distribution in the test set. The supplemental comparison with other architectures should be made available.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 2
- **Evidence pointer** Results section "Characterizing HTLV-1 viral integration throughout the genome and training DeepHTLV"
- **Issue** The chromosome distribution analysis (Figure 2A) shows raw counts, but the normalization by chromosome length (Figure 2B) is described in the text. The interpretation of "preferential integration" in chromosome 1-4 is not supported by statistical testing. The authors state "preferentially integrated in the first four chromosomes" but the normalized distribution appears nearly uniform except for chromosome Y.
- **Required correction** Provide statistical tests for non-uniform distribution and clarify whether the apparent preference for chromosomes 1-4 is significant after normalization.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Motif analysis and cis-regulatory factors identification"
- **Evidence pointer** Methods section
- **Issue** The description of the motif score calculation is incomplete. The authors state it is "the difference between the mean maximum activation for positive class and negative class" but do not describe how this is normalized or how significance is assessed.
- **Required correction** Provide a complete formula for the motif score and describe how statistical significance of motif enrichment is evaluated.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The comparison with DeepHINT is mentioned but not discussed in detail. The authors note DeepHINT achieved AUCs between 0.736 and 0.904, which overlaps with or exceeds DeepHTLV's performance. This comparison is not adequately addressed.
- **Required correction** Discuss the relative performance of DeepHTLV and DeepHINT more thoroughly, including differences in datasets, methodology, and potential reasons for performance differences.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 3E-3I
- **Evidence pointer** Results section "DeepHTLV accuracy, robustness, and model interpretability"
- **Issue** The UMAP visualizations are described as showing "clear separation" in the final layers, but this is a qualitative assessment. No quantitative metric of cluster separation is provided.
- **Required correction** Provide quantitative measures of cluster separation (e.g., silhouette score, adjusted Rand index) to support the qualitative claim.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Table 1
- **Evidence pointer** Results section "Identifying cis-regulatory factors associated with HTLV-1 integration and associated diseases"
- **Issue** The table lists transcription factors with literature support but does not provide the specific evidence or citations for each TF. The criteria for "literature evidence" are not defined.
- **Required correction** Provide a supplementary table with specific citations and a brief description of the evidence for each TF.

## Risk / unsupported claims
- The claim of being "the first deep learning framework" for HTLV-1 VIS prediction is not fully substantiated, as the authors do not provide a comprehensive literature search demonstrating the absence of prior work.
- The claim that 34 TFs are "involved in HTLV-1 integration" overstates the evidence, which only shows literature associations with HTLV-1 or its diseases, not direct involvement in integration.
- The biological significance of the identified motifs and TFs is presented as established rather than as hypotheses requiring validation.
- The performance comparison claims are not statistically substantiated.
- The claim of "more efficient and interpretive feature representations" is not quantified or compared against alternatives.
- The generalizability of the model to other retroviruses or other genomic contexts is implied but not tested.