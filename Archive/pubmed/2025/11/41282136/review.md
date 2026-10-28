## Review setup
- **Input scope** Full manuscript text (preprint, Research Square, DOI: 10.21203/rs.3.rs-7681940/v1)
- **Assessment boundary** Scientific content, methodology, claims, and evidence as presented in the provided text. No external data or code were accessed.
- **Shared manuscript claim summary** The authors present Shorkie, a masked DNA language model pretrained on 165 fungal genomes and fine-tuned on yeast RNA-seq, ChIP-exo, and ChIP-MNase data. They claim substantial improvements over non-pretrained baselines in predicting gene expression, dynamic TF-induction responses, and variant effects, with interpretability analyses revealing regulatory motif usage.
- **Visible evidence base** Main text figures (Figures 1–7, referenced), supplementary figures (S1–S25, referenced), and methods sections. No actual figure images, numerical results, or code were provided in the input.
- **Missing materials affecting confidence** Figure contents, quantitative performance metrics, model weights, code, and full supplementary tables are not available. This limits verification of all claims.

## Reviewer
- **Overall assessment** This manuscript presents a timely and potentially impactful application of self-supervised DNA language models to a compact, well-characterized genome. The core idea—that evolutionary-scale pretraining on related fungal genomes can overcome the limited training data of S. cerevisiae—is well motivated and the results, as described, are promising. However, the current text does not provide sufficient quantitative detail to fully assess the magnitude of the claimed improvements, the robustness of the benchmarking, or the biological novelty of the interpretability findings. The manuscript would benefit from clearer presentation of performance metrics, more rigorous baselines, and a more critical discussion of limitations.
- **Who would be interested in the results, and why** Computational biologists working on regulatory genomics, particularly those developing sequence-to-expression models; researchers using language models for non-coding variant interpretation; and yeast biologists interested in cis-regulatory code and dynamic transcriptional responses. The work bridges a gap between large-genome deep learning applications and the tractable, well-annotated yeast system.
- **Major strengths**
  1. The central hypothesis—that pretraining on a phylogenetically appropriate set of genomes improves downstream prediction in a data-limited species—is well articulated and addresses a key limitation in the field.
  2. The generation of a large new RNA-seq dataset (3,053 timepoints from TF induction experiments) is a significant experimental contribution.
  3. The evaluation across multiple tasks (expression prediction, variant effects, eQTL classification, MPRA concordance) is comprehensive in scope.
  4. The interpretability analyses (ISM, attention maps) are appropriate for probing what the model has learned.
- **Major Concerns**
  - **R1-M1** (Blocking: Yes)
  - **R1-M2** (Blocking: Yes)
  - **R1-M3** (Blocking: No)
  - **R1-M4** (Blocking: No)
- **Minor Comments**
  - **R1-m1**
  - **R1-m2**
  - **R1-m3**
  - **R1-m4**
  - **R1-m5**
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking. The manuscript cannot be fully evaluated without quantitative results and a more rigorous comparison to existing methods.
- **Assessment against Nature-style criteria**
  - **Originality** High. The application of cross-species pretraining to yeast regulatory genomics is a novel and well-reasoned approach.
  - **Scientific importance** Potentially high. If the claims hold, this could establish a general paradigm for applying language models to genetically tractable but data-limited organisms.
  - **Interdisciplinary readership** Moderate. The work will appeal to computational and yeast biologists, but the presentation is currently too technical and lacks sufficient biological insight for a broad audience.
  - **Technical soundness** Currently not fully assessable. The methods are described in detail, but the absence of quantitative results prevents verification of the central claims.
  - **Readability for nonspecialists** The abstract and introduction are clear, but the results section is dense and assumes significant familiarity with deep learning and genomics terminology.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is strong and the experimental effort is substantial, but the manuscript in its current form does not provide enough evidence to fully establish the claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** "Shorkie achieved superior ROC and PR metrics for both Caudal et al. and Kita et al. datasets" and "Shorkie achieved median bin-level Pearson's R of 0.78 versus 0.67 for Shorkie_Random_Init"
