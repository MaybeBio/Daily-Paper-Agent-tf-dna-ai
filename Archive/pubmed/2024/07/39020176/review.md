## Review setup
- **Input scope** Full manuscript text, including abstract, main text, methods, and supplementary figure legends
- **Assessment boundary** Scientific content, experimental design, data analysis, claims, and conclusions as presented in the provided manuscript
- **Shared manuscript claim summary** The authors present a genome-wide experimental identification of transcriptional activation domains (ADs) in Arabidopsis thaliana transcription factors using a high-throughput yeast-based assay (PADI), develop a neural network predictor (TADA) trained on this dataset, identify six AD subtypes based on sequence features, validate ADs in the AUXIN RESPONSE FACTOR (ARF) family, and demonstrate evolutionary conservation of AD position across flowering plants.
- **Visible evidence base** Main text figures 1–5, Extended Data figures 1–10, Supplementary Tables 1–3, Supplementary Dataset 1, methods section
- **Missing materials affecting confidence** Raw sequencing data, source data files, trained model weights, code for TADA, full supplementary tables, and detailed statistical outputs are not provided in the submitted material

## Reviewer
- **Overall assessment** This manuscript presents a substantial and valuable resource for the plant transcription factor community. The high-throughput experimental approach to identify ADs genome-wide is innovative and addresses a significant gap in the field. The integration of experimental data with neural network prediction and evolutionary analysis is commendable. However, several technical concerns regarding data analysis, validation stringency, and interpretation of evolutionary patterns need to be addressed before the conclusions are fully supported.
- **Who would be interested in the results, and why** Plant molecular biologists, particularly those studying transcriptional regulation, transcription factor function, and auxin signaling. The genome-wide AD annotation will be a widely used resource. Researchers studying intrinsically disordered regions and their functional roles will also find the framework valuable. The TADA predictor has broad applicability for predicting ADs in other plant species.
- **Major strengths** 1) Genome-wide experimental identification of ADs in Arabidopsis TFs, filling a major knowledge gap. 2) Development of a predictive neural network (TADA) that outperforms existing predictors. 3) Identification of six AD subtypes with distinct sequence features, providing a framework for functional dissection. 4) Evolutionary analysis across flowering plants revealing conserved AD positioning. 5) Validation in planta using ARF7 deletion mutants.
- **Major Concerns** 
  - R1-M1: The PADI assay relies on a yeast-based system, and the authors acknowledge potential limitations but do not adequately address the false positive rate from globular domains. The claim that 43% of high-scoring fragments from globular domains may not be functional in native context is concerning, yet these fragments are still included in the AD annotation and used for TADA training.
  - R1-M2: The validation of ADs in planta is limited to ARF7 and a small number of additional TFs. The claim that PADI accurately identifies Arabidopsis ADs genome-wide is not sufficiently supported by the validation data presented.
  - R1-M3: The TADA neural network training and evaluation methodology lacks critical details. The class imbalance handling, hyperparameter selection, and potential data leakage between training and test sets are not fully described.
  - R1-M4: The evolutionary analysis of ARF ADs across 12 species is based on a single experimental replicate per species, and the criteria for defining AD presence in non-Arabidopsis species are not clearly established.
  - R1-M5: The six AD subtypes are identified through unsupervised clustering, but the biological significance of these subtypes is not experimentally validated. The claim that subtypes represent functional sub-functionalization is speculative.
- **Minor Comments** 
  - R1-m1: The manuscript would benefit from a clearer description of the PADI score calculation and the rationale for the threshold of one standard deviation.
  - R1-m2: The authors should provide more detail on the reproducibility of the yeast assay, including the number of biological replicates and the variability between experiments.
  - R1-m3: The comparison with existing AD predictors (e.g., ADpred, PADDLE) should include a more detailed description of the evaluation metrics and datasets used.
  - R1-m4: The discussion of AD subtypes would be strengthened by including specific examples of TFs from each subtype and their known biological functions.
  - R1-m5: The authors should clarify whether the TADA predictions for non-Arabidopsis species were validated experimentally or only computationally.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** 
  - Originality: High. The genome-wide experimental identification of plant ADs is novel and addresses a long-standing gap.
  - Scientific importance: High. The resource and predictive model will be widely used by the plant community and beyond.
  - Interdisciplinary readership: Moderate. The work is primarily of interest to plant biologists and those studying transcriptional regulation, but the methodological framework for IDR function could attract broader attention.
  - Technical soundness: Moderate. The experimental design is generally sound, but several technical concerns regarding validation, data analysis, and model evaluation need to be addressed.
  - Readability for nonspecialists: Good. The manuscript is clearly written, with appropriate context and explanations of key concepts.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that PADI identified ADs in over half of Arabidopsis TFs, and that 43% of high-scoring fragments from globular domains may not reflect native function.
