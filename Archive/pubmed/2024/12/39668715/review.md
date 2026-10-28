## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and supplementary figure/table references. No supplementary files were provided for review.
- **Assessment boundary** The review is limited to the scientific claims, methodology, and evidence presented in the provided text. No independent replication or additional data analysis was performed.
- **Shared manuscript claim summary** The authors identify five non-synonymous single nucleotide polymorphisms (nsSNPs) in the tandem zinc finger domain of ZFP36L2 predicted to be deleterious by multiple in silico tools, and experimentally validate that all five variants (Y154H, R160W, R184C, G204D, C206F) dramatically reduce RNA binding in gel shift assays. They further use structural modeling, docking, and molecular dynamics simulations to propose atomic explanations for the reduced binding.
- **Visible evidence base** The manuscript provides descriptions of in silico prediction results (PredictSNP, SNPs&GO, MutationAssessor), EMSA data with quantification, Western blot controls, CETSA experiments, and computational analyses (DUET, DynaMut, PyMOL, HADDOCK, GROMACS). Specific numerical data, statistical details, and supplementary figures/tables are referenced but not available in the provided material.
- **Missing materials affecting confidence** Supplementary figures and tables (S1–S13, Tables 1–6) are referenced but not provided. Raw EMSA gel images, quantification data with error bars, CETSA raw data, and molecular dynamics trajectory analyses are not accessible. This limits independent verification of the reported results.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant question in RNA biology by linking naturally occurring genetic variants to functional consequences in an RNA-binding protein. The combination of computational prediction and experimental validation is commendable, and the finding that all five predicted deleterious variants indeed impair RNA binding is striking. However, the study has several technical limitations that temper the strength of the conclusions. The EMSA quantification methodology is not fully described, the CETSA data are presented without statistical analysis, and the computational structural predictions are not rigorously validated against the experimental results. The manuscript would benefit from clearer presentation of quantitative data and a more cautious interpretation of the computational predictions.
- **Who would be interested in the results, and why** Researchers studying post-transcriptional gene regulation, particularly the ZFP36 family of RNA-binding proteins, would find this work relevant. The study also has potential interest for those investigating the functional impact of rare human genetic variants, as it provides a workflow for prioritizing and validating nsSNPs in RNA-binding proteins. Clinicians or geneticists interested in variants that may contribute to hematopoietic disorders or cancer susceptibility may also find the results useful, though the clinical relevance is not directly established.
- **Major Strengths** The study combines multiple complementary approaches, from sequence-based prediction to experimental validation and structural analysis. The use of EMSA as a direct functional readout is appropriate and the inclusion of negative controls (predicted neutral variants) strengthens the validation. The identification of five variants with dramatic effects on RNA binding, including one that disrupts a zinc-coordinating cysteine, provides a clear mechanistic narrative. The authors are also transparent about the limitations of computational tools when they conflict with experimental data.
- **Major Concerns** The following concerns are detailed below.
- **Minor Comments** The following comments are detailed below.
- **Technical failings that need to be addressed before the case is established** The lack of quantitative EMSA data with proper statistical treatment, the absence of a positive control for the CETSA assay, and the unvalidated use of AlphaFold 3.0 predictions without confidence metrics for the specific variants are the most significant technical issues.
- **Assessment against Nature-style criteria** **Originality**: The work is moderately original, applying known prediction tools to a specific gene and validating with functional assays. The finding that all five predicted variants impair binding is notable but not conceptually novel. **Scientific importance**: The results are of interest to a specialized audience but do not fundamentally change our understanding of ZFP36L2 function or RNA-protein interactions. The clinical relevance is speculative given the very low allele frequencies. **Interdisciplinary readership**: The study bridges computational biology, biochemistry, and molecular biology, but the appeal is likely limited to researchers in these specific fields. **Technical soundness**: The experimental design is generally sound, but the lack of quantitative rigor in EMSA and CETSA analyses weakens the technical foundation. **Readability for nonspecialists**: The manuscript is clearly written and accessible, with helpful context on the ZFP36 family, though some computational methods may be opaque to experimental biologists.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding quantitative data presentation and statistical analysis.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental evidence
- **Claim pointer** The authors claim that all five nsSNPs "resulted in a dramatic reduction in RNA binding compared to the WT protein" based on EMSA.
- **Evidence pointer** Results section, Figure 3A and 3B; Methods, RNA Electrophoretic Mobility Assay
- **Concern** The EMSA quantification methodology is not described in sufficient detail. The authors state that "the amount of each bound and unbound probe was quantified" and that experiments were repeated four times, but they do not specify how the bound fraction was calculated, whether the WT binding was normalized to 100% in each experiment, or what statistical test was used to compare variants to WT. The reported percentages (e.g., <1%, 3.1%, 7.6%, 9.3%) lack error bars or confidence intervals in the text description, and Figure 3B is not available for inspection. Without this information, the reader cannot assess the variability or robustness of the reported differences.
- **Why it matters** The central claim of the paper rests on the EMSA results. If the quantification is not rigorous or the variability is high, the conclusion that all five variants dramatically reduce binding may be overstated. The authors also do not report whether the protein expression levels of the variants were comparable, which is critical for interpreting binding differences.
- **Resolution test** Provide a detailed description of the quantification method, including how the bound fraction was defined, how background was subtracted, and how the WT was normalized. Include error bars and individual data points in Figure 3B, and report the results of a statistical test (e.g., one-way ANOVA with post-hoc comparisons) comparing each variant to WT. Additionally, show representative Western blots with quantification of protein levels for all variants used in the EMSA.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental evidence
- **Claim pointer** The authors state that "the stability of the protein variants that most affect the RNA binding, Y154H, R184C and C206F, are comparable to the stability of the WT protein in CETSA assays."
- **Evidence pointer** Results section, Stability of protein variants using cellular temperature shift assay; Figure 5
- **Concern** The CETSA experiment is described only briefly, and no quantitative data or statistical analysis is presented. The authors do not report the melting temperatures (Tm) for each protein, the number of replicates, or how the data were analyzed. The claim of "comparable stability" is based on visual inspection of Figure 5, which is not available. Furthermore, the authors do not include a positive control (e.g., a known destabilized mutant) to validate that the assay can detect differences in stability. Without these details, the conclusion that the variants do not affect protein stability is not supported.
- **Why it matters** The authors use the CETSA result to argue that the reduced RNA binding is not due to protein instability, which is an important control. If the assay is not properly validated or quantified, this conclusion is weakened, and alternative explanations (e.g., reduced protein expression or folding) cannot be excluded.
- **Resolution test** Provide a detailed description of the CETSA protocol, including the temperature range, incubation times, and lysis conditions. Report the Tm values for WT and each variant with standard deviations from at least three independent experiments, and perform a statistical comparison. Include a positive control (e.g., a heat-sensitive mutant or a known destabilizing mutation) to demonstrate the assay's sensitivity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Computational methodology
- **Claim pointer** The authors use AlphaFold 3.0 to generate structural predictions and state that "we obtained comparable results as when we used PyMol."
- **Evidence pointer** Results section, Prediction of the effects of nsSNPs using Structure-based Analysis Tools; Figure S11
- **Concern** The use of AlphaFold 3.0 is mentioned, but the authors do not provide details on how the predictions were generated, what confidence metrics were used (e.g., pLDDT scores for the specific variant positions), or how the structures were compared to the PyMOL results. AlphaFold 3.0 is a relatively new tool, and its application to variant effect prediction is not standard. The claim of "comparable results" is vague and not supported by quantitative comparison.
- **Why it matters** The structural interpretations are used to propose atomic explanations for the reduced binding. If the AlphaFold predictions are not validated or the comparison to PyMOL is not rigorous, the mechanistic conclusions may be unreliable.
- **Resolution test** Provide the AlphaFold 3.0 confidence scores (pLDDT) for the variant positions and describe the methodology for generating and comparing the structures. If possible, validate the structural predictions against the experimental EMSA data (e.g., by correlating predicted binding disruption with observed binding reduction). Alternatively, remove the AlphaFold claims if they do not add significant insight beyond the PyMOL analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical analysis
- **Claim pointer** The authors report statistically significant differences in HADDOCK scores for R184C and C206F compared to WT (p < 0.001), but not for Y154H, R160W, and G204D.
- **Evidence pointer** Results section, Molecular docking analysis; Figure 6
- **Concern** The statistical analysis of the HADDOCK scores is not described. The authors state that "the number clusters for each interaction was considered as replicates," but it is unclear how many clusters were used, whether the data met the assumptions of the statistical test, and what specific test was performed (e.g., one-way ANOVA with post-hoc). The lack of methodological detail makes it difficult to evaluate the validity of the significance claims.
- **Why it matters** The docking results are used to support the mechanistic interpretations. If the statistical analysis is flawed or underpowered, the conclusions about which variants significantly affect binding may be incorrect.
- **Resolution test** Provide a detailed description of the statistical methods, including the number of clusters per variant, the test used, and how multiple comparisons were handled. Report the exact p-values and effect sizes for each comparison.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, Plasmid Constructs
- **Evidence pointer** Methods section, Plasmid Constructs
- **Issue** The text states "human ZFP35L2-WT" which appears to be a typo for ZFP36L2. Additionally, the description of the Kozak sequence and the Kozak consensus is not provided, which is relevant for ensuring proper translation initiation.
- **Required correction** Correct the typo to "ZFP36L2-WT" and provide the Kozak sequence used or a reference for it.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results, Subcellular localization
- **Evidence pointer** Results section, Subcellular localization of nsSNPs-containing ZFP36L2 variants; Figure S7
- **Issue** The subcellular localization results are only mentioned in a single sentence and the figure is not available. It is unclear whether the localization was quantified or if there were any differences between WT and variants.
- **Required correction** Provide a brief description of the localization results, including whether any variants showed altered localization, and include representative images with quantification if available.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion, clinical relevance
- **Evidence pointer** Discussion section, final paragraph
- **Issue** The authors state that the variants are "exceedingly rare" and that none have been associated with disease, but they do not discuss the potential implications of reduced RNA binding in heterozygous carriers or in the context of the known functions of ZFP36L2 in hematopoiesis.
- **Required correction** Add a brief discussion of the potential physiological consequences of reduced ZFP36L2 RNA binding, even if the variants are rare, and consider whether haploinsufficiency could be relevant.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methodology
- **Affected element** Methods, Molecular dynamics simulations
- **Evidence pointer** Methods section, Molecular dynamics simulations
- **Issue** The simulation parameters are described, but the authors do not state how many replicates were performed or how convergence was assessed. The choice of 1000 ns per simulation is stated, but no justification is provided.
- **Required correction** Provide details on the number of simulation replicates, convergence criteria, and any validation of the simulation setup (e.g., comparison to experimental data or known structural features).

## Risk / unsupported claims
- The claim that all five variants "dramatically reduce" RNA binding is not fully supported without quantitative EMSA data with error bars and statistical analysis.
- The claim that protein stability is "comparable" between WT and variants is unsupported without quantitative CETSA data and statistical comparison.
- The atomic explanations for the impact of each variant are based on computational predictions (PyMOL, AlphaFold, docking, MD) that are not experimentally validated, and the authors acknowledge limitations but do not provide a clear assessment of the reliability of these predictions.
- The statement that "our study offers a novel approach" is somewhat overstated, as the combination of in silico prediction and experimental validation is not entirely new, though the specific application to ZFP36L2 is novel.
- The clinical relevance of the findings is speculative, as the authors note the variants are rare and not associated with disease, but they do not provide a framework for how these results could be used in future studies.