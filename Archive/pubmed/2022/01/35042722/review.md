## Review setup
- **Input scope** Full manuscript text (abstract, results, discussion, methods) without figures, tables, or supplementary material
- **Assessment boundary** Scientific claims, methodology, and interpretation as presented in the text; figure/table contents not directly assessable
- **Shared manuscript claim summary** The authors train conventional and domain-adaptive neural networks to predict transcription factor binding from DNA sequence, demonstrate a cross-species performance gap between mouse and human, attribute a substantial portion of this gap to primate-specific Alu elements causing false positives in mouse-trained models, and show that a gradient reversal layer (GRL) domain adaptation approach partially corrects this overprediction.
- **Visible evidence base** Text descriptions of Figures 1–12, Tables 1, Supplemental Figures S1–S8, Supplemental Tables S1–S7; no actual data values, plots, or tables visible
- **Missing materials affecting confidence** All figures, tables, and supplementary data; exact performance metrics (auPRC values, confidence intervals); hyperparameter search details; code implementation specifics; data accession validation

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely problem in regulatory genomics: whether cross-species prediction of transcription factor binding is feasible and what systematic biases limit it. The authors identify a clear and mechanistically interpretable source of cross-species prediction error (primate-specific Alu elements) and demonstrate that a relatively simple domain adaptation technique partially mitigates this issue. The work is well-motivated, the experimental design is thoughtful, and the conclusions are appropriately cautious. However, the magnitude of the reported improvements is modest, and several technical details regarding the domain adaptation implementation and evaluation metrics require clarification. The claim that domain adaptation "improves" cross-species prediction is supported, but the practical significance of the improvement is not fully contextualized. The manuscript would be strengthened by a more quantitative treatment of the improvement relative to the total performance gap and by additional analysis of when the approach fails.

- **Who would be interested in the results, and why** Computational biologists developing predictive models for regulatory genomics; experimental biologists studying cross-species conservation of transcription factor binding; researchers working on domain adaptation and transfer learning in genomics; those interested in the regulatory role of transposable elements. The work has direct implications for efforts to impute regulatory information from model organisms to humans or non-model species.

- **Major strengths** 
  1. The problem is well-formulated and practically important; cross-species regulatory prediction has clear translational value.
  2. The identification of Alu elements as a dominant source of cross-species false positives is a concrete, mechanistically grounded finding with clear biological interpretation.
  3. The domain adaptation approach is simple, principled, and directly addresses the identified problem.
  4. The authors include multiple control analyses (gapped k-mer SVMs, BPNet-like profile models) that contextualize their main results.
  5. The expanded analysis across 53 additional datasets demonstrates generalizability beyond the initial liver-focused experiments.
  6. The writing is clear and accessible, with appropriate caveats about the limitations of the approach.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Domain-adaptive mouse models can improve cross-species performance" and "the auPRC for our domain-adaptive models on cross-species test data is moderately higher than the auPRC for the basic mouse models for all TFs except CTCF"
