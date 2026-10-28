## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends as provided.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text. No assessment of supplementary figures or tables beyond what is referenced in the text.
- **Shared manuscript claim summary** The authors develop a high-throughput assay (ChIP-ISO) to systematically dissect sequence features affecting FOXA1 binding specificity in A549 cells. They report that AP-1 and CEBPB co-binding strongly enhances FOXA1 binding, that FOXA1 and AP-1 show binding cooperativity in vitro, that local sequence rather than chromatin context determines FOXA1 binding, and that AP-1 partially explains cell-type-specific FOXA1 binding.
- **Visible evidence base** Figures 1-7 as described in text, supplementary figures S1-S7 as referenced, methods section, and statistical analyses as described.
- **Missing materials affecting confidence** Actual figure images, supplementary tables (Table S1-S3), detailed numerical data for all plots, exact statistical test outputs, and the trained neural network parameters are not available for direct inspection.

## Reviewer
- **Overall assessment** This manuscript presents a technically sophisticated approach to dissecting sequence determinants of pioneer factor binding. The ChIP-ISO method is a valuable contribution that allows systematic perturbation of sequence features in a controlled genomic context. The finding that AP-1 is a major co-factor for FOXA1 binding is well-supported by multiple lines of evidence including mutational analysis, in vitro assays, and neural network interpretation. However, several concerns regarding the generalizability of the conclusions, the quantitative rigor of some analyses, and the interpretation of the chromatin context experiments need to be addressed.
- **Who would be interested in the results, and why** Researchers studying transcription factor binding specificity, pioneer factor biology, enhancer regulation, and cell-type-specific gene regulation. The methodological advance (ChIP-ISO) will be of interest to the broader genomics and gene regulation community. The finding of FOXA1-AP-1 cooperativity has implications for understanding how pioneer factors achieve specificity in different cellular contexts.
- **Major strengths** 1) The ChIP-ISO method is a creative and rigorous approach that addresses a fundamental limitation in studying TF binding specificity. 2) The combination of in vivo, in vitro, and in silico approaches provides complementary evidence. 3) The finding that AP-1 is a dominant co-factor for FOXA1 is convincing and potentially important. 4) The demonstration that local sequence, not chromatin context, primarily determines FOXA1 binding is a significant conceptual contribution.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (generalizability of AP-1 cooperativity), R1-M2 (quantitative rigor of in vitro cooperativity), R1-M3 (interpretation of chromatin context experiments), R1-M4 (neural network interpretability).
- **Assessment against Nature-style criteria** **Originality**: High. The ChIP-ISO method is novel and the systematic dissection of sequence features is a fresh approach. **Scientific importance**: Moderate to high. The finding that AP-1 is a key determinant of FOXA1 binding specificity has implications for understanding pioneer factor function, but the broader significance for gene regulation mechanisms needs to be more clearly articulated. **Interdisciplinary readership**: Moderate. The work will appeal primarily to molecular biologists and genomics researchers. The methodological advance may attract a broader audience. **Technical soundness**: Generally strong, but several concerns need to be addressed (see Major Concerns). **Readability for nonspecialists**: The manuscript is clearly written and the logic is easy to follow, though some sections (neural network analysis) may be challenging for non-experts.
- **Recommendation posture** Supportive if technical concerns are resolved.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability of findings
- **Claim pointer** The authors claim that "AP-1 is a crucial co-factor that potentiates FOXA1 binding to the CCND1e" and extend this to genome-wide conclusions.
- **Evidence pointer** Figures 2E-2J, 3A-3E, 4B-4I
- **Concern** The central claim of AP-1-FOXA1 cooperativity is established primarily in the context of the CCND1e enhancer. While the genome-wide analyses support co-binding, the causal relationship between AP-1 and FOXA1 binding at other loci is inferred rather than directly tested. The authors show that AP-1 motif mutation reduces FOXA1 binding in a subset of native loci (Figure 3C-3E), but the number of loci tested is limited (10-20 per TF). The claim that AP-1 is a "crucial co-factor" for FOXA1 binding genome-wide would be strengthened by a more systematic perturbation, such as AP-1 knockdown followed by FOXA1 ChIP-seq.
- **Why it matters** The generalizability of the cooperativity finding is central to the paper's main conclusion. If AP-1 cooperativity is specific to certain genomic contexts, the conclusion that this is a general mechanism for FOXA1 binding specificity would be overstated.
- **Resolution test** Provide additional evidence that AP-1 perturbation (e.g., dominant-negative A-FOS or siRNA) globally reduces FOXA1 binding at AP-1-associated sites, or temper the claims to reflect the context-dependence of the cooperativity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor of in vitro cooperativity
- **Claim pointer** The authors state that "FOXA1 and AP-1 show binding cooperativity in vitro" based on EMSA experiments.
- **Evidence pointer** Figures 5F-5I
- **Concern** The in vitro cooperativity is demonstrated using EMSA with a single DNA template (CCND1e with mutations). The quantification appears to be based on band intensity measurements, but the statistical analysis and the magnitude of the cooperativity effect are not clearly described. The claim of "moderate" cooperativity is vague. A more quantitative approach, such as measuring binding affinities (Kd) in the presence and absence of the partner factor, would provide stronger evidence.
- **Why it matters** The in vitro cooperativity is a key piece of evidence supporting the model that FOXA1 and AP-1 directly interact to enhance each other's binding. Without quantitative binding data, the strength and specificity of this interaction remain unclear.
- **Resolution test** Provide quantitative binding curves and Kd values for FOXA1 and AP-1 binding alone and together, or clearly state the limitations of the EMSA approach and temper the claims accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of chromatin context experiments
- **Claim pointer** The authors conclude that "FOXA1's binding is determined more by local sequences than chromatin context, including eu-/heterochromatin."
- **Evidence pointer** Figures 6A-6G
- **Concern** The conclusion that chromatin context plays a minor role is based on comparing FOXA1 binding at native loci versus the same sequences relocated to the AAVS1 locus. However, the AAVS1 locus is a specific euchromatic environment, and the authors only tested a limited number of heterochromatic sequences (56 from H3K9me3 regions). The artificial deposition of H3K9me3 via KRAB-dCas9 (Figure 6I-6J) reached only ~10% of the highest genomic H3K9me3 level, which may not recapitulate the full repressive environment. The conclusion that chromatin context is largely irrelevant may be premature.
- **Why it matters** The relative contribution of local sequence versus chromatin context to pioneer factor binding is a fundamental question. If the conclusion is overstated, it could mislead the field about the mechanisms of pioneer factor targeting.
- **Resolution test** Test a larger and more diverse set of heterochromatic sequences, or use a more robust method to deposit H3K9me3, or temper the conclusion to reflect the specific conditions tested.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Neural network interpretability
- **Claim pointer** The authors use neural network analysis to support the finding that AP-1 and CEBPB motifs are important for FOXA1 binding.
- **Evidence pointer** Figures 3F-3G, 6H
- **Concern** The neural network analysis is described but the details of the model architecture, training, and validation are not fully provided in the main text. The feature attribution analysis (DeepLift-SHAP) and motif discovery (TF-MoDISco) are powerful tools, but the interpretation depends on the quality of the trained model. The authors report an auPRC of 0.20, which is modest, and it is unclear how this compares to other models in the field. The claim that the CNN analysis "supports" the findings would be strengthened by a more thorough description of the model performance and limitations.
- **Why it matters** The neural network analysis is used as independent evidence for the importance of AP-1 and CEBPB. If the model is not well-validated or the interpretation is not robust, this supporting evidence is weakened.
- **Resolution test** Provide more details on model training, hyperparameter selection, and performance metrics. Consider additional validation approaches, such as testing the model on independent datasets or using alternative interpretation methods.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of method description
- **Affected element** ChIP-ISO method description
- **Evidence pointer** Figures 1A, S1C-S1J
- **Issue** The ChIP-ISO method is described in the main text but the reader is referred to the STAR Methods for details. The schematic in Figure 1A is helpful but the key steps of the method (e.g., library design, integration efficiency, ChIP conditions) could be summarized more clearly in the main text to aid understanding.
- **Required correction** Provide a brief summary of the key steps and quality control measures of the ChIP-ISO method in the main text.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Correlation coefficients and significance values
- **Evidence pointer** Figures 1B, 2G, 3A
- **Issue** The correlation coefficient of 0.78 between biological replicates is reported, but the number of replicates and the statistical test used are not stated. Similarly, the significance of motif enrichment (p value < 10^-1000) is reported but the method for calculating this value is not described.
- **Required correction** Clearly state the number of replicates and the statistical methods used for all reported correlation coefficients and p values.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of distance analysis
- **Affected element** Figure 4H
- **Issue** The analysis of the distance between FOXA1 and AP-1 motifs in lost versus unchanged peaks is interesting, but the interpretation that "proximity, but not a specific spacing or orientation" is required for cooperativity is based on a relatively small number of peaks. The weak enrichment at 10, 20, 30, and 40 bp is intriguing but the statistical significance of this periodicity is not assessed.
- **Required correction** Provide statistical analysis of the distance distribution and the periodicity, or temper the interpretation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Cell-type specificity analysis
- **Affected element** Figure 7
- **Evidence pointer** Figures 7A-7E
- **Issue** The analysis of cell-type-specific FOXA1 binding is based on three cell lines. The conclusion that AP-1 expression levels correlate with FOXA1 binding patterns is suggestive but the sample size is small. The neural network analysis across 13 cell lines is more comprehensive but the results are only briefly described.
- **Required correction** Provide more details on the 13 cell line analysis and consider whether the three cell line comparison is sufficient to support the conclusions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion
- **Issue** The limitations section is brief and focuses on technical aspects of the ChIP-ISO method. The authors do not discuss the potential limitations of their conclusions, such as the possibility that other co-factors or mechanisms may be important in other cell types or contexts.
- **Required correction** Expand the limitations section to address the generalizability of the findings and potential alternative interpretations.

## Risk / unsupported claims
- The claim that "AP-1 is partially responsible for differential binding of FOXA1 in different cell types" is supported by correlative evidence but not directly tested. The causal role of AP-1 in cell-type-specific FOXA1 binding is not established.
- The claim that "chromatin context plays a minor role" in FOXA1 binding is based on a limited set of heterochromatic sequences and a single euchromatic integration site. This conclusion may not be generalizable.
- The claim of "binding synergy" between FOXA1 and AP-1 is supported by the data, but the molecular mechanism (direct protein-protein interaction vs. cooperative DNA binding) is not fully resolved.
- The neural network analysis is used to support the importance of AP-1 and CEBPB motifs, but the model performance (auPRC = 0.20) is modest and the interpretation may be sensitive to the training data and architecture.