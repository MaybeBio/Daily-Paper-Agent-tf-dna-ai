## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and conclusion
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and interpretation of findings as presented in the provided manuscript
- **Shared manuscript claim summary** The authors present a computational pipeline integrating evolutionary genomics, structural biology, and clinical variant analysis to prioritize functionally critical residues in TP53. They identify codon 129 as a consensus positive-selection site and residues 239-248 as the primary pathogenic hotspot, validated through LOOCV-based ensemble machine learning.
- **Visible evidence base** Abstract, full methods section, results section with figures and tables referenced, discussion, and conclusion
- **Missing materials affecting confidence** Figures and tables referenced in the text (Figures 1-10, Tables 1-11) were not provided; supplementary data, code availability, and detailed model hyperparameters were not included

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful integrative framework for TP53 residue prioritization, combining evolutionary selection analysis, clinical variant mapping, and machine learning. However, several critical methodological issues and overstatements undermine the strength of the conclusions. The evolutionary analysis relies on a small and phylogenetically biased sample, the machine learning tasks appear somewhat disconnected from the biological claims, and the composite scoring system involves arbitrary weight choices that are not adequately justified. The identification of codon 129 as a positive-selection site is interesting but requires more rigorous validation, particularly given the known functional importance of this region. The manuscript would benefit from clearer articulation of what is genuinely novel versus confirmatory of existing TP53 knowledge.
- **Who would be interested in the results, and why** Researchers in cancer genomics, TP53 biology, and evolutionary medicine would find the integrative approach of interest. Those working on variant prioritization and functional annotation of cancer genes may appreciate the framework. However, the incremental advance over existing TP53 knowledge is modest, and the machine learning component does not clearly connect to the biological findings.
- **Major strengths** The integration of multiple data types (evolutionary, structural, clinical) into a single framework is conceptually appealing. The use of LOOCV for model evaluation is appropriate given the small sample size. The authors acknowledge limitations regarding sample size and phylogenetic bias. The composite scoring approach, while arbitrary in its weights, does provide a transparent and reproducible method for ranking residues.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: Moderate. The integration of methods is somewhat novel, but the individual components are well-established. Scientific importance: Limited. The findings largely confirm known TP53 biology (hotspot mutations in the DNA-binding domain) with modest new insights. Interdisciplinary readership: The work spans evolutionary biology, structural biology, and clinical genomics, which could appeal to multiple communities, but the technical depth in each area is limited. Technical soundness: Several concerns as detailed below. Readability for nonspecialists: The manuscript is generally readable but contains some awkward phrasing and unclear transitions.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires substantial revisions to address methodological concerns and to more carefully calibrate the claims relative to what is actually demonstrated.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim that codon 129 is a "robust positive-selection site" based on consensus detection by both FEL and FUBAR.
- **Evidence pointer** Methods section, "Bioinformatics and evolutionary analysis"; Results section, "Evolutionary constraint, site-specific selection, and structural context"; Figure 2
- **Concern** The identification of a single consensus positive-selection site from a 19-species alignment, with 11 of 19 being mammals, provides very limited statistical power. FEL and FUBAR are known to have high false-positive rates on small alignments, and the authors do not report multiple testing corrections, site-specific p-value distributions, or sensitivity analyses with different species subsets. The claim of "robust" detection is not supported by the evidence presented.
- **Why it matters** The central biological claim of the paper rests on this positive-selection signal. If the signal is not statistically robust, the entire narrative about evolutionary convergence with clinical pathogenicity is weakened.
- **Resolution test** Provide multiple testing corrections (e.g., FDR), report the distribution of p-values across all sites, perform sensitivity analyses excluding individual lineages (especially non-mammals), and consider additional methods (e.g., MEME, SLAC) to confirm the signal. If the signal is not robust to these analyses, the claim should be substantially softened.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological justification
- **Claim pointer** The composite scoring system integrates four components with weights of 45%, 30%, 15%, and 10% for selection, pathogenic burden, hotspot enrichment, and domain context, respectively.
- **Evidence pointer** Methods section, "Bioinformatics and evolutionary analysis"; Results section, "Composite prioritization of functionally critical residues"; Equation 7
- **Concern** The weights assigned to the four scoring components are presented as "empirically optimized" but no optimization procedure is described. The authors state that "sensitivity analyses (not shown) indicated that the top-ranked residues remained stable," but these analyses are not presented. Without a clear justification for the weights or evidence of their robustness, the composite score is essentially arbitrary.
- **Why it matters** The composite score is used to identify residues 239-248 as the "primary pathogenic hotspot." If the weights are arbitrary, the ranking may not be reproducible or meaningful, and the central prioritization claim is undermined.
- **Resolution test** Describe the weight optimization procedure in detail, or present the sensitivity analyses in full. Alternatively, provide a rationale for the weights based on prior literature or theoretical considerations. Show that the top-ranked residues are stable across a range of plausible weight combinations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Relevance of machine learning
- **Claim pointer** The machine learning models "validate" the evolutionary and clinical features, with the ensemble achieving MAE = 2.41, RMSE = 3.72, R² = 0.91 for distance regression and 89.5% accuracy for clade classification.
- **Evidence pointer** Methods section, "Artificial intelligence and machine learning framework"; Results section, "Machine learning validation"; Figures 8-9; Tables 4-6, 10
- **Concern** The machine learning tasks (predicting phylogenetic distance and classifying clades) are not clearly connected to the biological claims about residue prioritization. Demonstrating that sequence features can predict phylogenetic distance does not validate the identification of functionally critical residues. The connection between "predictive accuracy" and "biological validity" is asserted but not logically established. Furthermore, with only 19 samples, the LOOCV results are highly sensitive to individual data points, and the reported performance metrics may not be stable.
- **Why it matters** The manuscript presents the machine learning as a key validation component, but if the tasks are not relevant to the biological question, this validation is meaningless. The reader is left wondering what exactly the machine learning adds to the evolutionary and clinical analyses.
- **Resolution test** Reframe the machine learning as a separate exploratory analysis rather than a validation of the biological findings, or design tasks that directly test the predictive power of the prioritized residues (e.g., predicting pathogenicity of unseen variants). Report confidence intervals for performance metrics and discuss the stability of LOOCV results with 19 samples.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Data quality and variant classification
- **Claim pointer** The authors state they integrated 3936 human variants from ClinVar and UniProt, classifying them as pathogenic, likely pathogenic, benign, likely benign, or uncertain.
- **Evidence pointer** Methods section, "Clinical variant distribution and hotspot mapping"; Results section, "Clinical variant distribution and hotspot mapping"; Table 8
- **Concern** The manuscript does not describe how variants were filtered, how conflicting classifications were resolved, or how the "pathogenic" category was defined for the analysis. ClinVar contains many variants with conflicting or outdated classifications, and the authors do not specify whether they used only reviewed entries or applied any quality filters. The count of 3936 variants seems low for TP53, which is one of the most extensively characterized genes in cancer genomics.
- **Why it matters** The pathogenic burden component of the composite score depends entirely on the accuracy and completeness of the variant classification. If the variant data are not carefully curated, the prioritization results may be biased or incorrect.
- **Resolution test** Describe the variant curation process in detail, including inclusion/exclusion criteria, handling of conflicting classifications, and any quality filters applied. Compare the variant counts and distribution with published TP53 databases (e.g., IARC TP53 Database) to demonstrate completeness.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors claim the pipeline is "fully reproducible" and "fully scripted."
- **Evidence pointer** Methods section throughout; Data availability section
- **Concern** The manuscript does not provide a link to code, a repository, or a detailed description of software versions and parameters. The data availability statement says data "will be made available upon reasonable request," which is not consistent with a claim of full reproducibility. Key parameters for PRANK, IQ-TREE, HyPhy, and the machine learning models are not fully specified.
- **Why it matters** Reproducibility is a core requirement for computational biology papers. Without access to the code and data, other researchers cannot verify the results or apply the framework to other genes.
- **Resolution test** Provide a public repository with all code, configuration files, and processed data. Specify all software versions and parameters in the methods. Make the raw data available through a public repository rather than "upon reasonable request."

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The sentence "TP53 encodes a master tumor suppressor, and understanding its evolutionary constraints is critical for interpreting pathogenic variation" is grammatically awkward and could be more concise.
- **Required correction** Revise to something like "TP53 encodes a master tumor suppressor whose evolutionary constraints are critical for interpreting pathogenic variation."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section
- **Evidence pointer** Methods, "Bioinformatics and evolutionary analysis"
- **Issue** The manuscript mentions that PRANK was run for five iterations and the first iteration gave the best score, but it is unclear why the first iteration would be best and whether this is a standard practice or a post-hoc selection.
- **Required correction** Clarify whether selecting the first iteration was pre-specified or based on the score, and discuss any potential bias introduced by this selection.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section
- **Evidence pointer** Results, "Machine learning validation"; Table 10
- **Issue** The manuscript reports R² = 0.91 for the regression task but does not report confidence intervals or standard errors for any performance metrics. With 19 samples, these metrics are likely to have wide uncertainty.
- **Required correction** Report confidence intervals for all performance metrics and discuss the uncertainty associated with the small sample size.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion, first paragraph
- **Issue** The statement "Codon 129 emerges as the sole site under positive selection" is presented as a key finding, but the authors do not discuss the biological plausibility of positive selection at this position given its known functional importance in DNA binding.
- **Required correction** Add a discussion of what positive selection at codon 129 might mean biologically, and consider whether this could reflect lineage-specific adaptation or relaxed constraint in certain lineages.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction, first paragraph
- **Issue** The introduction does not adequately situate this work relative to existing TP53 evolutionary analyses and variant prioritization tools. Several well-known studies have examined TP53 evolution and function.
- **Required correction** Add citations to key prior work on TP53 evolution, variant prioritization, and machine learning approaches for functional annotation.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figures 1-10
- **Evidence pointer** Figures referenced throughout
- **Issue** The figures were not provided for review, so their quality and informativeness cannot be assessed.
- **Required correction** Ensure all figures are high-resolution, clearly labeled, and self-contained with appropriate legends.

## Risk / unsupported claims
- The claim that codon 129 is a "robust positive-selection site" is not adequately supported given the small, phylogenetically biased sample and lack of multiple testing corrections.
- The claim that the machine learning models "validate" the biological findings is not logically established, as the ML tasks are not directly connected to residue prioritization.
- The composite scoring system is presented as "empirically optimized" but no optimization procedure is described, making the weights appear arbitrary.
- The claim of "full reproducibility" is not supported by the data availability statement, which says data will be made available "upon reasonable request."
- The statement that residues 239-248 constitute the "primary pathogenic hotspot" is largely confirmatory of well-established TP53 biology and does not represent a novel finding.
- The claim that the framework "may contribute to precision oncology" is speculative and not supported by any clinical validation data.