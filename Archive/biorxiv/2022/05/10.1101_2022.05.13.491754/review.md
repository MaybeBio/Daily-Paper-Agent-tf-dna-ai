## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors report development of XGBoost-based machine learning models to predict genome-wide AhR binding at DREs in open chromatin across four human cell types, using sequence flanking, chromatin accessibility, histone modifications, TF binding, and promoter proximity. They claim high accuracy and robustness, identify predictive features that are consistent within tissues but variable across tissues, and conclude that AhR binding is governed by tissue-agnostic flanking sequence and tissue-specific chromatin context.
- **Visible evidence base** Abstract text only; no quantitative performance metrics, feature importance values, cross-validation details, or experimental validation are provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, model performance statistics, feature importance rankings, data preprocessing details, hyperparameter settings, and any comparison to alternative methods

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially valuable application of gradient-boosted trees to a biologically important problem in transcriptional regulation. The central claim that tissue-specific chromatin context modulates AhR binding beyond the core DRE motif is scientifically interesting and consistent with prior literature. However, the abstract provides no quantitative evidence to support the stated accuracy, robustness, or feature importance claims. The conclusion about tissue-specific mechanisms is inferred from cross-tissue variability in predictive patterns, but the abstract does not describe how this variability was quantified or whether it exceeds what would be expected by chance. As presented, the case is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in environmental toxicology, transcriptional regulation, and computational genomics would be interested. The work addresses a long-standing question about why AhR binding is tissue-specific despite a conserved DNA motif, which has implications for understanding dioxin toxicity and adverse outcome pathways. The machine learning approach may also appeal to those developing predictive models for transcription factor binding in general.
- **Major strengths** The problem is well-motivated and biologically important. The use of multiple cell types, including both AhR-activated and non-activated conditions, is a sensible design. The integration of diverse feature types (sequence, chromatin, histone modifications, TF binding, promoter proximity) is comprehensive. The conclusion that both tissue-agnostic and tissue-specific determinants contribute to binding is biologically plausible and testable.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: moderate to high, as the application of XGBoost to AhR binding prediction with tissue-specific focus is not entirely novel but addresses a specific gap. Scientific importance: potentially high for toxicology and gene regulation, but the abstract does not demonstrate downstream functional relevance. Interdisciplinary readership: the topic bridges computational biology and environmental health, which could attract a broad audience if the evidence is strong. Technical soundness: cannot be assessed from the abstract alone; no metrics, validation details, or methodological rigor are visible. Readability for nonspecialists: the abstract is generally clear, though terms like "DRE" and "XGBoost" are used without brief explanation, which may hinder nonspecialist comprehension.
- **Recommendation posture** Currently not established from the provided evidence. The abstract promises results that are not substantiated with any quantitative data. A supportive posture would require the full manuscript to demonstrate model performance, feature importance, and cross-tissue comparisons with appropriate statistical rigor.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Our results demonstrate highly accurate and robust models of AhR binding"
- **Evidence pointer** Abstract, Results section; location not provided
- **Concern** The abstract claims high accuracy and robustness but provides no numerical performance metrics, such as AUC, precision, recall, or F1 scores, and no description of how robustness was assessed beyond 5-fold cross-validation.
- **Why it matters** Without quantitative performance data, the reader cannot evaluate whether the models are indeed accurate or whether the claim is overstated. Robustness is a multidimensional concept that requires demonstration of stability across folds, cell types, or feature subsets.
- **Resolution test** Provide performance metrics (e.g., AUC, accuracy, sensitivity, specificity) for each cell type, with confidence intervals, and describe any additional robustness checks such as permutation testing or independent validation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** "identify patterns of transcription factor binding and histone modifications predictive of AhR binding. These patterns are consistent within tissues but highly variable across tissues, which is suggestive of tissue-specific mechanisms of AhR binding"
- **Evidence pointer** Abstract, Results section; location not provided
- **Concern** The abstract states that predictive patterns are consistent within tissues and variable across tissues, but no data are shown to support this. There is no description of how feature importance was quantified, how within-tissue consistency was measured, or how cross-tissue variability was compared to a null expectation.
- **Why it matters** The central biological conclusion of tissue-specific mechanisms rests entirely on this claim. Without statistical evidence of differential feature importance across tissues, the conclusion is speculative.
- **Resolution test** Show feature importance rankings or SHAP values for each cell type, with statistical tests comparing importance distributions across tissues, and demonstrate that within-tissue replicates (if any) are more similar than across-tissue comparisons.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability
- **Claim pointer** "predict the genome wide AhR binding status of DREs in open chromatin" across four cell types, including "AhR non-activated HepG2 hepatocellular carcinoma cells"
- **Evidence pointer** Abstract, Methods and Results sections; location not provided
- **Concern** The inclusion of a non-activated cell type (HepG2) is mentioned, but the abstract does not clarify whether the model was trained to predict binding in the absence of activation, whether the same model was applied across all cell types, or how the non-activated state affects model interpretation. The generalizability of the model to other tissues or conditions is not addressed.
- **Why it matters** The claim of genome-wide prediction implies broad applicability. If the model performs differently in activated versus non-activated states, the interpretation of tissue-specific determinants may be confounded by activation status.
- **Resolution test** Clarify the training and evaluation scheme for each cell type, report performance separately for activated and non-activated conditions, and discuss whether the model can be expected to generalize to unmeasured tissues or ligand exposures.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, Background section
- **Evidence pointer** Abstract, Background; location not provided
- **Issue** The term "DRE" is used without definition in the abstract, and "open chromatin" is mentioned without specifying the assay used (e.g., ATAC-seq, DNase-seq).
- **Required correction** Define DRE at first use and specify the chromatin accessibility assay used to define open chromatin.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological transparency
- **Affected element** Abstract, Results section
- **Evidence pointer** Abstract, Results; location not provided
- **Issue** The abstract does not state the number of DREs analyzed, the genomic feature set size, or the class balance between bound and unbound DREs, which are important for interpreting model performance.
- **Required correction** Include basic dataset statistics, such as the number of DREs per cell type and the proportion of bound versus unbound sites.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretability
- **Affected element** Abstract, Conclusions section
- **Evidence pointer** Abstract, Conclusions; location not provided
- **Issue** The conclusion that "tissue-agnostic DNA sequence flanking" is a driver is stated, but the abstract does not explain what specific sequence features were found to be important or how they relate to known AhR binding motifs.
- **Required correction** Briefly mention the nature of the flanking sequence features (e.g., nucleotide composition, position weight matrices) and whether they correspond to known cofactor motifs.

## Risk / unsupported claims
- The claim of "highly accurate and robust models" is unsupported by any quantitative data in the abstract.
- The claim of "patterns consistent within tissues but highly variable across tissues" is unsupported by any statistical evidence.
- The conclusion that AhR binding is driven by "tissue-agnostic DNA sequence flanking" and "tissue-specific local chromatin context" is a reasonable hypothesis but is not substantiated by the abstract alone.
- The generalizability of the model to genome-wide prediction across tissues is not assessable from the supplied material.