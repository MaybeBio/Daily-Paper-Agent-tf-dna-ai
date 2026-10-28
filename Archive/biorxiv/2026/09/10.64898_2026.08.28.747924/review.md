## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions, supplementary figure/table legends)
- **Assessment boundary** Scientific soundness, methodological rigor, support of claims by evidence, and suitability for a high-impact generalist journal
- **Shared manuscript claim summary** The authors identify ABF2 and bZIP2 as interacting bZIP transcription factors that integrate phosphate deficiency and salinity signals to remodel root system architecture in Arabidopsis, based on meta-analysis of public transcriptomes, network inference, AlphaFold-Multimer predictions, and mutant phenotyping
- **Visible evidence base** Abstract, full introduction, full methods, full results, full discussion, conclusions, supplementary figure/table legends, author contributions, funding, data availability
- **Missing materials affecting confidence** Main-text figures and figure legends (Figures 1-5 referenced but not provided), supplementary figures S1-S11 and tables S1-S6 (referenced but not provided), exact statistical outputs beyond p-values, raw data files, DAP-seq binding site coordinates, AlphaFold-Multimer model quality metrics beyond iLIS/ipTM

## Reviewer
- **Overall assessment** This manuscript presents a potentially valuable integrative pipeline for identifying transcription factors involved in combined stress responses, and the identification of ABF2 and bZIP2 as candidate regulators of root architecture under combined phosphate deficiency and salinity is of interest. However, the evidence as presented is incomplete. The central claims regarding dimerization, target gene regulation, and the mechanistic model rest heavily on computational predictions and on figures and supplementary materials that were not available for review. The phenotypic data, while suggestive of additive or synergistic effects, are presented only as summary statistics without the underlying figures. The manuscript would benefit from clearer presentation of the experimental design, particularly the rationale for the chosen stress conditions and the exclusion of single-stress phenotyping arms, which the authors acknowledge as a limitation. The novelty of the findings relative to existing literature on ABF2 and bZIP2 in stress responses is not fully established. Overall, the work has potential but the case is not fully established from the provided materials.

- **Who would be interested in the results, and why** Plant molecular biologists studying root development, abiotic stress signaling, and transcription factor networks would be interested. Researchers working on phosphate starvation responses and salt stress signaling, particularly those interested in the intersection of these pathways, would find the integrative approach and the identification of a potential regulatory hub valuable. The work may also appeal to those interested in using public data mining and structural prediction to prioritize candidate genes for functional studies. The potential translational relevance for breeding stress-resilient crops could attract applied plant scientists.