- **Evidence pointer** Main text, Figure 1, Figure 4, Results section "Plant Activation Domain Identification (PADI)"
- **Concern** The inclusion of high-scoring fragments from globular domains in the AD annotation, despite the authors' own admission that these may not be functional in their native context, undermines the reliability of the genome-wide AD annotation. This is particularly problematic because these fragments are used to train TADA, which may learn to predict non-functional ADs. The authors should either exclude globular domain fragments from the AD annotation or provide additional evidence that these fragments are functional in planta.
- **Why it matters** The accuracy of the AD annotation is central to the manuscript's claims. If a substantial fraction of annotated ADs are false positives, the resource and the TADA predictor will be unreliable for the community.
- **Resolution test** The authors should provide a clear strategy for distinguishing functional ADs from non-functional fragments derived from globular domains. This could include experimental validation of a random sample of globular domain hits in planta, or a re-analysis of the data excluding these fragments to demonstrate that the main conclusions are unchanged.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that PADI accurately identifies Arabidopsis ADs, based on validation of a small number of TFs.
- **Evidence pointer** Main text, Figure 4, Results section "PADI and TADA validation"
- **Concern** The validation of PADI-identified ADs is limited to 9 previously characterized TFs and 24 additional hits tested in protoplasts. This is a small fraction of the 1,553 annotated ADs. The false positive rate of the assay is not systematically assessed, and the authors do not provide a clear estimate of the precision of their genome-wide annotation.
- **Why it matters** Without a robust estimate of the false positive rate, the community cannot assess the reliability of individual AD annotations. This is critical for the utility of the resource.
- **Resolution test** The authors should provide a more comprehensive validation strategy, such as testing a random sample of ADs from different families and subtypes in planta, and reporting the positive predictive value of the PADI assay.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that TADA outperforms existing AD predictors on human and plant datasets.
- **Evidence pointer** Main text, Extended Data Figure 3, Methods section "Training dataset and encoding"
- **Concern** The training and evaluation of TADA lack critical details. The class imbalance between ADs and non-ADs is acknowledged, but the specific cost-sensitive approaches are not fully described. The hyperparameter selection process is not detailed, and it is unclear whether the test set was used for model selection. Additionally, the comparison with existing predictors may be biased if the same data were used for training and evaluation.
- **Why it matters** The performance claims for TADA are a key contribution of the manuscript. If the evaluation is not rigorous, the claims of superiority over existing methods are not supported.
- **Resolution test** The authors should provide a detailed description of the training procedure, including hyperparameter tuning, cross-validation strategy, and the exact composition of the training, validation, and test sets. They should also ensure that the comparison with existing predictors is fair and unbiased.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that AD position is conserved across flowering plants based on analysis of 12 species.
- **Evidence pointer** Main text, Figure 5, Results section "AD evolution in the ARF family"
- **Concern** The evolutionary analysis is based on a single experimental replicate for each of the 12 species. The criteria for defining AD presence in non-Arabidopsis species are not clearly established, and the authors do not report the variability or confidence in their AD calls for these species. The claim of conservation of AD position is based on this limited dataset.
- **Why it matters** The evolutionary conclusions are a significant part of the manuscript's impact. If the data are not robust, the conclusions about conservation of AD position are not well supported.
- **Resolution test** The authors should provide evidence of reproducibility for the evolutionary dataset, such as technical replicates or a clear description of the statistical confidence in AD calls for each species. They should also clarify the criteria used to define AD presence in non-Arabidopsis species.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, PADI assay
- **Evidence pointer** Methods section "PADI Assay"
- **Issue** The description of the PADI score calculation is brief and lacks detail on the normalization and thresholding steps.
- **Required correction** Provide a more detailed description of the PADI score calculation, including the exact formula, the normalization procedure, and the rationale for the threshold of one standard deviation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, yeast assay
- **Evidence pointer** Methods section "Yeast Integration, Selection, and Mating"
- **Issue** The number of biological replicates and the variability between experiments are not reported for the yeast assay.
- **Required correction** Report the number of biological replicates and the variability (e.g., standard deviation) for the PADI assay, and describe how the reproducibility of the assay was assessed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, TADA comparison
- **Evidence pointer** Extended Data Figure 3
- **Issue** The comparison with existing predictors (ADpred, PADDLE) is not described in sufficient detail, including the datasets and metrics used.
- **Required correction** Provide a detailed description of the evaluation protocol, including the datasets used for comparison, the metrics reported, and the statistical significance of any differences.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, AD subtypes
- **Evidence pointer** Figure 3, Results section "TADA Network and sequence features"
- **Issue** The biological significance of the six AD subtypes is not experimentally validated, and the discussion of their potential functional differences is speculative.
- **Required correction** Provide specific examples of TFs from each subtype and discuss their known biological functions to support the claim of sub-functionalization. Alternatively, temper the interpretation of the subtypes.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, TADA predictions
- **Evidence pointer** Extended Data Figure 9
- **Issue** It is unclear whether the TADA predictions for non-Arabidopsis species were validated experimentally or only computationally.
- **Required correction** Clarify whether any experimental validation was performed for TADA predictions in non-Arabidopsis species, and if not, state this limitation explicitly.

## Risk / unsupported claims
- The claim that 53% of Arabidopsis TFs contain at least one AD is based on the PADI assay, but the false positive rate is not adequately assessed, and the inclusion of globular domain fragments may inflate this number.
- The claim that TADA outperforms existing predictors is not fully supported due to insufficient detail on the evaluation methodology.
- The claim of conservation of AD position across flowering plants is based on a single experimental replicate per species and lacks clear criteria for AD calls in non-Arabidopsis species.
- The biological significance of the six AD subtypes is not experimentally validated, and the claim of sub-functionalization is speculative.
- The claim that PADI accurately identifies Arabidopsis ADs genome-wide is not sufficiently supported by the limited validation data presented.