## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and figure legends
- **Assessment boundary** Technical soundness, methodological novelty, validation strength, and support for biological claims
- **Shared manuscript claim summary** The authors present PRINT, a computational method for detecting multiscale footprints of DNA-protein interactions from bulk and single-cell ATAC-seq data, and seq2PRINT, a deep learning framework that predicts transcription factor and nucleosome binding from DNA sequence. They apply these tools to human bone marrow hematopoiesis and mouse aging hematopoietic stem cells, revealing sequential establishment of cis-regulatory elements during differentiation and age-associated alterations in nucleosome footprints and transcription factor binding.
- **Visible evidence base** Main text figures 1-4, extended data figures 1-10 (referenced), supplementary tables 1-8 (referenced), supplementary notes (referenced)
- **Missing materials affecting confidence** Extended data figures, supplementary tables, and supplementary notes are referenced but not provided in the submitted material. These are essential for evaluating validation details, model performance metrics, and statistical methods.

## Reviewer
- **Overall assessment** This manuscript presents a potentially valuable computational framework for extracting protein-DNA interaction information from ATAC-seq data at multiple scales. The combination of bias correction, multiscale footprinting, and deep learning-based sequence interpretation is conceptually appealing and addresses real limitations in existing footprinting methods. The application to hematopoiesis and aging provides biologically interesting observations. However, the provided material lacks critical validation details and quantitative comparisons that would establish the method's reliability and superiority over existing approaches. The biological conclusions, while intriguing, require stronger statistical support and independent validation to be fully convincing.

- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and epigenomics would be interested in the methodological advances. The ability to infer TF binding and nucleosome positioning from widely available ATAC-seq data without additional experiments has broad appeal. Biologists studying hematopoiesis, stem cell aging, and gene regulation would be interested in the biological findings. The deep learning community working on sequence-to-function models would also find the seq2PRINT architecture and its interpretability features relevant.

- **Major strengths** 
  1. The conceptual advance of multiscale footprinting to capture proteins of diverse sizes is well motivated and addresses a known limitation of single-scale approaches.
  2. The integration of bias correction, statistical footprint scoring, and deep learning-based interpretation into a unified framework is elegant and practical.
  3. The use of LoRA for efficient fine-tuning across many cell states is a thoughtful solution to a real computational bottleneck.
  4. The biological applications demonstrate the method's potential to reveal dynamics not captured by standard accessibility analysis.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim pointer** The authors claim that PRINT "significantly outperformed k-mer and PWM models" for Tn5 bias correction and that the footprint scoring approach "reduces false-positive detection on deproteinized DNA by an order of magnitude."
