## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, discussion, declarations)
- **Assessment boundary** Scientific claims, methodology, evidence quality, and internal consistency as presented in the provided text
- **Shared manuscript claim summary** The authors use transfer learning with a convolutional neural network (ChromBPNet) to predict quantitative chromatin accessibility responses to TWIST1 and SOX9 dosage in cranial neural crest cells. They identify sequence features that predict buffered versus sensitive responses, validate these with reporter assays, and propose a biophysical model of TF-nucleosome competition to explain the sensitizing effect of low-affinity motifs.
- **Visible evidence base** Abstract, full introduction, results narrative (without figures), methods, discussion, data/code availability statements
- **Missing materials affecting confidence** All figures and tables, supplementary materials, exact model hyperparameters, detailed statistical outputs, and the full results section with quantitative values

## Reviewer
- **Overall assessment** This manuscript presents a compelling and timely application of transfer learning to a biologically important problem: understanding how chromatin responds quantitatively to transcription factor dosage. The conceptual advance is significant, and the combination of predictive modeling, motif discovery, evolutionary analysis, and experimental validation is ambitious and largely coherent. However, the provided text lacks the figures and quantitative details necessary to fully evaluate the strength of the claims. Several methodological choices require clarification, particularly around the definition of direct targets, the handling of correlated features, and the interpretation of the biophysical model fits. The claim that low-affinity motifs sensitize the response is intriguing but rests on correlative evidence and a simplified model that may not capture the full complexity of the system. Overall, the work is potentially important and suitable for a high-impact venue, but the current evidence base is insufficient to fully establish the central claims.

- **Who would be interested in the results, and why** This work will appeal to several overlapping communities. First, computational biologists and machine learning researchers working on regulatory genomics will be interested in the transfer learning framework as a general strategy for modeling perturbed chromatin states with limited training data. Second, molecular biologists studying transcriptional regulation, particularly those focused on dosage-sensitive transcription factors, craniofacial development, and enhancer biology, will find the sequence determinants of dosage sensitivity directly relevant. Third, evolutionary geneticists interested in constraint on regulatory elements will be interested in the purifying selection analysis. Finally, the work has potential translational relevance for interpreting non-coding variants in genome-wide association studies, which will interest human geneticists.

