## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion) from bioRxiv preprint
- **Assessment boundary** Scientific claims, methodology, evidence quality, and interpretation as presented in the provided text; no supplementary figures or tables were available for direct inspection
- **Shared manuscript claim summary** The authors use their previously developed computational model, ChIPanalyser, to systematically analyse ChIP-seq data for hundreds of human and mouse transcription factors (TFs) and classify them based on their chromatin accessibility preferences. They report that approximately one third of TFs bind chromatin in an accessibility-independent manner at their strongest binding sites, and identify a small number of TFs that prefer dense chromatin. They further validate their approach across multiple cell lines and accessibility measurement methods.
- **Visible evidence base** Main text figures referenced (Figures 1-5), supplementary figures and tables referenced but not provided, methods descriptions, and discussion of results
- **Missing materials affecting confidence** Supplementary figures (S1-S14), supplementary tables (S1-S10), actual numerical results, model parameter estimates, detailed statistical outputs, and code implementation details were not available for inspection

## Reviewer
- **Overall assessment** This manuscript presents a systematic computational analysis of TF binding preferences with respect to chromatin accessibility, using a previously published model (ChIPanalyser). The central claim, that many TFs bind inaccessible chromatin at their strong binding sites, is potentially interesting and relevant to the field of gene regulation. However, the evidence as presented in the main text is insufficient to fully evaluate the robustness of the classification scheme, the statistical significance of the findings, and the biological interpretation. The manuscript would benefit from clearer presentation of validation metrics, more rigorous statistical comparisons, and a more cautious interpretation of the model's predictions.
- **Who would be interested in the results, and why** Researchers studying transcription factor binding mechanisms, chromatin biology, gene regulation, and computational modelling of protein-DNA interactions. The findings could be relevant to those interested in pioneer factors, bookmarking factors, and the relationship between chromatin structure and TF occupancy.
- **Major strengths** The study addresses an important question in gene regulation, namely whether TFs can bind inaccessible chromatin. The use of a mechanistic, interpretable model (ChIPanalyser) rather than black-box machine learning is a strength. The analysis spans multiple species and cell lines, and the authors consider multiple methods for measuring chromatin accessibility. The discussion of potential confounding factors, such as dataset quality and TF concentration, shows awareness of limitations.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that approximately one third of TFs are predicted to bind the genome in a DNA accessibility independent fashion, and that this classification is robust.
  - **Evidence pointer** Results section "Many human TFs are predicted to bind to the DNA at their strong binding regions independent of DNA accessibility"; Figure 3; Supplementary Tables S2-S5
  - **Concern** The classification of TFs into AIF, ADF, IDF, and partial categories relies on threshold-based criteria applied to AUC values. The thresholds are described as informed by k-means clustering, but the specific rationale for choosing AUC > 0.8 and difference > 0.3 is not fully justified. More importantly, the manuscript does not report confidence intervals, statistical tests, or sensitivity analyses for these classifications. It is unclear whether the classifications are stable across different choices of thresholds, different accessibility datasets, or different model parameter estimates.
  - **Why it matters** The central claim of the paper depends entirely on the reliability of the TF classification. If the classification is sensitive to arbitrary threshold choices or to noise in the underlying data, the main conclusion could be substantially altered.
  - **Resolution test** Provide a sensitivity analysis showing how classifications change with varying thresholds. Report confidence intervals or bootstrap estimates for the proportion of TFs in each class. Show that classifications are consistent across biological replicates and across different accessibility datasets.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological validation
  - **Claim pointer** The authors state that ChIPanalyser predicts TF binding profiles with high accuracy, with 95 out of 110 human datasets having AUC >= 0.8.
  - **Evidence pointer** Results section "Modelling binding of human transcription factors"; Figure S2B; Supplementary Table S2
  - **Concern** The manuscript reports AUC values as a measure of model fit, but does not provide a clear baseline or null model for comparison. It is unclear what AUC value would be expected by chance, or how the model performs compared to simpler alternatives (e.g., using only motif presence, or only accessibility). The validation is performed on the top 50 regions with strongest ChIP signal, which may not be representative of genome-wide performance. The authors do not report how the model performs on held-out chromosomes or on regions with weaker signal in the initial K562 analysis.
  - **Why it matters** Without a clear baseline or proper validation strategy, the reported AUC values are difficult to interpret. High AUC on the strongest binding regions may not indicate that the model captures the biology of TF binding genome-wide.
  - **Resolution test** Report AUC against a null model (e.g., random genomic regions, or motif-only predictions). Perform cross-validation or held-out chromosome validation. Report performance metrics separately for strong, medium, and weak binding regions in the K562 analysis.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretational caution
  - **Claim pointer** The authors interpret accessibility-independent binding as evidence that TFs can bind dense chromatin, and suggest that this may indicate pioneer or bookmarking activity.
  - **Evidence pointer** Discussion section "Several transcription factors have no or limited preference for open or dense chromatin"
  - **Concern** The model uses accessibility data as an input and then tests how predictions change when accessibility is varied. However, the interpretation that "accessibility-independent binding" means the TF can bind dense chromatin in vivo is a strong claim. The model does not directly measure TF binding to nucleosomal DNA; it infers this from the fit of predicted profiles to ChIP-seq data. The authors acknowledge that co-factors, TF concentration, and other factors may influence binding, but the discussion sometimes overstates the biological implications of the computational classification.
  - **Why it matters** The biological interpretation of the computational results is a key part of the paper's significance. Overstating the implications could mislead readers about the strength of the evidence for pioneer or bookmarking activity.
  - **Resolution test** Soften the language in the discussion to clearly distinguish between computational predictions and experimental evidence. Explicitly state that the model identifies candidate TFs that may bind inaccessible chromatin, and that experimental validation is needed.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** The authors state that all scripts are available at a GitHub repository.
  - **Evidence pointer** Data access section
  - **Concern** The manuscript states that scripts are available, but does not provide details on the exact versions of software packages, the specific parameters used for each analysis, or a clear description of the computational environment. The ChIPanalyser model itself is described in previous publications, but the specific implementation details for this analysis (e.g., how accessibility data were processed, how QDA thresholds were applied) are not fully described in the methods.
  - **Why it matters** Reproducibility is a core requirement for computational studies. Without detailed methods and version information, other researchers may not be able to reproduce the results.
  - **Resolution test** Provide a detailed methods section with all software versions, parameters, and data processing steps. Ensure the GitHub repository contains a complete workflow with documentation.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 1D
  - **Evidence pointer** Results section "Modelling binding of human transcription factors"
  - **Issue** The description of Figure 1D mentions three classes of TFs (AIF, ADF, IDF), but the figure itself is not available for inspection. The text would benefit from a clearer description of what is shown in the figure and how the classes are visually distinguished.
  - **Required correction** Provide a more detailed description of Figure 1D in the text, including what each panel shows and how the classification is visually represented.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Methods section
  - **Evidence pointer** Methods section "Modelling TF binding with ChIPanalyser"
  - **Issue** The equation for the probability of TF binding is mentioned but not fully defined in the text. The variables in the equation are not all explained.
  - **Required correction** Define all variables in the equation and provide a brief explanation of the model's assumptions.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Results section "Mouse TFs display similar behaviour to human TFs"
  - **Evidence pointer** Figure 4
  - **Issue** The text states that 90% of mouse datasets were modelled with high accuracy, but does not report the exact number of datasets or the range of AUC values.
  - **Required correction** Report the exact number of datasets and the range of AUC values for the mouse analysis.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Consistency
  - **Affected element** Results section "Jun is predicted to bind before the chromatin is open in MCF10A cells upon Her2 overexpression"
  - **Evidence pointer** Figure 6
  - **Issue** The text describes predictions for seven TFs but only discusses JUN in detail. It is unclear what the predictions are for the other six TFs.
  - **Required correction** Briefly describe the predictions for all seven TFs, or state why only JUN is discussed in detail.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Literature context
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section
  - **Issue** The discussion mentions previous studies on pioneer factors but does not provide a systematic comparison of the TFs identified here with those previously reported.
  - **Required correction** Add a more systematic comparison with previously identified pioneer factors and discuss any discrepancies.