- **Evidence pointer** Figure 1b, Extended Data Figure 1l-v (not provided)
- **Concern** The quantitative evidence for these performance claims is not visible in the provided material. Figure 1b shows a bar plot but the actual values, statistical tests, and comparison details are not described in the text. The claim of "an order of magnitude" reduction in false positives requires specific numbers and appropriate statistical testing. Without the extended data figures, I cannot assess whether the comparison to previous methods (e.g., TOBIAS) is fair and whether the performance difference is robust across conditions.
- **Why it matters** The entire utility of the PRINT method rests on its ability to accurately distinguish true protein binding from technical noise. If the bias correction and false-positive control are not rigorously validated, all downstream biological conclusions are compromised.
- **Resolution test** Provide the full comparison data including ROC/PR curves, precision-recall at matched thresholds, and statistical significance tests. Show that the improvement is consistent across multiple cell types, depths, and genomic contexts. Include the deproteinized DNA false-positive rates with confidence intervals.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validation
- **Claim pointer** The authors state that seq2PRINT "outperformed previous methods" for TF binding prediction and that the model can predict binding for TFs with weak or no direct footprint.
- **Evidence pointer** Figure 2d-e, Extended Data Figure 4c-f (not provided), Supplementary Table 2 (not provided)
- **Concern** The TF binding prediction validation is described only in summary form. I cannot evaluate: (1) how ChIP-seq ground truth was defined and whether peak calling thresholds were consistent across TFs; (2) whether the training and test sets were properly separated to avoid data leakage; (3) how the comparison methods (ChromBPNet, TOBIAS) were configured and whether they received equivalent training data; (4) the actual precision values and the number of TFs tested. The claim about predicting binding for weak-footprint TFs is particularly important but lacks supporting evidence in the visible text.
- **Why it matters** The seq2PRINT model is central to the biological applications. If its predictions are not well-validated against independent ChIP-seq data, the downstream inferences about TF dynamics during hematopoiesis and aging are unreliable.
- **Resolution test** Provide per-TF precision-recall curves, the full list of TFs tested with their performance metrics, and a clear description of the validation protocol. Show that performance is maintained for TFs with weak footprints and that the model generalizes across cell types not seen during training.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors report "widespread loss of nucleosome footprints across cCREs in old HSCs" and "38% of cCREs with differential nucleosome footprints did not show significant accessibility changes."
- **Evidence pointer** Figure 4i, Extended Data Figure 9k-q (not provided)
- **Concern** The statistical framework for calling differential nucleosome footprints between young and old HSCs is not described in the provided text. I cannot assess: (1) how pseudoreplication was handled given that cells from the same mouse are not independent; (2) what the false discovery rate control was and how it was applied; (3) whether the analysis accounted for differences in sequencing depth and cell composition between young and old samples; (4) how the 38% overlap figure was calculated and what its confidence interval is.
- **Why it matters** The aging-related conclusions are a major selling point of the manuscript. If the differential analysis is not statistically rigorous, the biological claims about age-associated changes in nucleosome positioning and TF binding are not established.
- **Resolution test** Describe the full statistical model including how mouse-level variation was modeled, how multiple testing was controlled, and how potential confounders were addressed. Provide effect sizes with confidence intervals and show that results are robust to analysis choices.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological validation
- **Claim pointer** The authors propose a "stepwise model of activation of erythroid and lymphoid cCREs" with sequential binding of pioneer factors followed by widening of CREs.
- **Evidence pointer** Figure 3d-g, Extended Data Figure 6h-s (not provided)
- **Concern** The sequential binding model is inferred from pseudotime analysis of cross-sectional data. The authors do not provide experimental validation (e.g., perturbation experiments, time-course data, or orthogonal assays) to confirm that the inferred temporal order reflects causal relationships. The correlation between TF binding timing and distance from CRE center is interesting but could reflect other factors such as motif affinity or chromatin state.
- **Why it matters** The proposed model of CRE establishment has implications for understanding enhancer function and cell fate decisions. Without experimental validation, it remains a correlative observation that may not reflect actual regulatory mechanisms.
- **Resolution test** Provide orthogonal evidence supporting the sequential binding model, such as perturbation of pioneer factor binding followed by assessment of downstream TF binding, or time-course experiments in a differentiation system. Alternatively, clearly frame the model as a hypothesis requiring future testing.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Methodological novelty
- **Claim pointer** The authors claim that PRINT and seq2PRINT provide "rich insights into DNA-binding protein dynamics from chromatin accessibility data" that go beyond existing approaches.
- **Evidence pointer** Throughout, particularly Discussion
- **Concern** The novelty relative to existing footprinting methods (e.g., TOBIAS, HINT-ATAC, ChromBPNet) and deep learning models (e.g., Basenji, Enformer) needs clearer articulation. The multiscale aspect is novel, but I cannot determine from the provided text whether the improvements are incremental or transformative. The authors should more explicitly state what specific biological questions can now be addressed that were previously impossible.
- **Why it matters** For a Nature-level publication, the methodological advance must be substantial and clearly differentiated from prior work. If the improvements are marginal, the impact may not justify the claims.
- **Resolution test** Provide a systematic comparison with existing methods on benchmark datasets, highlighting specific cases where PRINT/seq2PRINT reveals information that other methods miss. Quantify the improvement in a way that demonstrates practical significance, not just statistical significance.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 1a schematic
- **Evidence pointer** Figure 1a
- **Issue** The schematic of the multiscale footprinting workflow is described but not visible in the provided text. The description in the text is insufficient to understand the computational steps.
- **Required correction** Ensure the figure clearly illustrates the workflow from raw ATAC-seq data to multiscale footprint scores, including the bias correction step and the statistical testing.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section
- **Evidence pointer** Methods, "Tn5 bias sequence modelling"
- **Issue** The description of the neural network architecture for bias correction lacks details on hyperparameter selection, training epochs, and early stopping criteria. The statement "hyperparameters were optimized based on validation set" is insufficient for reproduction.
- **Required correction** Provide the full hyperparameter search space, final selected values, and training details in the supplementary materials.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 1e-f
- **Evidence pointer** Figure 1e-f
- **Issue** The box plots comparing PRINT and TOBIAS show distributions but no statistical test results are reported in the text. It is unclear whether the differences are significant.
- **Required correction** Add statistical test results (e.g., Wilcoxon rank-sum test) with effect sizes to the figure or text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Not explicitly provided in the submitted text
- **Issue** The data availability statement is not included in the provided material. Given the large scale of the datasets (874,480 cells from 7 donors), clear data deposition and access information is essential.
- **Required correction** Include a complete data availability statement with accession numbers for all raw and processed data.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Code availability
- **Affected element** Code availability statement
- **Evidence pointer** Not explicitly provided in the submitted text
- **Issue** The code availability statement is not included. Given the computational nature of the work, the code must be publicly available with documentation.
- **Required correction** Provide a code availability statement with repository URL and version information.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Throughout
- **Evidence pointer** Main text
- **Issue** The term "footprint" is used to describe both the statistical depletion signal and the biological protein-DNA interaction. This dual usage could confuse readers.
- **Required correction** Consider using "footprint score" for the quantitative measure and "protein-DNA interaction" or "binding event" for the biological interpretation.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 3b
- **Evidence pointer** Figure 3b
- **Issue** The description of the SPI1 promoter analysis mentions "TF binding scores derived from seq2PRINT" but the color scale and interpretation of the heatmap are not fully explained in the text.
- **Required correction** Add a clear legend explaining the color scale and how to interpret the binding scores across pseudobulks and positions.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of previous footprinting methods is brief and does not fully contextualize the advances. The authors should more thoroughly discuss why existing methods fail to capture the dynamics they observe.
- **Required correction** Expand the discussion of prior methods and their limitations, citing specific examples where they fall short.

## Risk / unsupported claims
- The claim that PRINT "significantly outperformed" existing bias correction models cannot be fully evaluated without the extended data figures and statistical details.
- The claim of "an order of magnitude" reduction in false positives on deproteinized DNA is not supported by visible quantitative evidence.
- The sequential binding model of CRE establishment during hematopoiesis is inferred from correlational pseudotime analysis and lacks experimental validation.
- The claim of "widespread loss of nucleosome footprints" in aged HSCs requires the full statistical framework to be assessable.
- The statement that seq2PRINT can predict binding for TFs with "weak or no direct footprint" needs supporting evidence showing performance metrics for such TFs specifically.
- The biological significance of the Ets/Runx composite motifs in aging is supported only by computational predictions and AlphaFold3 modeling, not by direct biochemical or genetic validation.
- The generalizability of PRINT to other species, tissue types, and experimental conditions (e.g., different Tn5 concentrations, fixation protocols) is not demonstrated.