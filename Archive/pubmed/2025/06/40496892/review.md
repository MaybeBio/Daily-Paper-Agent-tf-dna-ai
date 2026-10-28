## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, limitations, conclusion, and methods sections
- **Assessment boundary** Scientific validity, methodological rigor, claims versus evidence, and significance of the comparative analysis of AlphaFold 2 predictions against experimental nuclear receptor structures
- **Shared manuscript claim summary** The authors present the first comprehensive comparison of AlphaFold 2-predicted full-length nuclear receptor structures against all available experimental structures, reporting domain-specific variations in RMSD, systematic overestimation of α-helical content, underestimation of ligand-binding pocket volumes, and failure to capture asymmetric conformational states in homodimeric receptors
- **Visible evidence base** RMSD calculations across three atom selections, secondary structure element content analysis, domain geometry measurements (distances, angles, dihedrals), ligand-binding pocket volume and sphericity calculations, RSCC versus pLDDT comparisons, Ramachandran plot statistics, and MolProbity validation metrics
- **Missing materials affecting confidence** Supplementary data files (MMC 1-6) not provided; statistical analysis details incomplete; no access to raw structural alignment parameters; no code or scripts for reproducibility; figure quality and full data points not assessable

## Reviewer
- **Overall assessment** This manuscript addresses a timely and relevant question regarding the reliability of AlphaFold 2 predictions for a pharmaceutically important protein family. The authors have assembled a valuable dataset of all available full-length nuclear receptor structures and applied multiple complementary metrics to evaluate prediction accuracy. The finding that AF2 systematically underestimates ligand-binding pocket volumes and fails to capture asymmetric homodimeric states is potentially important for structure-based drug design. However, the manuscript suffers from several significant weaknesses that currently prevent the conclusions from being fully established. The statistical framework is underdeveloped, with key analyses lacking appropriate methodological detail. The sample size of seven receptors is small, and the authors do not adequately address how representative this set is of the broader nuclear receptor family. The comparison between RSCC and pLDDT values, while conceptually interesting, requires more rigorous treatment given that these metrics measure fundamentally different properties. The discussion is overly speculative in places, extending beyond what the data can support. The manuscript would benefit from clearer presentation of the statistical methods, more careful interpretation of the domain geometry results, and a more balanced treatment of AF2's known capabilities and limitations.

- **Who would be interested in the results, and why** Structural biologists studying nuclear receptors will find the comparative analysis useful for understanding when experimental structure determination remains necessary. Computational biologists developing or benchmarking protein structure prediction methods will be interested in the domain-specific performance metrics. Researchers in structure-based drug design targeting nuclear receptors will value the documentation of systematic pocket volume underestimation, which has direct implications for virtual screening and ligand docking studies. The framework established for evaluating multi-domain protein predictions could also be of interest to the broader protein structure prediction community.

