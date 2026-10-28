## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, data availability, acknowledgments)
- **Assessment boundary** Scientific content, methodological soundness, validity of claims, and presentation quality as presented in the preprint
- **Shared manuscript claim summary** The authors present an integrated experimental and computational approach combining ultra-deep Region Capture Micro-C (RCMC) and Micro-C data with a deep learning model (Cleopatra) to predict genome-wide 3D chromatin contact maps at sub-kilobase resolution across four human cell types, identifying over 900,000 loops and revealing cell-type-specific microcompartments and regulatory interactions.
- **Visible evidence base** Main text figures referenced (Figures 1–5, S1–S17), tables (Table S1), methods descriptions, supplementary notes (1–4)
- **Missing materials affecting confidence** Raw sequencing data not yet deposited (stated as in progress); detailed model architecture hyperparameters not fully specified; complete loop-calling parameters and thresholds not provided; full validation statistics for CH-IRON not shown; code availability not stated

## Reviewer
- **Overall assessment** This manuscript presents a substantial and ambitious effort to integrate high-resolution experimental 3D genomics with deep learning to achieve genome-wide prediction of fine-scale chromatin architecture. The combination of RCMC and Micro-C with a pre-training/fine-tuning strategy is conceptually novel and the resulting resource of predicted loops across four cell types is potentially valuable. However, several technical concerns regarding model validation, generalizability, and the interpretation of predicted loops require clarification before the central claims can be fully accepted. The work is likely to interest the 3D genomics and gene regulation communities, but the evidence as presented does not yet fully establish that Cleopatra predictions are reliable proxies for experimental data at the claimed resolution.

- **Who would be interested in the results, and why** Researchers in 3D genome organization, gene regulation, and computational biology would find this work relevant. The predicted genome-wide maps at 500 bp resolution could serve as a resource for studying enhancer-promoter interactions, cell-type-specific looping, and the principles of distal gene regulation. The methodological framework combining experimental data generation with deep learning may also interest those developing predictive models for chromatin architecture.

