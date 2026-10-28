## Review setup
- **Input scope** Full manuscript text, including summary, introduction, results, discussion, methods, figure legends, and supplementary file descriptions.
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and presentation quality. Not assessed: editorial fit, formatting, or grammatical style.
- **Shared manuscript claim summary** The authors analyzed 92 human homeodomain (HD) missense variants, including disease-associated and variants of unknown significance, using universal protein binding microarrays (PBMs) and a new statistical method ("upm") to identify variants with altered DNA binding affinity and/or specificity. They report 14 novel specificity-determining positions, several of which do not contact DNA, and show that variant effect prediction tools perform poorly at identifying specificity-altering variants.
- **Visible evidence base** Results sections, figures (Fig. 1-5), tables (Table 1), supplementary figure and table legends, methods descriptions.
- **Missing materials affecting confidence** Raw PBM data, full supplementary tables (e.g., Supplementary Tables 2-4 with detailed variant calls and scores), complete figure panels, and code implementation details are not fully accessible in the provided text. Specific statistical thresholds and validation metrics are described but not fully quantified in the main text.

## Reviewer
- **Overall assessment** This manuscript presents a valuable and comprehensive functional analysis of HD missense variants, leveraging a large-scale PBM dataset and a novel analytical approach. The identification of 14 novel specificity-determining positions, including non-DNA-contacting residues, is a significant advance. However, the strength of the conclusions depends heavily on the robustness of the "upm" method and the interpretation of specificity changes, which require closer scrutiny. The poor performance of prediction tools on specificity-altering variants is an important finding with clinical implications.
- **Who would be interested in the results, and why** Researchers in transcription factor biology, DNA-protein recognition, functional genomics, and clinical genetics. The findings on novel specificity determinants will interest those studying HD evolution and DNA binding mechanisms. The evaluation of variant effect predictors is relevant to the clinical genomics community for interpreting TF variants in disease.
- **Major strengths** 1) Large-scale, systematic functional assessment of rare HD variants, filling a gap in current knowledge. 2) Development of a new analytical method ("upm") that captures both affinity and specificity changes, including lower-affinity binding sites. 3) Discovery of multiple novel specificity-determining positions, some distal to the DNA interface, challenging existing models. 4) Rigorous validation using independent datasets (e.g., ChIP-seq) and null comparisons. 5) Clear demonstration of the limitations of current prediction tools for specificity-altering variants.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (upm method validation), R1-M2 (specificity call thresholds), R1-M3 (context-dependence claims), R1-M4 (prediction tool evaluation).
- **Assessment against Nature-style criteria**  
  - **Originality** High. The study provides novel insights into HD specificity determinants and a new analytical framework.  
  - **Scientific importance** High. It addresses a fundamental question in TF-DNA recognition and has direct implications for interpreting human genetic variation.  
  - **Interdisciplinary readership** Moderate to high. Will appeal to molecular biologists, geneticists, and computational biologists.  
  - **Technical soundness** Generally strong, but the new method and its thresholds require further validation and transparency.  
  - **Readability for nonspecialists** The main text is accessible, but the methods section is dense and may be challenging for non-experts.  
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding the validation and transparency of the "upm" method and the robustness of specificity calls.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological rigor  
- **Claim pointer** The "upm" method is claimed to identify variants with altered DNA binding affinity and/or specificity, including changes affecting lower-affinity binding sites.  
- **Evidence pointer** Methods section "Statistical analysis of PBM data"; Supplementary Fig. 2, 3  
- **Concern** The novelty and central role of the "upm" method require a more detailed and transparent description of its statistical model, assumptions, and implementation. The current text provides a high-level overview but lacks specifics on how the parametric scoring is computed, how the B-spline trends are fitted, and how the covariance between reference and variant allele scores is estimated. Without this, the method cannot be independently evaluated or reproduced.  
- **Why it matters** The entire study's conclusions rest on the validity of this method. If the method is flawed or not fully specified, the identification of novel specificity determinants and the classification of variants are called into question.  
- **Resolution test** Provide a complete mathematical description of the upm model, including all equations, parameter estimation procedures, and code availability. Include a detailed validation section demonstrating the method's performance on simulated or benchmark datasets, with quantified false positive/negative rates.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Data interpretation  
- **Claim pointer** The authors call 28 variants as having altered DNA binding specificity based on thresholds for specificityQ and edit distance.  
- **Evidence pointer** Methods section "Identification of differentially specific 8-mers"; Supplementary Fig. 9  
- **Concern** The criteria for calling a variant as specificity-altering are complex and involve multiple thresholds (specificityQ, edit distance, and a panel of combinations). The rationale for these specific thresholds and the panel approach is not fully justified. The manual removal of one variant (ARX-R332H) as a false positive raises concerns about the objectivity of the calling process.  
- **Why it matters** The specificity calls are a key output of the study. If the thresholds are arbitrary or the calling process is subjective, the list of novel specificity determinants may be unreliable.  
- **Resolution test** Clearly justify the choice of thresholds based on the null distribution, and provide a sensitivity analysis showing how the number of specificity-altering variants changes with different threshold values. Describe the manual review process in detail and consider implementing a fully automated, pre-specified calling algorithm.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** No  
- **Axis** Generalizability of claims  
- **Claim pointer** The authors state that the same missense substitution at analogous positions within different HDs often exhibited different effects on DNA binding, and that some positions may exhibit subfamily-specific or individual HD-specific effects.  
- **Evidence pointer** Results section "Missense variants at the same position in different HDs can have different effects on DNA binding"; Supplementary Fig. 7  
- **Concern** The evidence for context-dependent effects is based on a limited number of examples (e.g., position 31 in VENTX, PROP1, PAX4; position 38 in HOXD13, SIX6). The claim of "often" different effects may be overstated given the small sample size and the lack of a systematic analysis across all positions and subfamilies.  
- **Why it matters** This claim has implications for the generalizability of recognition rules and for variant interpretation. If overstated, it could mislead future studies.  
- **Resolution test** Provide a systematic analysis of all positions where the same substitution was tested in multiple HDs, with statistical testing for context-dependence. If the sample size is insufficient, temper the claim accordingly.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Clinical relevance  
- **Claim pointer** The authors suggest that variants with altered DNA binding activity may be pathogenic and prioritize them for further investigation.  
- **Evidence pointer** Results section "Disease-associated homeodomain variants exhibit a spectrum of different types of altered homeodomain DNA binding specificities"; Table 1  
- **Concern** The link between altered in vitro DNA binding and pathogenicity is inferred but not directly demonstrated. For example, the claim that NKX2-6 R150C "may also cause heart abnormalities" is speculative. The study does not provide functional validation in cellular or organismal models.  
- **Why it matters** Overstating clinical implications could lead to misinterpretation by clinicians or researchers. The study's value is in generating hypotheses, not in establishing pathogenicity.  
- **Resolution test** Clearly distinguish between variants with demonstrated pathogenicity and those with only altered binding activity. Avoid speculative statements about disease causation without direct evidence. Consider adding a disclaimer about the need for further functional studies.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Figure 1  
- **Evidence pointer** Figure 1 legend  
- **Issue** The legend for Figure 1 is brief and does not fully explain all panels, particularly the distribution of variants across HD positions and the color coding.  
- **Required correction** Expand the legend to describe each panel in detail, including the meaning of colors, symbols, and any statistical annotations.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Data presentation  
- **Affected element** Table 1  
- **Evidence pointer** Table 1 legend  
- **Issue** Table 1 lists variants and their altered binding activities but does not include quantitative measures (e.g., effect sizes, confidence intervals) or the specific 8-mers affected.  
- **Required correction** Add columns with quantitative metrics (e.g., number of affected 8-mers, magnitude of change) and reference to Supplementary Table 4 for full data.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Methods section "Analysis of variant effect prediction tools"  
- **Evidence pointer** Methods section  
- **Issue** The description of how prediction tool scores were obtained and processed is incomplete. It is unclear how missing predictions were handled and whether all tools were used with default parameters.  
- **Required correction** Provide a detailed protocol for obtaining and processing scores from each tool, including version numbers, parameters, and handling of missing data.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Literature context  
- **Affected element** Discussion  
- **Evidence pointer** Discussion section  
- **Issue** The discussion of prior studies on HD specificity determinants is brief and does not fully contextualize the novelty of the findings.  
- **Required correction** Expand the discussion to more thoroughly compare and contrast the current findings with prior work, highlighting specific advances and remaining gaps.

## Risk / unsupported claims
- The claim that 14 positions are "novel specificity-determining" is supported by the data but depends on the definition of "novel" and the completeness of prior literature. The authors should ensure no prior studies have implicated these positions.
- The statement that "the same missense substitution at analogous positions within different HDs often exhibited different effects" is based on limited examples and may be overstated.
- The suggestion that specific variants (e.g., NKX2-6 R150C) may cause disease is speculative and not directly supported by functional or clinical data.
- The performance of the "upm" method in detecting specificity changes is not fully validated against an independent gold standard, making the absolute accuracy uncertain.