## Technical failings that need to be addressed before the case is established
- R1-M1: Lack of sensitivity analysis for classification thresholds
- R1-M2: Inadequate validation strategy for model predictions
- R1-M4: Insufficient methodological detail for reproducibility

## Risk / unsupported claims
- The claim that "approximately one third of TFs are predicted to bind the genome in a DNA accessibility independent fashion" is not fully supported without sensitivity analyses and confidence intervals.
- The claim that JUN acts as a bookmarking TF based on computational predictions alone is speculative and not directly supported by experimental evidence.
- The statement that "many TFs can bind dense chromatin" is an extrapolation from model predictions and should be framed as a hypothesis.
- The comparison between the proportion of TFs identified here (one third) and the previous estimate of 16% pioneer factors is not rigorously quantified or statistically tested.
- The claim that ATAC-seq and DNaseI-seq perform better than MNase-seq and NOMe-seq is based on limited comparisons and may be confounded by dataset quality.

## Assessment against Nature-style criteria
- **Originality** The study applies a previously published model to a new question, namely the systematic classification of TFs by chromatin accessibility preference. While the approach is not entirely novel, the scale of the analysis and the focus on inaccessible chromatin binding is a useful contribution.
- **Scientific importance** The question of whether TFs can bind inaccessible chromatin is important for understanding gene regulation, pioneer factors, and chromatin dynamics. However, the findings are largely computational and would benefit from experimental validation to increase their impact.
- **Interdisciplinary readership** The work is primarily of interest to computational biologists and researchers studying transcription factor binding. The methods and findings may be less accessible to a broader biological audience without additional context and clearer explanations.
- **Technical soundness** The model itself has been previously published and validated, but the specific application and classification scheme presented here have methodological weaknesses, particularly regarding threshold selection, validation, and sensitivity analysis.
- **Readability for nonspecialists** The manuscript is written in a technical style that assumes familiarity with ChIP-seq, chromatin accessibility assays, and computational modelling. The abstract is clear, but the main text would benefit from more accessible explanations of the model and the classification scheme.

## Recommendation posture
**Currently not established from the provided evidence.** The manuscript addresses an interesting question and presents a potentially useful computational framework, but the evidence as presented is insufficient to support the main claims. The classification scheme needs sensitivity analysis, the model validation needs to be more rigorous, and the biological interpretations need to be tempered. With substantial revisions addressing these concerns, the manuscript could become a valuable contribution to the field.