## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, data/code availability statements) as provided.
- **Assessment boundary** Scientific and technical evaluation of the claims, methods, and evidence presented in the provided text. No evaluation of supplementary figures, tables, or text beyond what is explicitly described in the main text.
- **Shared manuscript claim summary** The authors present Deep DNAshape, a deep learning method that predicts DNA shape features and shape fluctuations for any DNA sequence, accounting for extended flanking regions beyond the 2-bp limit of the existing pentamer-based DNAshape method. They claim improved accuracy in predicting TF-DNA binding specificities and the ability to reveal conserved DNA shape relationships at transcription start sites across Drosophila species.
- **Visible evidence base** Main text descriptions of model architecture, training data (MC simulations, 2,121 sequences), validation against MD-derived tetramers, comparisons with DNAshapeR, application to bHLH and Hox TF binding data, and a genomic-scale analysis of TSSs in four Drosophila species. References to supplementary figures (S1-S19), tables (S1-S4), and text are made but not directly visible.
- **Missing materials affecting confidence** All supplementary figures, tables, and text; detailed quantitative results (e.g., R² values, error metrics, statistical significance tests); model architecture diagrams; hyperparameter search details; and the actual code or pretrained model outputs. The manuscript text alone does not provide sufficient quantitative evidence to fully assess the claims.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely problem in computational biology: improving DNA shape prediction by considering longer-range flanking effects. The proposed deep learning architecture is conceptually sound and the application to TF-DNA binding is of interest. However, the provided text lacks the quantitative detail necessary to evaluate the strength of the claims. Key results are described qualitatively, and the main evidence appears to reside in supplementary materials that were not provided. The core claim of superiority over the existing DNAshape method is not substantiated with specific performance metrics in the visible text. The manuscript has potential, but the case is not fully established from the supplied material.
- **Who would be interested in the results, and why** Researchers in computational biology, bioinformatics, and structural biology, particularly those studying protein-DNA interactions, transcription factor binding specificity, and DNA structural prediction. The method could also be of interest to machine learning practitioners applying deep learning to biological sequence problems. The potential to replace expensive simulations with high-throughput predictions would appeal to a broad genomics audience.
- **Major strengths**  
  1. The problem is well-motivated: the limitation of the pentamer-based approach is clearly explained, and the need for longer-range flanking effects is justified with references to prior work.  
  2. The deep learning architecture is designed to address the specific limitation, with a layer-by-layer approach that incrementally considers flanking regions, which is a sensible and novel contribution.  
  3. The method is presented as a general framework, not just a one-off predictor, which increases its potential utility.  
  4. The application to TF-DNA binding, particularly the bHLH and Hox examples, demonstrates practical relevance and the ability to generate testable hypotheses.  
  5. The inclusion of model variants trained on different data sources (MC, MD, experimental) shows awareness of data quality issues.
- **Major Concerns**  
  - **Concern ID** R1-M1  
    - **Severity** Major  
    - **Blocking** Yes  
    - **Axis** Evidence sufficiency  
    - **Claim pointer** The authors claim that Deep DNAshape "outperforms" the pentamer DNAshape method in predicting TF-DNA binding specificities (Results section, "Deep DNAshape is superior to pentamer DNAshape in elucidating TF-DNA binding" and "Deep DNAshape exhibits improved prediction accuracy for TF-DNA binding specificity").  
    - **Evidence pointer** Results section, Figures 3-5, Table S2, Figure S17-S18 (location not provided in visible text).  
    - **Concern** The visible text provides no quantitative comparison between Deep DNAshape and DNAshapeR. The claim of superiority is supported only by qualitative descriptions (e.g., "subtler differences can be seen") and references to supplementary figures. Without specific R² values, error bars, or statistical tests, the reader cannot assess whether the improvement is significant or meaningful.  
    - **Why it matters** The central claim of the manuscript is that the new method improves upon the existing state of the art. If this is not quantitatively demonstrated, the contribution is not established.  
    - **Resolution test** Provide explicit performance metrics (e.g., R², AUC, or correlation coefficients) for both Deep DNAshape and DNAshapeR on the same datasets, with appropriate statistical significance testing (e.g., paired tests across folds).  
  - **Concern ID** R1-M2  
    - **Severity** Major  
    - **Blocking** Yes  
    - **Axis** Technical soundness  
    - **Claim pointer** The authors claim that Deep DNAshape "accurately accounts for the influence of extended flanking regions" and that predictions are "almost perfectly aligned" with statistically computed values (Abstract and Results section, "Deep DNAshape predicts DNA shape and shape fluctuations considering extended flanking influences without biases").  
    - **Evidence pointer** Results section, Figures 2a-d, S5-S7, Table S2 (location not provided in visible text).  
    - **Concern** The validation of the model against MD-derived tetramers and the comparison with statistically computed values are described only qualitatively. The term "almost perfectly aligned" is not quantified. The manuscript does not report error metrics (e.g., RMSE, MAE) or correlation coefficients for the validation. Additionally, the claim of "without biases" is not supported by any bias analysis in the visible text.  
    - **Why it matters** The accuracy of the predictions is foundational to all downstream applications. Without quantitative validation, the reliability of the method is unknown.  
    - **Resolution test** Report quantitative error metrics (e.g., RMSE, MAE, Pearson correlation) for Deep DNAshape predictions against MD-derived and MC-derived values, and include a bias analysis (e.g., residual plots or per-sequence-type error breakdown).  
  - **Concern ID** R1-M3  
    - **Severity** Major  
    - **Blocking** No  
    - **Axis** Reproducibility  
    - **Claim pointer** The authors state that "all code related to training, prediction, and the pretrained models" is available at a GitHub repository (Code availability statement).  
    - **Evidence pointer** Code availability statement.  
    - **Concern** While the code availability statement is commendable, the manuscript does not describe the software dependencies, hardware requirements, or expected runtime in sufficient detail. The statement mentions processing TSS data "in a matter of minutes on a machine equipped with an NVIDIA A100," but no benchmark details are provided.  
    - **Why it matters** Reproducibility is a key criterion for methodological contributions. Without clear documentation, other researchers may struggle to use or adapt the method.  
    - **Resolution test** Provide a detailed description of the computational environment, dependencies, and a benchmark of runtime and memory usage on standard datasets.  
  - **Concern ID** R1-M4  
    - **Severity** Major  
    - **Blocking** No  
    - **Axis** Generalizability  
    - **Claim pointer** The authors claim that Deep DNAshape is a "versatile and powerful tool for diverse DNA structure-related studies" (Abstract) and that it can be retrained on alternative data sources (Discussion).  
    - **Evidence pointer** Abstract, Discussion, Results section (model variants).  
    - **Concern** The manuscript demonstrates applications to TF-DNA binding and TSS analysis, but the claim of versatility is broad. The text does not discuss potential limitations, such as the model's performance on non-B-form DNA, chemically modified bases, or sequences with unusual structural properties. The generalizability to other organisms or genomic contexts is not tested.  
    - **Why it matters** Overclaiming generalizability without evidence can mislead potential users.  
    - **Resolution test** Add a discussion of limitations and, if possible, include additional validation on diverse datasets (e.g., different organisms, non-canonical DNA structures).  