- **Major strengths** The manuscript addresses an important gap in the literature by providing a systematic evaluation of AF2 predictions specifically for full-length multi-domain nuclear receptors, rather than individual domains. The multi-metric approach, combining RMSD, secondary structure content, domain geometry, pocket properties, and validation scores, provides a more comprehensive assessment than single-metric studies. The inclusion of all available experimental structures as of the stated date represents a thorough literature search. The authors make an appropriate methodological choice to analyze raw AF2 predictions without additional refinement, which provides an unbiased assessment of the standard prediction pipeline. The discussion of limitations and future directions, particularly regarding newer models like AF3, is thoughtful and forward-looking.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims statistically significant differences between DBD and LBD variability (mean difference = -0.070 Å, t = -1.988, p < 0.05, Cohen's d = 0.574) and significant differences between receptors in pocket properties (Kruskal-Wallis H = 32.145 and 27.893)
- **Evidence pointer** Results sections "Root-mean-square deviation of the structures" and "Analysis of ligand-binding pocket geometry"; location not provided
- **Concern** The statistical methods are inadequately described. The authors report p-values and test statistics but do not specify the exact tests used, the assumptions checked, or how multiple comparisons were handled. For the RMSD comparison, a paired t-test is mentioned in the methods, but it is unclear whether the data meet the normality assumptions required. The Kruskal-Wallis tests for pocket properties are reported with H values but no degrees of freedom or post-hoc analyses. More critically, the sample size is very small (seven receptors, with varying numbers of experimental structures per receptor), and the authors do not report effect sizes with confidence intervals or perform power analyses. The claim of "significant" differences requires more robust statistical support.
- **Why it matters** The central conclusions of the manuscript rest on claims of statistically significant differences between domains and between receptors. If the statistical framework is inadequate, these conclusions cannot be considered reliable. The small sample size and potential violations of test assumptions could lead to both false positives and false negatives.
- **Resolution test** Provide complete details of all statistical tests including test names, assumptions verified, degrees of freedom, exact p-values, and effect sizes with confidence intervals. Report how multiple testing was addressed. Consider whether the sample size is sufficient for the claims made, and if not, temper the conclusions accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that "AlphaFold 2 systematically underestimates ligand-binding pocket volumes" and that AF2 "captures only single conformational states in homodimeric receptors where experimental structures show functionally important asymmetry"
- **Evidence pointer** Results sections "Analysis of ligand-binding pocket geometry" and "Geometric analysis of domain architecture"; Figures 2 and 3; location not provided
- **Concern** The evidence presented does not fully support the strength of these claims. For pocket volume underestimation, the data show variable results across receptors, with some receptors showing close agreement and others showing large discrepancies. The claim of "systematic" underestimation requires a more rigorous quantitative analysis, including statistical testing across all receptors and consideration of whether the differences correlate with receptor-specific features. For the homodimer asymmetry claim, the analysis is based on only two receptors (GR and HNF4α), and the authors do not adequately address whether the observed asymmetry in experimental structures represents functionally relevant states or crystallization artifacts. The claim that AF2 captures "only single conformational states" is based on comparison with a limited number of experimental structures that may themselves not represent the full conformational landscape.
- **Why it matters** These are the two most significant and potentially impactful findings of the manuscript. If they are not supported by sufficient evidence, the manuscript's contribution is substantially diminished. Overstating conclusions based on limited data could mislead researchers using AF2 predictions for drug design.
- **Resolution test** Provide quantitative analysis of pocket volume differences across all receptors with appropriate statistical testing. For the homodimer asymmetry claim, either expand the analysis to include more receptors or temper the claim to reflect the limited evidence. Discuss alternative explanations for observed differences, including crystallization conditions, construct boundaries, and the presence or absence of ligands and cofactors.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological transparency
- **Claim pointer** The manuscript describes a "comprehensive analysis" using multiple metrics including RMSD, secondary structure elements, domain geometry, and pocket properties
- **Evidence pointer** Materials and methods section; location not provided
- **Concern** The methods section is extremely brief and lacks critical details needed for reproducibility. The authors state that "all geometrical measurements and analysis have been done in PyMOL v2.4.2 using internal commands or python scripts" but do not provide the scripts, parameters, or detailed protocols. For the RMSD calculations, it is unclear how the structural alignment was performed, which atoms were included, and how the domains were defined. The secondary structure analysis does not specify which algorithm was used for assignment. The pocket detection method using hollow 1.3 is mentioned but parameters are not given. The comparison of RSCC and pLDDT values requires more detail on how these were calculated and normalized. Without these details, the analyses cannot be reproduced or verified.
- **Why it matters** Reproducibility is a fundamental requirement for scientific manuscripts. The lack of methodological detail prevents other researchers from replicating the analysis or applying the framework to other protein families, which the authors suggest as a contribution of the work.
- **Resolution test** Expand the methods section to include all parameters, scripts, and analysis protocols. Consider depositing analysis scripts in a public repository. Provide clear definitions of domain boundaries and the criteria used for structural alignment.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation and contextualization
- **Claim pointer** The manuscript states that "AlphaFold 2 has revolutionized protein structure prediction, yet systematic evaluations of its performance against experimental structures for specific protein families remain limited" and positions this work as the "first comprehensive analysis" for nuclear receptors
- **Evidence pointer** Abstract and Introduction; location not provided
- **Concern** The manuscript does not adequately engage with the existing literature on AF2 evaluation. Numerous studies have benchmarked AF2 against experimental structures across various protein families, including nuclear receptors. The claim of being "first" requires a more thorough literature search and explicit statement of what makes this analysis unique. Additionally, the authors do not discuss known limitations of AF2 that have been documented in previous studies, such as its performance on multi-domain proteins, conformational ensembles, and ligand-bound states. The discussion would benefit from more direct comparison with previous benchmarking efforts to contextualize the findings.
- **Why it matters** The novelty claim is central to the manuscript's contribution. If similar analyses have been published, the authors need to clearly differentiate their work. Contextualizing findings within the broader AF2 evaluation literature would strengthen the manuscript and help readers understand the significance of the results.
- **Resolution test** Conduct a more comprehensive literature review and explicitly state what is novel about this analysis compared to previous AF2 benchmarking studies. Discuss how the findings align with or contradict previous observations about AF2 performance on multi-domain proteins.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1 and associated text
- **Evidence pointer** Results section "Root-mean-square deviation of the structures"; location not provided
- **Issue** The description of Figure 1 is confusing. The text states that "The columns are overlaid, and different color hues represent the conditions used to calculate RMSD," but it is unclear what "overlaid" means in this context and how the three RMSD metrics are distinguished visually. The figure legend is not provided in the manuscript text.
- **Required correction** Clarify the figure presentation in the text and ensure the figure legend clearly explains the color coding and column arrangement. Consider whether a different visualization approach would more clearly convey the RMSD values across receptors and domains.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout the manuscript
- **Evidence pointer** Multiple sections; location not provided
- **Issue** The manuscript uses "AlphaFold 2," "AlphaFold," and "AF2" interchangeably. While this is common in the literature, consistency would improve readability. Additionally, the term "full-length" is used to describe the nuclear receptor structures, but the definition of full-length in this context is not explicitly stated.
- **Required correction** Standardize the terminology throughout the manuscript. Define what is meant by "full-length" nuclear receptor structures, particularly in the context of the experimental structures that may contain flexible regions or missing residues.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Table 3
- **Evidence pointer** Results section "Summary of metrics"; location not provided
- **Issue** Table 3 provides a qualitative summary of the findings but does not include quantitative values or statistical measures. This makes it difficult for readers to assess the magnitude of the reported differences.
- **Required correction** Consider adding quantitative values to Table 3, such as mean RMSD values, correlation coefficients, or p-values, to provide a more informative summary.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion and Limitations sections; location not provided
- **Issue** The manuscript discusses limitations of AF2 but does not adequately address limitations of the experimental structures used as comparators. Crystal structures can be influenced by crystal packing, construct design, and crystallization conditions, which may affect the comparison.
- **Required correction** Add a discussion of potential biases in the experimental structures and how these might affect the comparison with AF2 predictions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Reference to supplementary data
- **Affected element** Supplementary materials
- **Evidence pointer** Supplementary material section; location not provided
- **Issue** The supplementary data files are listed but their contents are not described in the text. Readers cannot determine what analyses are included in each file.
- **Required correction** Add brief descriptions of the contents of each supplementary file in the main text or in the supplementary material section.

- **Technical failings that need to be addressed before the case is established**
1. Inadequate statistical methodology description, including unspecified tests, unverified assumptions, and lack of multiple comparison corrections (R1-M1)
2. Insufficient evidence for the strong claims of "systematic" pocket volume underestimation and failure to capture asymmetric states (R1-M2)
3. Lack of methodological detail preventing reproducibility of the analyses (R1-M3)
4. Incomplete engagement with existing AF2 benchmarking literature, weakening the novelty claim (R1-M4)

- **Assessment against Nature-style criteria**
  - **Originality**: The manuscript addresses a relevant question, but the claim of being the "first comprehensive analysis" for nuclear receptors requires more careful verification against existing literature. The multi-metric approach has some novelty, though individual metrics have been used in previous studies.
  - **Scientific importance**: The findings have potential importance for researchers using AF2 predictions for nuclear receptor drug design. The documentation of pocket volume underestimation and failure to capture asymmetric states could influence how computational predictions are used in this field. However, the small sample size and limited statistical support reduce the confidence in these findings.
  - **Interdisciplinary readership**: The manuscript would primarily interest structural biologists, computational biologists, and researchers in drug discovery. The broader readership interest is limited by the narrow focus on nuclear receptors and the technical nature of the analysis.
  - **Technical soundness**: The technical approach is generally sound in concept, but the execution has significant weaknesses. The statistical analysis is underpowered and inadequately described. The comparison of RSCC and pLDDT values, while interesting, requires more careful treatment given the different nature of these metrics. The lack of methodological detail prevents verification of the results.
  - **Readability for nonspecialists**: The manuscript is written in a technical style that would be challenging for nonspecialists. The introduction provides some context, but the results section assumes significant background knowledge in structural biology and protein structure prediction. The discussion of limitations is thoughtful but could be more accessible.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript addresses an important question and has assembled a valuable dataset, but the statistical weaknesses and insufficient evidence for the central claims prevent the conclusions from being fully supported. The authors should be encouraged to revise the manuscript with more rigorous statistical analysis, expanded methodological detail, and more measured claims that accurately reflect the evidence. If these concerns are addressed, the manuscript could make a useful contribution to the field.