- **Major strengths** The integrative approach combining meta-analysis, network inference, structural prediction, and mutant phenotyping is ambitious and potentially powerful. The use of DAP-seq evidence to filter network interactions adds confidence. The recovery of known stress regulators provides internal validation. The identification of a trichoblast-expressed target (AT3G03790) provides a plausible molecular link to root hair phenotypes. The authors are transparent about limitations, including the lack of single-stress phenotyping arms and the computational nature of interaction predictions.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that ABF2 and bZIP2 "act in an additive or synergistic manner to sustain not only macroscopic root branching but also the critical absolute elongation of root hairs required for acclimation to combined nutrient deprivation and osmotic stress"
- **Evidence pointer** Results section, Figure 5 (not provided), Supplementary Figures S6-S10 (not provided)
- **Concern** The central phenotypic claims are based on figures and supplementary materials that were not provided for review. The text provides some quantitative values (e.g., 22.8% reduction in primary root length, 53% reduction in lateral root number, root hair lengths of 312 vs. 371 µm and 57 vs. 108 µm), but without the actual figures, statistical plots, or full data tables, the robustness of these effects cannot be assessed. The claim of additivity or synergy requires comparison of single mutants under combined stress and ideally double mutants under single stresses, which the authors acknowledge was not performed. The statistical analysis (two-way ANOVA with genotype × treatment) is described, but the full output, including interaction terms, is not presented.
- **Why it matters** The phenotypic validation is the core experimental evidence supporting the functional role of ABF2 and bZIP2. Without the full data presentation, the reader cannot evaluate the magnitude, consistency, or statistical robustness of the reported effects. The claim of additivity or synergy is a strong one that requires specific experimental designs to support.
- **Resolution test** Provide the main-text figures with full statistical annotations, including individual data points, effect sizes, confidence intervals, and the results of the two-way ANOVA interaction terms. Include the single-stress phenotyping data or explicitly reframe the claims to avoid the term "synergistic" if such data are not available.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The manuscript claims that "ABF2 and bZIP2 form a mutually interacting, combinatorial regulatory module" and that "distinct dimeric configurations preferentially orchestrate specific targets: AT3G03790 is uniquely regulated by the ABF2 homodimer, ACR8 (AT1G12420) is governed by the bZIP2 homodimer, and HSP70 (AT4G16660) is under the strict combinatorial control of the ABF2/bZIP2 heterodimer"
- **Evidence pointer** Results section, Figure 3 (not provided), Figure 4 (not provided), Supplementary Table S4 (not provided), Supplementary Table S6 (not provided)
- **Concern** The claim of a specific dimerization module and dimer-specific target regulation rests on AlphaFold-Multimer predictions and a computational motif-spacing analysis. The AlphaFold-Multimer results are presented as iLIS and ipTM scores, but the full scoring table (Supplementary Table S4) is not available. The threshold of iLIS ≥ 0.551 is described as "stringent" and "internally calibrated," but the basis for this calibration is not fully explained. The motif-spacing analysis uses a 3-10 bp separation threshold, but the text states "[insert exact threshold, e.g., 3-10 bp]" and "[insert exact window, e.g., 1000 bp]" in the methods, indicating incomplete editing. The assignment of specific targets to specific dimer configurations appears to be based on this computational analysis alone, with no experimental validation (e.g., ChIP-seq, EMSA, or reporter assays) presented.
- **Why it matters** The dimer-specific regulatory model is a central mechanistic claim of the manuscript. If the computational predictions are not robustly supported or experimentally validated, the model remains speculative. The incomplete methods text undermines confidence in the rigor of the analysis.
- **Resolution test** Provide the complete methods text with exact parameters. Present the full AlphaFold-Multimer scoring table and the distribution of scores to justify the threshold. Provide experimental validation of at least one predicted dimer-specific target (e.g., EMSA, ChIP-qPCR, or transactivation assays). Alternatively, soften the claims to reflect that these are predictions requiring experimental testing.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and context
- **Claim pointer** The manuscript claims to provide "one of the few comprehensive analyses of how multiple abiotic stressors jointly shape root development and plant fitness" and "the first mechanistic evidence for how these novel TF complexes govern RSA remodeling under the combined constraints of combined low-phosphate and salt stress"
- **Evidence pointer** Introduction, Discussion
- **Concern** The novelty claim is not fully contextualized. The authors cite Ibeas et al. (2024) as a prior comprehensive treatment of combined stress in root hairs, but the relationship between that work and the present study is not clearly delineated. ABF2 is a well-known ABA-responsive transcription factor, and bZIP2 has been studied in stress contexts. The specific claim of novelty for the ABF2-bZIP2 interaction and its role in combined stress needs to be positioned more carefully against existing literature on bZIP dimerization and stress responses. The statement "first mechanistic evidence" is strong and requires a thorough literature search to support.
- **Why it matters** For a high-impact journal, the novelty and significance of the findings must be clearly established. Overclaiming novelty without adequate contextualization can undermine the credibility of the work.
- **Resolution test** Expand the introduction and discussion to more thoroughly review existing literature on ABF2, bZIP2, their homologs, and bZIP dimerization in stress responses. Clearly state what is known and what is genuinely new. Adjust the novelty claims to be more precise and defensible.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The manuscript describes a meta-analysis of public transcriptomic datasets and states that "approximately 45-54% of sDEGs were shared between the two stresses, comprising 2,185 commonly up-regulated and 2,308 commonly down-regulated genes"
- **Evidence pointer** Methods, Results, Figure 2 (not provided), Supplementary Figure S1 (not provided)
- **Concern** The meta-analysis methodology is described at a high level, but key details are missing. The criteria for dataset inclusion and exclusion are described, but the specific number of datasets excluded at each step and the reasons are not quantified. The integration method using Monte Carlo simulation is mentioned, but the statistical details are not fully specified. The statement that 45-54% of sDEGs are shared is presented without confidence intervals or a clear definition of what constitutes "shared" (e.g., same direction of change, similar magnitude). The figure showing this overlap (Figure 2C) is not provided.
- **Why it matters** The meta-analysis is the foundation of the entire study. If the methodology is not transparent and reproducible, the identification of candidate TFs is not trustworthy. The reader cannot assess the robustness of the overlap claim without seeing the underlying data and analysis.
- **Resolution test** Provide a more detailed methods section for the meta-analysis, including the full list of datasets, the filtering criteria with counts at each step, and the statistical details of the Monte Carlo integration. Present the overlap analysis with appropriate statistical measures (e.g., odds ratios, confidence intervals). Make the code and data publicly available.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, Promoter motif-spacing analysis
- **Evidence pointer** Methods section, "Promoter motif-spacing analysis"
- **Issue** The methods text contains placeholder text: "[insert exact window, e.g., 1000 bp]" and "[insert exact threshold, e.g., 3-10 bp]". This indicates incomplete editing and prevents the reader from understanding the exact parameters used.
- **Required correction** Replace the placeholder text with the exact values used in the analysis.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, Measurement of RSA traits
- **Evidence pointer** Results section, "Single and double mutants display distinct yet overlapping constraints..."
- **Concern** The text reports p-values for various comparisons but does not consistently report effect sizes, confidence intervals, or the results of multiple comparison corrections. The statement "p < 0.001" is used repeatedly without specifying the exact test or the adjusted p-value.
- **Required correction** Provide a more complete statistical reporting, including effect sizes, confidence intervals, and the specific post-hoc tests used. Consider presenting the data in a more accessible format, such as a summary table with all pairwise comparisons.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability section
- **Evidence pointer** Data availability section
- **Concern** The data availability statement indicates that transcriptomic data are from public repositories and that code is available at GitHub, but it does not specify where the processed data (e.g., the sDEG lists, the network files, the AlphaFold-Multimer output) can be accessed. The statement "All other data supporting the findings are available from the corresponding authors on reasonable request" is vague.
- **Required correction** Provide a more detailed data availability statement, including accession numbers for processed data and a persistent repository (e.g., Zenodo, Figshare) for the analysis outputs.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** All figures
- **Evidence pointer** Figures 1-5 (not provided)
- **Concern** The figures are referenced extensively but were not provided for review. This makes it impossible to assess the quality of the data presentation, the appropriateness of the statistical visualizations, or the clarity of the figures.
- **Required correction** Ensure that all figures are included in the manuscript submission and are of high quality, with clear labels, legends, and statistical annotations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract, "Highlight" section
- **Evidence pointer** Abstract
- **Concern** The "Highlight" section states "Data mining of public transcriptomes, network inference and AlphaFold-Multimer screening identify ABF2 and bZIP2 as interacting regulators of root remodelling under combined stress." The term "identify" implies experimental validation, but the evidence presented is primarily computational and phenotypic. The wording could be interpreted as overclaiming.
- **Required correction** Consider rephrasing to "predict" or "implicate" to more accurately reflect the nature of the evidence.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results, AlphaFold analysis
- **Evidence pointer** Results section, "AlphaFold protein–protein analysis reveals heterodimerization among ABF2, bZIP2, and HB6"
- **Concern** The text states that "only three candidates robustly interacted with one another in a heterotypic manner" but also notes that homodimers scored comparably or higher. The distinction between "robust" heterotypic interactions and the homodimer scores is not clearly defined. The biological significance of the heterodimer versus homodimer preference is not discussed.
- **Required correction** Clarify the criteria for "robust" interaction and discuss the potential biological implications of the relative strengths of homo- versus heterodimer formation.

## Risk / unsupported claims
- The claim of "additive or synergistic" effects of ABF2 and bZIP2 on root system architecture is not fully supported without single-mutant data under single stresses and double-mutant data under single stresses. The current experimental design only compares mutants under combined stress versus control.
- The claim of "first mechanistic evidence" for the ABF2-bZIP2 complex in combined stress is not fully supported without a comprehensive literature review demonstrating that no prior mechanistic evidence exists.
- The assignment of specific downstream targets to specific dimeric configurations (homodimer vs. heterodimer) is based solely on computational motif-spacing analysis and is not experimentally validated.
- The statement that "approximately 45-54% of sDEGs were shared between the two stresses" is presented without confidence intervals or a clear statistical framework for defining "shared."
- The AlphaFold-Multimer predictions of protein-protein interactions are presented as evidence of physical interaction, but no experimental validation (e.g., co-immunoprecipitation, yeast two-hybrid) is provided.
- The functional significance of the trichoblast-expressed target AT3G03790 is inferred from expression data but not experimentally tested.
- The generalizability of the findings to soil-based conditions is limited, as acknowledged by the authors, but the discussion does not fully address how the in vitro phenotypes might translate to field conditions.