- **Major strengths** The study addresses a significant gap in the field by attempting to overcome the experimental intractability of genome-wide ultra-high-resolution 3D mapping. The integration of RCMC and Micro-C with a pre-training/fine-tuning deep learning approach is innovative. The validation against held-out regions and functional datasets (CRISPRi, eQTL) strengthens the utility of the predictions. The identification of cell-type-specific microcompartments and the nomination of new transcription factors provide testable hypotheses.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Cleopatra accurately predicts 3D maps at sub-kilobase bin sizes and unprecedented resolution"
- **Evidence pointer** Figures 3B–3F, S9–S11; location not provided
- **Concern** The claim of accurate prediction at sub-kilobase resolution is supported primarily by Pearson correlation coefficients and visual similarity. However, correlation metrics can be inflated by smooth, low-frequency features in contact maps. The manuscript does not report more stringent metrics such as reproducibility of specific loop calls, precision-recall against experimental RCMC loops, or comparison of insulation scores at fine scales. The held-out validation uses only three regions, which may not be representative of genome-wide performance.
- **Why it matters** The central contribution of the paper is the ability to predict fine-scale structures genome-wide. If the accuracy metrics are not robust, the downstream analyses of loops and microcompartments may be based on artifacts rather than true biological structures.
- **Resolution test** Provide precision-recall or F1 scores for loop detection in held-out regions against RCMC calls, report reproducibility metrics (e.g., stratum-adjusted correlation coefficient), and validate on additional held-out regions across different chromatin states.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We identified 5,224 loops in GM12878, 2,676 loops in HCT116, 2,866 loops in K562 and 2,154 loops in H1 cells in RCMC data at 1kb bin size"
- **Evidence pointer** Results section, Figure 2C; location not provided
- **Concern** The loop counts are presented as definitive numbers, but the methodology for loop calling (CH-IRON) is described only briefly with reference to supplementary notes. The false discovery rate, thresholds for significance, and comparison with existing loop callers are not fully detailed. The statement that RCMC identifies more loops than Micro-C is plausible but requires quantitative comparison with appropriate controls.
- **Why it matters** The reliability of all downstream analyses depends on the accuracy of loop calling. If the loop caller is not rigorously benchmarked, the biological conclusions about cell-type-specific loops and enhancer-promoter interactions may be compromised.
- **Resolution test** Provide a detailed benchmark of CH-IRON against existing methods (e.g., Mustache, HiCCUPS) on matched data, report FDR estimates, and show sensitivity analysis with different thresholds.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "We further show the enhancer-promoter loops are often anchored by CTCF, and nominate new transcription factors that may regulate cell-type-specific enhancer-promoter interactions"
- **Evidence pointer** Results section, Figures 5F–5J, S16; location not provided
- **Concern** The analysis of CTCF anchoring and transcription factor motif enrichment is correlative. The claim that "about 3/4 of E-P loops might be at least partially facilitated by CTCF" is based on motif presence within a 5 kb window, which does not demonstrate functional involvement. The nominated transcription factors are not validated experimentally or with independent datasets.
- **Why it matters** The functional implications of the predicted loops are a key aspect of the paper's significance. Without functional validation or at least orthogonal support, these claims remain speculative.
- **Resolution test** Validate nominated transcription factors with perturbation data (e.g., knockdown or degradation) or with independent chromatin interaction datasets (e.g., HiChIP for specific factors). Provide a more conservative interpretation of motif-based predictions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "We generate the highest resolution genome-wide contact maps in four human cell types"
- **Evidence pointer** Results section, Figure 4; location not provided
- **Concern** The claim of "highest resolution" is difficult to evaluate without a systematic comparison to existing predicted maps or experimental data. The effective resolution of predicted maps depends on model accuracy, which is not fully established. Additionally, the comparison to existing models (Akita v2, C.Origami) is limited to qualitative statements and a single figure.
- **Why it matters** This claim positions the work as a significant advance. If not substantiated with quantitative benchmarks, it may overstate the contribution.
- **Resolution test** Provide a quantitative comparison of resolution metrics (e.g., number of loops detected, insulation score sharpness) against existing models and experimental data across multiple cell types.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract uses terms such as "microcompartments" and "sub-kilobase bin sizes" without brief definitions, which may limit accessibility to readers outside the 3D genomics field.
- **Required correction** Add brief contextual definitions or examples to make the abstract more accessible.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods description
- **Evidence pointer** Methods section; location not provided
- **Issue** The description of the deep learning architecture is incomplete. Key hyperparameters, training details, and computational resources are not fully specified, which limits reproducibility.
- **Required correction** Provide a complete description of the model architecture, training procedure, and hyperparameters, or reference a public code repository.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion section; location not provided
- **Issue** The discussion of limitations is brief and does not address potential biases in the training data or the generalizability of the model to other cell types or conditions.
- **Required correction** Expand the limitations section to discuss potential sources of bias and the conditions under which the model may fail.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Figure 2E
- **Evidence pointer** Figure 2E; location not provided
- **Issue** The comparison with CRISPRi datasets is presented for the MYC region only. It is unclear whether this is representative of other regions.
- **Required correction** Clarify whether the CRISPRi comparison was performed for additional regions and, if not, acknowledge this limitation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Results section
- **Evidence pointer** Results section, "RCMC enables accurate identification of cell-type-specific boundaries and loops"; location not provided
- **Issue** The term "similiar" is a typographical error.
- **Required correction** Correct the typo.

- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are the primary technical concerns. The accuracy of Cleopatra predictions and the reliability of loop calling must be rigorously demonstrated with appropriate metrics and benchmarks before the biological conclusions can be considered robust.

- **Assessment against Nature-style criteria**  
  - Originality: The integration of RCMC with a pre-training/fine-tuning deep learning approach is original and distinguishes this work from prior models that rely on existing datasets.  
  - Scientific importance: The potential to generate genome-wide ultra-high-resolution maps is significant, but the importance is contingent on the reliability of predictions, which is not fully established.  
  - Interdisciplinary readership: The work bridges experimental genomics and deep learning, appealing to both communities, though the technical depth may limit accessibility.  
  - Technical soundness: The experimental data generation appears rigorous, but the validation of the computational model and loop calling requires additional metrics and benchmarks.  
  - Readability for nonspecialists: The manuscript is generally well-written but includes technical terms and methods that may be challenging for readers outside the field.

- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual framework and resource are valuable, but the current evidence does not fully substantiate the central claims of accurate sub-kilobase prediction and comprehensive loop identification. Addressing the validation and benchmarking concerns would significantly strengthen the manuscript.

## Risk / unsupported claims
- The claim of "unprecedented resolution" and "highest resolution genome-wide contact maps" is not quantitatively benchmarked against existing methods.
- The statement that "about 3/4 of E-P loops might be at least partially facilitated by CTCF" is based on correlative motif analysis and is not functionally validated.
- The nominated transcription factors for cell-type-specific loops are not experimentally or independently validated.
- The generalizability of Cleopatra to cell types beyond the four tested is not assessed.
- The claim that RCMC identifies more boundaries than Micro-C with fewer false positives is based on downsampling analysis but lacks a formal statistical comparison.