- **Evidence pointer** Results section, Figures 3C–G, 7E–H; location not provided
- **Concern** The manuscript makes strong quantitative claims about performance improvements but does not present any of the actual numbers, error bars, or statistical significance tests in the text. The figures are referenced but their contents are not visible in the provided material. Without these data, it is impossible to assess whether the improvements are meaningful, consistent across folds, or statistically robust.
- **Why it matters** The central claim of the paper is that pretraining improves prediction. This claim rests entirely on the quantitative comparison between Shorkie and Shorkie_Random_Init. If the performance gains are marginal or inconsistent, the main conclusion is weakened.
- **Resolution test** Provide the actual performance metrics (e.g., mean and standard deviation of Pearson's R across cross-validation folds) for all models and tasks, along with appropriate statistical tests (e.g., paired t-test or Wilcoxon signed-rank test) comparing Shorkie to baselines.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Benchmarking rigor
- **Claim pointer** "Shorkie accurately predicted variant effects, outperforming leading sequence-to-expression models in cis-eQTL classification"
- **Evidence pointer** Results section, Figure 7; location not provided
- **Concern** The comparison to "leading sequence-to-expression models" is mentioned but the specific models, their training procedures, and hyperparameters are not described. It is unclear whether these baselines were trained on the same data, with the same cross-validation splits, and with comparable compute. Without a clear description of the baseline setup, the claim of "outperforming" cannot be evaluated.
- **Why it matters** A fair comparison is essential to demonstrate that the improvement is due to pretraining and not to other factors such as model architecture, training data, or evaluation protocol.
- **Resolution test** Clearly describe all baseline models, their training data, hyperparameters, and evaluation protocols. Ensure that all models are trained and evaluated under identical conditions, and report these details in the Methods.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological insight
- **Claim pointer** "Shorkie captures dynamic cis-regulatory motif changes across time-course TF inductions"
- **Evidence pointer** Results section, Figure 5; location not provided
- **Concern** The interpretability analyses show that the model can track motif usage over time, which is interesting. However, the biological novelty is unclear. Do these dynamic changes provide new insights into regulatory mechanisms, or do they simply recapitulate known biology? The manuscript does not discuss whether any novel regulatory relationships were discovered.
- **Why it matters** For a Nature-style audience, demonstrating new biological insight is crucial. Simply showing that a model can recover known motifs is a technical validation, not a scientific discovery.
- **Resolution test** Discuss whether any of the dynamic motif changes are novel or unexpected, and validate these predictions with independent experiments or literature evidence.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** "evolutionary-scale pretraining combined with transfer learning substantially improves our ability to decode gene regulation from sequence"
- **Evidence pointer** Discussion section; location not provided
- **Concern** The manuscript focuses exclusively on S. cerevisiae. It is unclear whether the conclusions generalize to other fungal species or to more complex eukaryotes. The authors speculate about this in the discussion, but no data are presented to support these claims.
- **Why it matters** The broader impact of the work depends on its generalizability. If the approach only works for yeast, its significance is limited.
- **Resolution test** Either provide preliminary results on a second species or temper the claims in the discussion to clearly state that generalizability remains to be tested.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, "Shorkie identified canonical transcription factor (TF) binding motifs and tracked their usage across induction experiments"
- **Issue** The abstract states that Shorkie "identified" motifs, but the methods describe using TF-MoDISco-Lite on model predictions. It would be clearer to state that the model's predictions were used to identify motifs, not that the model itself performs motif discovery.
- **Required correction** Rephrase to "Analysis of Shorkie's predictions identified canonical TF binding motifs..."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Methods, "Shorkie LM training"
- **Issue** The training procedure is described in detail, but the total number of training steps, the learning rate schedule, and the compute resources used are not specified. This information is important for reproducibility.
- **Required correction** Add the total number of training steps, the learning rate schedule, and the hardware used for training.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results
- **Evidence pointer** Results, "Shorkie exceeded Shorkie_Random_Init in 87.8% of genes"
- **Issue** The percentage of genes where Shorkie outperforms the baseline is reported, but no confidence interval or statistical test is provided. It is unclear if this proportion is significantly different from 50%.
- **Required correction** Provide a confidence interval or a binomial test for the proportion of genes where Shorkie outperforms the baseline.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and Code Availability
- **Evidence pointer** Data and Code Availability section
- **Issue** The section is empty in the provided text. It is unclear whether the data and code will be made available, which is critical for reproducibility.
- **Required correction** Complete the Data and Code Availability section with clear statements about what will be deposited and where.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 1
- **Evidence pointer** Results, "Figure 1A"
- **Issue** The description of Figure 1A mentions "the same training data as the Species-aware LM developed by Karollus et al." but does not explain what this means for the reader. A brief explanation of the relationship to prior work would be helpful.
- **Required correction** Add a sentence explaining the relationship between the training data used here and that of Karollus et al.

## Risk / unsupported claims
- The claim of "substantial improvements" in expression prediction is unsupported without quantitative metrics.
- The claim of "outperforming leading sequence-to-expression models" is unsupported without a description of the baselines.
- The claim that the model "captures dynamic cis-regulatory motif changes" is supported only by qualitative descriptions of figures, not by quantitative analysis.
- The generalizability claims in the discussion are speculative and not supported by data.
- The biological novelty of the interpretability findings is not established.