- **Evidence pointer** Figure 9, described in text; location not provided
- **Concern** The reported improvement in cross-species auPRC is described as "moderate" but no quantitative values are provided in the text. The magnitude of the improvement relative to the total cross-species performance gap is not stated. Without these numbers, it is impossible to assess whether the improvement is practically meaningful or merely statistically detectable. Additionally, the authors do not report confidence intervals or significance tests for the auPRC differences across the five replicate models.
- **Why it matters** The central claim of the paper is that domain adaptation improves cross-species prediction. The strength of this claim depends entirely on the magnitude and reliability of the improvement. If the improvement is small relative to the gap, the practical utility of the approach is questionable. If the improvement is not statistically robust across replicates, the conclusion is not supported.
- **Resolution test** Report the mean and standard deviation (or confidence interval) of auPRC across the five replicates for basic and domain-adaptive models for each TF and species direction. State the improvement as a percentage of the total cross-species gap. Provide a statistical test (e.g., paired Wilcoxon or bootstrap) comparing basic and domain-adaptive models across replicates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We modified our existing model architecture to perform training-integrated domain adaptation across species" and "the GRL merely computes the identity of its input, but as the loss gradient backpropagates through the GRL, it is reversed"
- **Evidence pointer** Figure 8, described in text; location not provided
- **Concern** The description of the domain adaptation architecture is underspecified. The GRL is added "in parallel with the LSTM, taking in the result of the max-pooling step." It is unclear how the species discrimination task interacts with the binding prediction task during training. Specifically: (1) Are the two tasks trained jointly with a weighted combined loss? If so, what is the weighting? (2) How is the GRL's gradient reversal applied in the multi-task setting? (3) The text states that "the binding task only trains on examples from the source species" but the species discriminator sees both species. How does the model avoid learning species-specific features in the shared convolutional layers while still performing binding prediction? (4) The masking procedure for the two output heads is described but the implementation details are not provided.
- **Why it matters** The domain adaptation mechanism is the key methodological contribution. Without a precise description of the architecture, training procedure, and loss weighting, the work cannot be reproduced or extended. The claimed effect of the GRL depends critically on these details.
- **Resolution test** Provide a complete description of the multi-task training procedure, including the loss function, weighting scheme, and how the GRL is applied in the backward pass. Include a diagram or pseudocode. State whether the species discriminator is trained on the same batches as the binding task or on separate batches.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "On average, 89% of these false positives unique to the mouse model overlap with an Alu element, compared with the average overlap rate of 21% for unbound sites overall, or 18% for unbound sites incorrectly predicted by both models."
- **Evidence pointer** Table 1, described in text; location not provided
- **Concern** The authors state that they "focus analyses here only on highly mappable Alu instances" but do not provide details on how mappability filtering was applied to the Alu overlap analysis. The Methods section describes mappability filtering for the genome windows used in training, but it is unclear whether the same filtering was applied to the Alu annotation track. If Alu elements are generally poorly mappable, the filtering criteria could substantially affect the reported overlap percentages. Additionally, the authors do not report the total number of Alu-overlapping windows in each category, only percentages.
- **Why it matters** The Alu enrichment finding is the central biological insight of the paper. If the mappability filtering is not consistently applied or if the denominator (total number of false positives) is small, the reported enrichment could be misleading. The reader needs to know the absolute counts to assess the robustness of the finding.
- **Resolution test** Report the number of windows in each category (e.g., false positives unique to mouse model, unbound sites overall) and the number of Alu-overlapping windows in each. Describe the mappability filtering applied to the Alu annotation and confirm that the same criteria were used for all analyses.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "Our results show that cross-species TF binding prediction is feasible when models account for domain shifts driven by species-specific repeats."
- **Evidence pointer** Figures 9–12, described in text; location not provided
- **Concern** The authors demonstrate that domain adaptation reduces Alu-related false positives, but they do not show that the approach improves prediction of true binding sites. The text states that "the site-distribution plots for bound sites show no noticeable difference from the original plots for the basic model architecture," indicating that the domain adaptation does not help with false negatives. The overall auPRC improvement is attributed to reducing false positives, but the authors do not report whether the precision-recall tradeoff is favorable. If the domain adaptation reduces false positives at the cost of increasing false negatives, the net benefit is unclear.
- **Why it matters** The practical value of cross-species prediction depends on both sensitivity and specificity. If the approach only reduces false positives without improving true positive detection, its utility for genome annotation is limited. The authors should clarify whether the auPRC improvement reflects a genuine improvement in ranking or merely a shift in the precision-recall operating point.
- **Resolution test** Report precision-recall curves for basic and domain-adaptive models, or report recall at fixed precision thresholds. State whether the domain adaptation changes the ranking of true binding sites or only the calibration of scores.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interdisciplinary readership
- **Claim pointer** "We observed that this strategy outperformed backpropagation-based scoring methods, potentially by avoiding gradient instability"
- **Evidence pointer** Methods, Importance scoring; location not provided
- **Concern** The importance scoring method is described as "similar to in silico mutagenesis (ISM)" but the implementation differs from standard ISM in that it uses dinucleotide-shuffled reference sequences rather than a single reference. The authors state that this "outperformed backpropagation-based scoring methods" but do not provide a comparison or justification for this claim. No data are shown to support the superiority of this approach.
- **Why it matters** The importance scores are used to draw conclusions about model behavior (e.g., "pseudomotifs" in false positives). If the scoring method is not validated, the interpretation of the importance score patterns is uncertain. The claim of superiority over backpropagation methods is unsupported.
- **Resolution test** Provide a comparison of the proposed importance scoring method with at least one backpropagation-based method (e.g., saliency maps, integrated gradients) on a validation set. Alternatively, remove the claim of superiority and describe the method as one of several possible approaches.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states that "domain-adaptive neural networks improve cross-species prediction" but does not define what "domain adaptation" means in this context. A reader unfamiliar with transfer learning may not understand the distinction between a conventional model and a domain-adaptive model.
- **Required correction** Add a brief parenthetical explanation, e.g., "a training strategy that discourages the model from learning species-specific features."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Model training
- **Evidence pointer** Methods; location not provided
- **Issue** The text states that "the epochs in which models had highest source-species auPRCs were often epochs in which models had near-best cross-species auPRC" but does not specify how often "often" is, nor whether this pattern held for all TFs and both species directions.
- **Required correction** Provide a quantitative summary, e.g., "in 7 of 8 model configurations, the epoch with highest source-species auPRC was within the top 3 epochs for cross-species auPRC."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion; location not provided
- **Issue** The discussion mentions that "Alus and other transposable elements can serve as true regulatory elements," but the authors do not discuss the implications of this for their analysis. If some Alu elements are truly bound by TFs, then the "false positives" attributed to Alu overprediction may include some true binding events.
- **Required correction** Add a brief discussion of how the analysis distinguishes between Alu elements that are truly bound and those that are spuriously predicted, or acknowledge this as a limitation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Data processing
- **Evidence pointer** Methods; location not provided
- **Issue** The Methods state that "candidate data sets were discarded from the analysis if the numbers of called peaks was less than 1000 in mouse or human." This threshold is not justified, and it is unclear how many datasets were discarded.
- **Required correction** Provide a justification for the threshold and report the number of datasets excluded.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results, Section 2
- **Evidence pointer** Results, "The mouse-to-human cross-species gap originates from misprediction of both bound and unbound sites"; location not provided
- **Issue** The term "site-distribution plots" is used without a clear explanation of what is being plotted. The reader must infer the plot structure from the text.
- **Required correction** Briefly describe the plot axes and what each point represents, or refer to a figure legend that provides this information.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, Importance scoring
- **Evidence pointer** Methods; location not provided
- **Issue** The importance scoring method uses 10 dinucleotide-shuffled reference sequences, but the text does not specify how the 5-bp replacement region is chosen or whether the results are averaged over the 10 references.
- **Required correction** Clarify whether the reported score is the average over the 10 shuffled references and describe the replacement procedure precisely.

