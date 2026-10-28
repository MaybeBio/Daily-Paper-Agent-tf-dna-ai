## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Scientific claims, methodology, and evidence presented in the provided text; no assessment of figures or supplementary materials as they were not supplied
- **Shared manuscript claim summary** The authors use transfer learning with ChromBPNet to predict quantitative chromatin accessibility responses to TWIST1 and SOX9 dosage in cranial neural crest cells. They identify sequence features that predict buffered versus sensitive responses, validate predictions with reporter assays, and propose TF-nucleosome competition as a mechanistic explanation.
- **Visible evidence base** Abstract, introduction, results narrative, discussion, methods text; figure and table references are listed but their content is not visible
- **Missing materials affecting confidence** All figures, tables, supplementary materials, and figure legends; specific numerical results, model performance metrics, and statistical details are referenced but not visible

## Reviewer
- **Overall assessment** This manuscript presents a compelling and well-structured approach to a significant problem in regulatory genomics: predicting quantitative chromatin responses to TF dosage from DNA sequence. The transfer learning strategy is methodologically sound and addresses a real limitation of existing models. The finding that low-affinity motifs predict sensitivity while high-affinity motifs predict buffering is biologically interesting and potentially generalizable. However, the absence of all figures, tables, and supplementary materials prevents full evaluation of the evidence quality, effect sizes, and robustness of the claims. The manuscript is likely to be of interest to a broad readership in gene regulation, computational biology, and human genetics, but the strength of the conclusions cannot be fully assessed from the text alone.
- **Who would be interested in the results, and why** Researchers studying cis-regulatory logic, TF dosage sensitivity, and chromatin dynamics would find the transfer learning framework and sequence determinants directly relevant. The work also speaks to human geneticists interested in interpreting non-coding variants, particularly those affecting TF levels. The biophysical modeling component will appeal to those working on TF-nucleosome competition and quantitative models of gene regulation.
- **Major strengths** The study addresses a gap in the field by moving beyond steady-state predictions to quantitative responses to perturbation. The transfer learning approach is well motivated and appears to achieve accuracy approaching experimental reproducibility. The discovery of opposing effects of high- versus low-affinity motifs on dosage sensitivity is a novel and testable finding. The integration of computational prediction, evolutionary conservation analysis, and experimental validation via reporter assays is a strong multi-pronged approach. The biophysical model provides a mechanistic framework that connects the empirical findings to established principles of TF-nucleosome competition.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality
  - **Claim pointer** The claim that fine-tuned ChromBPNet models predict RE responses to TF dosage "with accuracy approaching experimental reproducibility" is central to the paper.
  - **Evidence pointer** Figure 2A,B; location not provided
  - **Concern** The quantitative performance metrics supporting this claim are not visible. The text states that prediction accuracy is "roughly on par with experimental reproducibility" but does not provide the actual correlation coefficients, R-squared values, or comparison statistics. Without these numbers, it is impossible to evaluate whether the models are genuinely useful or whether the comparison to experimental reproducibility is appropriately benchmarked.
  - **Why it matters** This is the foundational claim of the paper. If the predictive accuracy is not convincingly demonstrated, the subsequent interpretation of sequence features and the biological conclusions rest on a weak foundation. The comparison to experimental reproducibility is a reasonable benchmark, but the reader needs to see the actual values and the statistical framework used.
  - **Resolution test** Provide the correlation coefficients (e.g., Pearson R) between predicted and observed values for each task, the corresponding confidence intervals, and the explicit comparison to the reproducibility estimate. Show that the prediction accuracy is statistically indistinguishable from or close to the reproducibility bound, and that this holds across independent test sets.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim support
  - **Claim pointer** The claim that "high-affinity motifs that allow for heterotypic TF co-binding and are concentrated at the center of REs buffer against quantitative changes in TF dosage" and that "low-affinity or homotypic binding distributed throughout REs lead to sensitive responses."
  - **Evidence pointer** Figure 3A,B; Figure 4A-E; location not provided
  - **Concern** The distinction between buffering and sensitizing sequence features is a key finding, but the supporting evidence is not visible. The text describes motif classes and their positional distributions, but the actual effect sizes, statistical significance, and the robustness of the classification are not presented. The claim that these features are "concentrated at the center" versus "distributed throughout" needs quantitative support showing that these positional differences are significant and not driven by a small number of outliers.
  - **Why it matters** The biological interpretation hinges on the reliability of the motif classification and the positional analysis. If the classification of motifs as buffering or sensitizing is noisy or the positional differences are marginal, the conclusions about distinct regulatory logic would be weakened.
  - **Resolution test** Show the distribution of motif positions relative to RE summits for buffering versus sensitizing motifs, with appropriate statistical tests (e.g., Kolmogorov-Smirnov or permutation tests). Provide effect sizes for the contribution of each motif class to predicted dosage sensitivity, with confidence intervals. Demonstrate that the classification is stable across different thresholds and model initializations.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Validation strength
  - **Claim pointer** The claim that "enhancer reporter assays validate model predictions on mutant sequences."
  - **Evidence pointer** Figure 5A-E; location not provided
  - **Concern** The reporter assay validation is described but the results are not visible. The text mentions a "strong, positive correlation between the predicted and observed DED50 values" but does not provide the correlation coefficient, the number of constructs tested, the range of DED50 values, or the statistical significance. The example of PTCHD4 and MSR1 is illustrative but does not substitute for a systematic presentation of all results.
  - **Why it matters** Experimental validation is critical to establish that the computational predictions have biological relevance. Without seeing the actual data, the reader cannot assess whether the validation is convincing or whether it is limited to a small number of favorable cases.
  - **Resolution test** Provide a scatter plot of predicted versus observed DED50 for all tested constructs, with the correlation coefficient and p-value. Show the number of constructs, the distribution of effect sizes, and the results of any statistical tests comparing mutant to wild-type activity. Include positive and negative controls for the assay.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Mechanistic support
  - **Claim pointer** The claim that "a biophysical model of TF-nucleosome competition can explain the sensitizing effect of low-affinity motifs."
  - **Evidence pointer** Figure 6A-D; location not provided
  - **Concern** The biophysical model is presented as providing a mechanistic explanation, but the fit to experimental data is not shown. The text states that fitted values of c and KD ratios were obtained, but the quality of the fits, the number of curves fitted, and the comparison to alternative models are not presented. The model appears to be a simplified two-site version, and it is unclear whether it captures the complexity of real enhancers with multiple TF binding sites.
  - **Why it matters** The biophysical model is intended to provide a mechanistic rationale for the observed sequence determinants. If the model fits are poor or the model is too simplistic, the mechanistic claim would be overstated.
  - **Resolution test** Show the fitted curves alongside the experimental data for a representative set of enhancers. Provide the distribution of fitted parameters (c, KD ratios) and their uncertainties. Compare the model with and without TF-nucleosome competition to demonstrate that competition is necessary to explain the data. Discuss the limitations of the simplified model and whether more complex models would change the conclusions.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods, modeling of TF dose-response curves
  - **Evidence pointer** Methods section; location not provided
  - **Issue** The description of the Hill equation fitting is incomplete. The text mentions "a two-parameter Hill equation" and "a three-parameter Hill equation" but does not specify the exact form of the equation, the parameters being fit, or the criteria for choosing between the two models beyond a decrease in AIC.
  - **Required correction** Provide the explicit Hill equation used, define all parameters, and describe the model selection procedure in more detail. Specify how many curves were fit with each model and the distribution of Hill coefficients.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, deep learning model pretraining and fine-tuning
  - **Evidence pointer** Methods section; location not provided
  - **Issue** The fine-tuning procedure is described briefly. The text states that the model was fine-tuned for 10 epochs with a learning rate of 1e-3, but it is unclear how the learning rate was chosen, whether early stopping was used, and how the validation set was used during training.
  - **Required correction** Provide more details on the optimization procedure, including the optimizer used, batch size, and any regularization. Describe how the validation set was used and whether the final model was selected based on validation loss.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion, paragraph on low-affinity sites
  - **Evidence pointer** Discussion section; location not provided
  - **Issue** The discussion states that low-affinity sites "play an important role in setting the shape of the TF dosage-response curve even in REs with other, high-affinity sites." This is an interesting claim, but the text does not specify whether this is a general phenomenon or specific to TWIST1. The authors note that the same pattern was not observed for SOX9, but the implications of this difference are not discussed.
  - **Required correction** Clarify whether the sensitizing effect of low-affinity sites is expected to be general across TFs or specific to TWIST1. Discuss possible reasons for the difference between TWIST1 and SOX9 and what this implies for the generality of the proposed mechanism.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Results, section on evolutionary conservation
  - **Evidence pointer** Figure 4F; location not provided
  - **Issue** The text states that both buffering and sensitizing elements show "similar levels of negative selection" and are "higher than shuffled regions." However, the actual conservation scores are not presented, and it is unclear whether the comparison to shuffled regions is appropriately controlled for sequence composition and GC content.
  - **Required correction** Provide the mean conservation scores for each element class and the shuffled control, with confidence intervals. Describe the shuffling procedure and any controls for sequence composition.