- **Minor Comments**  
  - **Concern ID** R1-m1  
    - **Severity** Minor  
    - **Axis** Clarity  
    - **Affected element** Methods section, "Pre- and post-processing of DNA shape values"  
    - **Evidence pointer** Methods section, equation (location not provided).  
    - **Issue** The normalization equation is referenced but not shown in the visible text. The description is incomplete without the actual formula.  
    - **Required correction** Include the full normalization equation in the main text or clearly reference the supplementary material where it is presented.  
  - **Concern ID** R1-m2  
    - **Severity** Minor  
    - **Axis** Readability  
    - **Affected element** Results section, "Deep DNAshape is superior to pentamer DNAshape in elucidating TF-DNA binding"  
    - **Evidence pointer** Results section, Figure 3.  
    - **Issue** The description of the bHLH example is dense and assumes prior knowledge of the TF families. The text could benefit from a brief explanation of why flanking regions are particularly important for bHLH binding.  
    - **Required correction** Add a sentence or two providing biological context for the bHLH example.  
  - **Concern ID** R1-m3  
    - **Severity** Minor  
    - **Axis** Completeness  
    - **Affected element** Methods section, "Data of transcription factor (TF)-DNA binding assays"  
    - **Evidence pointer** Methods section.  
    - **Issue** The text states that datasets were "the same as were used in 27" but does not provide details on data preprocessing, quality control, or the number of sequences per dataset.  
    - **Required correction** Provide a brief summary of dataset sizes and preprocessing steps, or refer to the original publication with specific details.  
  - **Concern ID** R1-m4  
    - **Severity** Minor  
    - **Axis** Consistency  
    - **Affected element** Discussion section.  
    - **Evidence pointer** Discussion section.  
    - **Issue** The Discussion mentions "very likey" (typo for "very likely") in the context of other studies benefiting from Deep DNAshape. This typo should be corrected.  
    - **Required correction** Fix the typographical error.  
- **Technical failings that need to be addressed before the case is established**  
  1. Lack of quantitative validation metrics for the core prediction accuracy claim (R1-M1, R1-M2).  
  2. Insufficient detail on the model architecture and training procedure to allow independent replication.  
  3. No statistical analysis of the improvement in TF-DNA binding prediction accuracy.  
  4. The claim of "without biases" is unsupported by any bias analysis.  
- **Assessment against Nature-style criteria**  
  - **Originality** The idea of using a deep learning architecture to model extended flanking effects on DNA shape is novel and goes beyond the existing pentamer-based approach. The layer-by-layer design is a creative solution to a known limitation.  
  - **Scientific importance** DNA shape prediction is widely used in studying protein-DNA interactions, and improving accuracy with longer-range effects could have broad impact. The application to TF binding and TSS analysis demonstrates relevance.  
  - **Interdisciplinary readership** The work bridges computational biology, structural biology, and machine learning. The potential to replace expensive simulations with fast predictions would interest a broad audience.  
  - **Technical soundness** The conceptual approach is sound, but the visible evidence is insufficient to confirm technical soundness. Quantitative validation and reproducibility details are missing.  
  - **Readability for nonspecialists** The text is generally clear but assumes familiarity with DNA shape features and TF binding assays. Some sections (e.g., the bHLH example) could be more accessible.  
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important problem with a promising approach, but the current evidence base is insufficient to establish the claims. The authors must provide quantitative validation, statistical comparisons, and sufficient methodological detail to support the conclusions.

## Risk / unsupported claims
- The claim that Deep DNAshape "outperforms" pentamer DNAshape in TF-DNA binding prediction is unsupported by visible quantitative data.
- The claim that predictions are "almost perfectly aligned" with statistically computed values is not quantified.
- The claim that the method is "without biases" is not supported by any bias analysis.
- The claim of "versatile and powerful tool for diverse DNA structure-related studies" is overbroad given the limited applications shown.
- The generalizability of the method to non-B-form DNA or chemically modified bases is not addressed and cannot be assessed.