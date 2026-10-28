## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, conclusion, author contributions, conflicts of interest, data availability, acknowledgements)
- **Assessment boundary** Scientific and technical evaluation of the reported engineering strategy, screening platform, and performance claims for compact cytosine base editors based on SsdAtox
- **Shared manuscript claim summary** The authors report an integrated computational and directed evolution approach to engineer SsdAtox, a compact deaminase from Pseudomonas syringae, into cytosine base editors with improved activity, reduced indel formation, and lower cytotoxicity compared to wild type. They introduce Trinity-Screen, an E. coli-based three-in-one selection platform, and a new metric (BEPI) for standardizing base editor performance comparisons.
- **Visible evidence base** Methods descriptions for structure analysis, alanine scanning, library construction, Trinity-Screen, and mammalian cell assays; results narrative with references to Figures 1-5 and supplementary tables/figures; data availability statement referencing NCBI SRA accession PRJNA1203172
- **Missing materials affecting confidence** Figures and supplementary tables/figures are referenced but not provided; no raw numerical data for editing efficiencies, indel rates, or statistical analyses; no detailed protocol for Trinity-Screen selection stringency; no information on sequencing depth or coverage for NGS analyses; no negative control data for the selection platform

## Reviewer
- **Overall assessment** The manuscript presents a potentially valuable integrated strategy for engineering compact base editors, combining structure-guided rational design with a novel three-axis bacterial selection system. The concept of simultaneously selecting for activity, low indel formation, and reduced toxicity is conceptually sound and addresses a real need in the field. However, the current manuscript has several critical gaps that prevent full evaluation of the claims. The absence of figures and raw data makes it impossible to verify the magnitude of reported improvements, the statistical robustness of comparisons, or the functional significance of the engineered variants. The BEPI metric, while an interesting contribution, requires more rigorous justification and validation. The mechanistic explanations for variant performance rely heavily on computational predictions without experimental validation. The Trinity-Screen platform is described at a conceptual level but lacks the procedural detail necessary for replication or assessment of its selectivity. The claim of outperforming BE4max requires careful scrutiny given the limited number of endogenous targets tested and the lack of comprehensive off-target analysis.
- **Who would be interested in the results, and why** Researchers in genome editing, particularly those working on base editor development and optimization; synthetic biologists interested in directed evolution platforms; structural biologists studying deaminase enzymes; therapeutic developers seeking compact editing tools for delivery applications. The Trinity-Screen platform and BEPI metric could have broader utility beyond SsdAtox engineering.
- **Major strengths** The integrated approach combining computational prediction with directed evolution is methodologically innovative. The Trinity-Screen concept of simultaneously selecting for three desirable traits in a single bacterial workflow is elegant and addresses a recognized limitation of sequential screening approaches. The identification of non-overlapping mutation sites relative to previous engineering efforts suggests the selection platform accesses a distinct solution space. The BEPI metric, despite requiring further validation, represents a thoughtful attempt to standardize base editor comparisons beyond simple efficiency ratios. The compact size of SsdAtox and its demonstrated mitochondrial editing potential make this a clinically relevant target for optimization.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5, R1-M6
- **Assessment against Nature-style criteria** 
- **Recommendation posture** Currently not established from the provided evidence

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim summary** The authors claim up to 30-fold improvement in C-to-T editing efficiency and 10-fold reduction in cytotoxicity for optimized SsdAtox variants compared to wild type.
- **Evidence pointer** Results section, Figures 1-5 (figures not provided)
- **Concern** The central quantitative claims of the manuscript cannot be verified because all figures and supplementary data are absent from the provided materials. The reported fold-improvements, indel rates, and cytotoxicity measurements are presented only as narrative summaries without accompanying numerical data, statistical analyses, or visualization. This is a fundamental limitation that prevents assessment of the magnitude, consistency, and significance of the reported improvements.
- **Why it matters** The primary contribution of this work is the demonstration that the integrated computational and directed evolution approach yields variants with substantially improved performance. Without access to the underlying data, the validity and reproducibility of these claims cannot be evaluated. The absence of effect sizes, confidence intervals, and statistical test results for the key comparisons undermines confidence in the conclusions.
- **Resolution test** Provide all figures with complete data visualization, including individual data points, error bars, and statistical annotations. Include raw numerical values for editing efficiencies, indel rates, and cytotoxicity measurements for all variants and targets in supplementary tables. Report effect sizes and confidence intervals for all key comparisons.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim summary** The authors claim that Trinity-Screen simultaneously selects for high activity, reduced indel formation, and low toxicity in a single E. coli workflow.
- **Evidence pointer** Methods section "Trinity-Screen", Results section "Directed Evolution With Trinity-Screen", Figure 2
- **Concern** The mechanistic basis for the three selection axes is not adequately described or validated. The activity selection relies on correction of a defective kanamycin resistance start codon, but the relationship between editing efficiency at this single locus and overall base editor activity is not established. The DSK reduction axis assumes that indels at repetitive genomic loci correlate with indel formation at on-target sites in mammalian cells, but this connection is not demonstrated. The toxicity axis conflates general protein toxicity with deaminase-specific effects. No control experiments are described to show that each selection pressure operates independently and as intended.
- **Why it matters** The novelty of this work rests substantially on the Trinity-Screen platform. If the three selection pressures are not mechanistically independent or do not accurately report on the traits they claim to select for, the validity of the entire directed evolution approach is compromised. The lack of validation experiments makes it impossible to determine whether the enriched variants are truly superior on all three axes or whether the selection is dominated by one or two pressures.
- **Resolution test** Provide validation experiments demonstrating that each selection axis functions independently. Include control experiments with known high-activity/high-indel and low-activity/low-indel variants to show differential survival under each selection pressure. Demonstrate that the kanamycin resistance readout correlates with editing efficiency across a range of activities. Show that the repetitive locus DSK selection specifically reports on indel propensity rather than general DNA damage sensitivity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Metric validation
- **Claim summary** The authors propose BEPI as a standardized metric for comparing base editor performance that integrates editing efficiency and indel frequency.
- **Evidence pointer** Methods section "Development of BEPI Evaluation System", Results section "Development of BEPI for Base Editor Assessment", Table S2, Figures S2-S3
- **Concern** The BEPI formula (C-to-T - indel)/exp(indel/10) is presented as the optimal choice among fifteen candidates, but the selection criteria and validation approach are not described in sufficient detail. The manuscript states that formulas were assessed for "computational stability, sensitivity patterns, and practical utility" but does not define these criteria operationally or show the comparative analysis that led to the selection of Formula 14. The claim that BEPI provides a "balanced analytical framework" is not supported by any formal analysis of its properties, such as monotonicity, boundedness, or discriminative power across the relevant range of values.
- **Why it matters** BEPI is used throughout the manuscript as the primary metric for comparing variant performance and for the key claim that optimized variants outperform BE4max. If the metric is not properly validated or has undesirable mathematical properties, the ranking of variants and the conclusions drawn from these rankings could be misleading. The choice of the exponential penalty term and the linear subtraction in the numerator appear arbitrary without a systematic justification.
- **Resolution test** Provide a detailed description of the evaluation criteria used to select Formula 14, including the full comparative analysis of all fifteen formulas across the 56 test scenarios. Demonstrate that BEPI satisfies desirable properties for a performance metric, such as monotonic response to changes in efficiency and indel rate, appropriate sensitivity across the clinically relevant range, and robustness to small measurement errors. Validate BEPI against existing metrics or against expert ranking of representative variants.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic interpretation
- **Claim summary** The authors claim that the K31 residue acts as a gatekeeper whose substitution enlarges the DNA binding pocket, and that this mechanism explains the enhanced activity of K31X variants.
- **Evidence pointer** Results section "Identification of K31X Mutation via AlphaFold Alanine Scan and Site Saturation Mutation Screen", Figure 1
- **Concern** The mechanistic interpretation relies entirely on computational predictions from AlphaFold3 and CASTpFold without any experimental validation. The claim that K31X mutations "enlarge the DNA binding pocket" is based on predicted structures, but no experimental evidence such as binding affinity measurements, crystallography, or hydrogen-deuterium exchange is provided. The relationship between pocket size and catalytic activity is assumed but not demonstrated. The authors acknowledge AlphaFold's limitations in predicting mutational effects but do not provide any experimental data to support their specific mechanistic claims.
- **Why it matters** The rational design component of the integrated approach depends on the validity of the structural predictions. If the mechanistic explanation is incorrect, the generalizability of the approach to other deaminases is questionable. The field has seen numerous cases where computational predictions of mutational effects do not hold up experimentally, and the authors should provide direct evidence for their proposed mechanism.
- **Resolution test** Provide experimental validation of the proposed mechanism, such as binding affinity measurements of K31X variants to ssDNA, circular dichroism or other biophysical characterization of structural changes, or site-directed mutagenesis of the predicted gatekeeper residues with functional assays. Alternatively, provide a more cautious interpretation that acknowledges the speculative nature of the structural predictions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Comparative analysis
- **Claim summary** The authors claim that optimized SsdAtox variants outperform BE4max at multiple endogenous targets.
- **Evidence pointer** Results section "Combination and Evaluation of SsdA5mix Variants", Figure 5
- **Concern** The comparison with BE4max is limited to a small number of endogenous targets (10), and the criteria for target selection are not described. The manuscript reports that SsdA5mix variants show "comparable or superior performance" to BE4max, but the specific targets where superiority is claimed are not identified. The statistical significance of the differences is not reported for individual targets. The comparison is further complicated by the use of different delivery methods or expression systems, which is not clearly described.
- **Why it matters** The claim of outperforming BE4max is a key selling point of the engineered variants. A limited comparison on a small number of potentially selected targets does not provide sufficient evidence for general superiority. The field has learned that base editor performance is highly context-dependent, and claims of superiority require testing across a diverse panel of targets with appropriate statistical power.
- **Resolution test** Provide a comprehensive comparison across a larger panel of endogenous targets with diverse sequence contexts. Report individual target data with statistical analyses. Describe the criteria for target selection and ensure they are not biased toward the SsdAtox variants. Include a power analysis to justify the number of targets tested. Consider testing in multiple cell types to assess generalizability.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim summary** The authors describe a complete protocol for Trinity-Screen and the computational pipeline for variant identification.
- **Evidence pointer** Methods section "Trinity-Screen", "Hit Identification and Site Saturation Mutagenesis"
- **Concern** The methods section lacks critical details necessary for replication. The selection stringency and timing for each round of Trinity-Screen are not specified. The criteria for identifying "surviving colonies" and the number of colonies screened per round are not reported. The computational pipeline for analyzing NGS data to identify enriched variants is described only at a high level. The threshold for considering a mutation "beneficial" is not defined. The methods for combinatorial library construction and the number of variants tested are not provided.
- **Why it matters** Reproducibility is a fundamental requirement for scientific publication. The described platform is a major methodological contribution, and other laboratories should be able to implement it based on the manuscript. The lack of procedural detail undermines the utility of the work and prevents independent validation.
- **Resolution test** Provide a detailed step-by-step protocol for Trinity-Screen, including selection timing, antibiotic concentrations, colony numbers, and passaging conditions. Describe the NGS analysis pipeline with specific software versions and parameters. Report the number of colonies screened and the criteria for variant selection. Provide details on combinatorial library construction, including the number of variants and the method for generating combinations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "ten-fold higher activity" and "ten-fold lower cytotoxicity" without specifying the comparison basis or the assay conditions. The term "ten-fold" appears multiple times with different meanings, which could confuse readers.
- **Required correction** Specify the comparison basis for each fold-change claim and ensure consistent use of terminology. Consider providing a brief description of the assay conditions in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section
- **Evidence pointer** Results section "Combination and Evaluation of SsdA5mix Variants"
- **Issue** The manuscript mentions statistical analysis using Welch's t-test and ANOVA but does not report specific p-values, effect sizes, or confidence intervals for the key comparisons. The statement "differences were not statistically significant at all targets" is vague.
- **Required correction** Report specific p-values for all key comparisons, including corrections for multiple testing where appropriate. Provide effect sizes and confidence intervals. Clearly indicate which comparisons reached statistical significance.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Introduction and Results
- **Evidence pointer** Introduction, Results section "Combination and Evaluation of SsdA5mix Variants"
- **Issue** The term "specificity" is used in multiple contexts without clear definition. The manuscript discusses "editing specificity" in terms of window position, but also references "specificity" in the context of off-target effects. The relationship between these uses is not clarified.
- **Required correction** Define "specificity" explicitly in each context where it is used. Consider using more precise terms such as "window specificity" or "off-target specificity" to avoid ambiguity.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results section "Combination and Evaluation of SsdA5mix Variants"
- **Evidence pointer** Results section, Figure 5
- **Issue** The manuscript reports that SsdA5mix variants show "comparable or superior performance" to BE4max, but the specific targets where superiority is claimed are not identified. The reader cannot determine which targets favor which editor.
- **Required correction** Provide a table listing each endogenous target with the corresponding editing efficiency, indel rate, and BEPI for each variant tested. Highlight the targets where SsdA5mix outperforms BE4max.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction
- **Issue** The introduction mentions previous efforts to engineer SsdAtox but does not provide specific citations or a detailed comparison with those efforts. The claim that this is the "first validated instance" of AlphaFold3-guided alanine scanning leading to a gain-of-function design in a genome-editing enzyme requires more careful contextualization.
- **Required correction** Provide a more detailed review of previous SsdAtox engineering efforts, including specific mutations and their reported performance. Discuss how the current approach differs from and improves upon these efforts. Soften the "first" claim or provide a comprehensive literature search to support it.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability Statement
- **Evidence pointer** Data Availability Statement
- **Issue** The data availability statement mentions submission to NCBI SRA under accession PRJNA1203172, but the accession is not yet active or verifiable. The statement also mentions "Supplemental Dataset 1" without describing its contents.
- **Required correction** Provide the accession number and confirm that the data will be publicly available upon publication. Describe the contents of Supplemental Dataset 1 in the data availability statement or in a supplementary information file.

## Risk / unsupported claims
- The claim that optimized SsdAtox variants outperform BE4max is not fully supported by the provided evidence, as the comparison is limited to a small number of targets and the statistical significance of differences is not reported for individual targets.
- The claim that K31X mutations "enlarge the DNA binding pocket" is based solely on computational predictions without experimental validation.
- The claim that Trinity-Screen simultaneously selects for three independent traits is not supported by validation experiments demonstrating the independence and specificity of each selection axis.
- The claim that this is the "first validated instance" of AlphaFold3-guided alanine scanning leading to a gain-of-function design in a genome-editing enzyme is not supported by a comprehensive literature search.
- The mechanistic explanation for the reduced indel formation in 5mix variants, involving "cooperative optimization" and "pocket remodeling," is speculative and not directly tested.
- The generalizability of the approach to other deaminases is claimed but not demonstrated experimentally.
- The BEPI metric is presented as a standardized tool, but its properties and advantages over existing metrics are not rigorously validated.