- **Major strengths** The study addresses a genuinely under-explored problem: most deep learning models of chromatin predict steady-state states, not responses to perturbation. The use of transfer learning to overcome the limited number of perturbed samples is methodologically sound and well-motivated. The finding that low-affinity motifs, which are typically invisible to standard motif scanning and steady-state models, play a role in dosage sensitivity is conceptually novel and important. The combination of predictive modeling with experimental validation via reporter assays strengthens the conclusions. The evolutionary analysis showing purifying selection on both buffering and sensitizing elements adds weight to the biological relevance of the findings. The biophysical model provides a mechanistic framework that goes beyond purely descriptive sequence features.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The claim that fine-tuned ChromBPNet models predict the magnitude and shape of the response to TF dosage "with accuracy approaching experimental reproducibility" is central to the paper.
- **Evidence pointer** Results section, Figure 2A,B (location not provided)
- **Concern** The text states that prediction accuracy is "roughly on par with experimental reproducibility" but provides no quantitative values. The benchmark against experimental reproducibility is a strong claim that requires explicit numbers (e.g., correlation coefficients, R² values, or error metrics) for both the model predictions and the reproducibility estimate. Without these, the reader cannot assess whether the model performance is genuinely near the theoretical limit or merely comparable to a noisy baseline.
- **Why it matters** This claim underpins the entire premise that the model is good enough to be interpretable. If the model is substantially worse than experimental reproducibility, the subsequent feature discovery could be driven by model artifacts rather than biology.
- **Resolution test** Provide the actual performance metrics for all four prediction tasks (TWIST1 and SOX9, full depletion and ED50) and the corresponding reproducibility estimates, with confidence intervals. Show that the model performance is statistically indistinguishable from the reproducibility bound.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The claim that "high-affinity, buffering Coordinator motifs" and "low-affinity, sensitizing motifs" are distinct and functionally meaningful classes.
- **Evidence pointer** Results section, Figure 3B,C,D (location not provided)
- **Concern** The classification of motifs into buffering versus sensitizing appears to be based on the direction of their contribution to ED50 in the model. However, the text does not describe how the threshold between "high-affinity" and "low-affinity" was defined, how the degeneracy of the Coordinator CWMs was quantified, or how the authors distinguished between a motif that is genuinely low-affinity versus one that is a partial match to a different motif. The mapping of CWMs to genomic locations uses a lowered threshold, which may increase false positives. The statement that "most (55.3%) of the sensitizing Coordinator instances are undetectable by even lenient PWM matching thresholds" is striking but the PWM matching threshold is not defined.
- **Why it matters** The central biological conclusion is that low-affinity motifs sensitize the response. If the classification of low-affinity is arbitrary or confounded with other sequence features, the conclusion may not hold. The lack of a clear operational definition makes the finding difficult to reproduce or extend.
- **Resolution test** Provide a precise, quantitative definition of high- versus low-affinity motifs, including the PWM score thresholds used. Show that the sensitizing effect is robust to reasonable variations in these thresholds. Demonstrate that the sensitizing motifs are not simply weak matches to other known motifs.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The claim that a biophysical model of TF-nucleosome competition "can explain the sensitizing effect of low-affinity motifs."
- **Evidence pointer** Results section, Figure 6 (location not provided)
- **Concern** The model fitting procedure is described only briefly. The authors fit the model to 540 and 1,810 REs, but the text does not state how many parameters are free, how the fits were evaluated, or whether the model was compared to alternative models (e.g., a model without nucleosome competition, or a model with independent binding sites). The statement that "the median KD ratio between the low- and high-affinity sites ranged from ~13-fold to ~29-fold" is presented without confidence intervals or a measure of fit quality. The model assumes a specific distance between sites, but the text later acknowledges that only ~40% of low-affinity sites are within the assumed range.
- **Why it matters** The biophysical model is presented as providing mechanistic insight. If the model is not rigorously tested against alternatives or if the fits are poor, the mechanistic claim is weakened. The distance assumption is a potential limitation that could undermine the model's applicability to the majority of sites.
- **Resolution test** Provide a detailed description of the fitting procedure, including the number of free parameters, the goodness-of-fit metrics, and a comparison to alternative models. Show that the model fits the data well and that the inferred parameters are biologically plausible. Address the distance assumption explicitly, either by extending the model or by showing that the results are robust to it.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Experimental validation
- **Claim pointer** The claim that reporter assays "validate" the predictive sequence features.
- **Evidence pointer** Results section, Figure 5 (location not provided)
- **Concern** The reporter assays are performed on 7 wild-type enhancers with 15 mutant constructs. This is a modest number, and the text does not describe how these enhancers were selected. The correlation between predicted and observed ΔED50 is stated to be "strong and positive" but the correlation coefficient and significance are not given. The text also notes that reporter assays measure transcriptional activity, not chromatin accessibility, which is a known discrepancy. The example of the PTCHD4 enhancer is compelling, but it is a single example.
- **Why it matters** The experimental validation is a key strength of the paper, but the limited number of constructs and the lack of quantitative details make it difficult to assess the robustness of the validation. If the correlation is driven by a few outliers, the conclusion would be weakened.
- **Resolution test** Provide the full dataset of predicted and observed ΔED50 values for all 15 mutants, with the correlation coefficient and p-value. Describe the criteria for selecting the 7 enhancers. Discuss the potential impact of the accessibility versus activity discrepancy on the interpretation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The claim that "both buffering and sensitizing features show signatures of purifying selection."
- **Evidence pointer** Results section, Figure 4F (location not provided)
- **Concern** The text states that sensitizing and buffering elements show "very similar degrees of negative selection and both were higher than shuffled regions." However, the magnitude of the difference and the statistical significance are not reported. The use of phyloP and phastCons scores from 30 primate genomes is appropriate, but the analysis may be confounded by the fact that sensitizing elements are located further from the peak summit, which could correlate with different baseline constraint levels.
- **Why it matters** The evolutionary analysis is used to argue that both types of elements are biologically relevant. If the selection signal is weak or confounded, this argument is weakened.
- **Resolution test** Provide the quantitative selection scores for each class of element and the control, with statistical tests. Show that the difference between sensitizing and buffering elements is not explained by their genomic position or other covariates.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that the model predicts "with accuracy approaching experimental reproducibility" but does not provide any context for how this was measured.
- **Required correction** Add a brief parenthetical with the key metric (e.g., "correlation with held-out replicates, R = 0.85") to give the reader a concrete sense of the performance.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods, "Modeling of TF dose-response curves"
- **Evidence pointer** Methods section
- **Issue** The text says "The data were then to the Hill equation" which appears to be a typo, likely missing the word "fit."
- **Required correction** Correct the typo to "The data were then fit to the Hill equation."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Sequence features predictive of RE responsiveness to TF dosage"
- **Evidence pointer** Results section
- **Issue** The description of the three subclusters of degenerate CWMs is brief. It is unclear whether these subclusters have distinct biological properties or whether they are simply a descriptive grouping.
- **Required correction** Clarify whether the subclusters are functionally distinct or whether they are grouped for convenience. If they are functionally distinct, describe the differences.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Prediction of RE responsiveness from DNA sequence"
- **Evidence pointer** Methods section
- **Issue** The text mentions that the model was fine-tuned for 10 epochs with a learning rate of 1e-3, but does not specify the batch size, optimizer, or the size of the training set for each task.
- **Required correction** Provide the missing training details to ensure the work is reproducible.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion of GWAS interpretation is speculative and does not provide any concrete examples or analysis to support the claim that these models could aid in fine-mapping.
- **Required correction** Either add a brief example or analysis, or soften the claim to be more clearly a future direction.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results, "Buffering and sensitizing motif occurrences show distinct regulatory logic but are similarly constrained"
- **Evidence pointer** Results section
- **Issue** The text mentions "Figure 4A,B ; Figure S5A,B" but does not describe what is shown in these panels. The reader is left to infer the content.
- **Required correction** Add a brief description of the figure panels in the text.

## Risk / unsupported claims
- The claim that prediction accuracy "approaches experimental reproducibility" is not quantitatively supported in the provided text.
- The claim that low-affinity motifs are "undetectable by even lenient PWM matching thresholds" is not supported by a defined threshold.
- The claim that the biophysical model "can explain" the sensitizing effect is not rigorously tested against alternative models.
- The claim that the reporter assays "validate" the sequence features is based on a small number of constructs without reported statistics.
- The claim that both buffering and sensitizing features show "similar degrees of negative selection" is not supported by quantitative data.
- The claim that the approach could aid in interpreting GWAS variants is speculative and not demonstrated.