- **Technical failings that need to be addressed before the case is established** The primary technical failing is the lack of visible quantitative results. The manuscript relies heavily on figures and tables that are not provided, making it impossible to verify the central claims about predictive accuracy, motif classification, positional distributions, reporter assay validation, and model fits. Specific technical details that need clarification include: the exact definition of "experimental reproducibility" and how it was estimated; the statistical framework for comparing model performance to this benchmark; the criteria for classifying motifs as buffering versus sensitizing; the handling of multiple testing in the motif analysis; and the sensitivity of the results to model hyperparameters and training data.
- **Assessment against Nature-style criteria**  
  *Originality*: The approach of using transfer learning to predict quantitative responses to TF dosage is novel and represents a meaningful advance over steady-state models. The finding that low-affinity motifs predict sensitivity is an original contribution.  
  *Scientific importance*: The work addresses a fundamental question in gene regulation with implications for understanding TF dosage effects in development and disease. The potential to interpret non-coding variants in terms of dosage sensitivity is significant.  
  *Interdisciplinary readership*: The topic bridges computational biology, genomics, and developmental biology, and the findings are likely to interest researchers across these fields. The biophysical modeling component adds further breadth.  
  *Technical soundness*: The methodology appears sound in principle, but the lack of visible results prevents a full assessment. The transfer learning approach is well established, and the use of ChromBPNet is appropriate. The reporter assays and conservation analysis are standard. However, the statistical rigor of the comparisons and the robustness of the classification need to be demonstrated.  
  *Readability for nonspecialists*: The manuscript is generally well written and accessible. The key concepts are explained clearly, and the narrative flows logically from problem to approach to findings to implications. Some sections, particularly the biophysical modeling, may be challenging for nonspecialists but are presented in an understandable way.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a potentially important advance with a well-designed approach and biologically interesting findings. However, the current submission does not provide sufficient visible evidence to fully establish the claims. The authors should be encouraged to resubmit with the full set of figures and tables, along with the requested statistical details, so that the evidence can be properly evaluated.

## Risk / unsupported claims
- The claim that prediction accuracy approaches experimental reproducibility is unsupported without the actual performance metrics.
- The classification of motifs as buffering versus sensitizing and the associated positional differences are unsupported without the underlying data.
- The claim that reporter assays validate model predictions is unsupported without the experimental results.
- The claim that the biophysical model can explain the sensitizing effect is unsupported without the model fits and comparisons.
- The statement that "both buffering and sensitizing features show signatures of purifying selection" is unsupported without the conservation scores and statistical tests.
- The claim that "sensitive responses were selectively linked to specific craniofacial phenotypes" (referenced from prior work) is not directly evaluated here and should be clearly distinguished from the current findings.