## Risk / unsupported claims
- The claim that the importance scoring method "outperformed backpropagation-based scoring methods" is unsupported by any data shown in the text.
- The statement that "domain-adaptive models’ auPRCs on mouse test data, meanwhile, are comparable to the auPRCs of basic models" is vague; "comparable" is not quantified.
- The claim that "the domain-adaptive models still do not achieve a level of performance comparable to same-species models" is presented without quantitative context, making it difficult to assess the practical significance.
- The assertion that "the false-positive predictions that do overlap Alus are also generally less likely to be corrected by our domain adaptation approach in these cell types" (megakaryocyte and hematopoietic progenitor) is based on Figure 12, which is not visible; the magnitude of this effect is not described.
- The statement that "the underlying assumption of cross-species TF binding prediction, that is, that the overall features of cell-specific TF binding sites are conserved, may not hold true in all cases" is presented as a caveat but is not systematically evaluated in the manuscript.

## Assessment against Nature-style criteria
- **Originality** The application of domain adaptation via GRL to cross-species TF binding prediction is novel in this specific context, though the technique itself is established in the machine learning literature. The identification of Alu elements as a dominant source of cross-species prediction error is a new and mechanistically informative finding.
- **Scientific importance** The problem of cross-species regulatory prediction is of broad interest to the genomics community. The finding that species-specific repeats are a major confounder has practical implications for any cross-species prediction effort. However, the modest improvement from domain adaptation limits the immediate impact.
- **Interdisciplinary readership** The work bridges machine learning and regulatory genomics, and the writing is generally accessible to both communities. The biological interpretation of the Alu finding is clear. However, the technical details of the domain adaptation implementation may be opaque to experimental biologists.
- **Technical soundness** The experimental design is generally sound, with appropriate controls (gapped k-mer SVMs, profile models) and multiple replicates. However, the lack of quantitative performance metrics in the text, the underspecified domain adaptation architecture, and the unclear mappability filtering for the Alu analysis are significant gaps that must be addressed.
- **Readability for nonspecialists** The manuscript is well-written and the narrative is easy to follow. The key findings are clearly stated. However, some technical terms (e.g., "gradient reversal layer," "domain adaptation") are used without sufficient explanation for a general audience.

## Recommendation posture
Supportive if technical concerns are resolved. The core finding that Alu elements drive cross-species false positives is interesting and likely correct, and the domain adaptation approach is a reasonable first step toward addressing this problem. However, the manuscript currently lacks the quantitative detail needed to assess the magnitude and robustness of the reported improvement. The authors must provide specific performance numbers, clarify the domain adaptation implementation, and address the mappability filtering issue before the claims can be fully evaluated.