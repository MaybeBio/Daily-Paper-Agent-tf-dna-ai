## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, conclusion, materials and methods, and sequence information
- **Assessment boundary** Scientific validity, technical soundness, clarity of claims, and adequacy of evidence as presented in the provided manuscript
- **Shared manuscript claim summary** The authors report semi-rational engineering of a B-family DNA polymerase from Thermococcus kodakaraensis (KOD pol) to improve incorporation of 3'-O-azidomethyl-modified nucleotides. Through site-directed saturation mutagenesis, computational screening, and stepwise combinatorial mutagenesis, they identify variant Mut_E11 with eleven mutations that shows over 20-fold improved activity relative to an intermediate variant and demonstrates functional performance on two sequencing platforms.
- **Visible evidence base** Results sections describing screening strategies, mutagenesis libraries, kinetic assays, computational predictions, and sequencing platform validation; figures referenced but not provided; supplementary files referenced but not provided
- **Missing materials affecting confidence** All figures (Fig 1-9), supplementary figures (S1-S4), supplementary tables (S1-S2), raw sequencing data, kinetic parameter values, and detailed computational methods are not provided. This substantially limits independent verification of the reported results.

## Reviewer
- **Overall assessment** The manuscript describes a systematic enzyme engineering effort with a logical workflow from active-site saturation mutagenesis to computational prediction and combinatorial assembly. The reported improvements in modified nucleotide incorporation and successful validation on two sequencing platforms are potentially valuable for the NGS field. However, the absence of all figures, tables, and supplementary materials prevents verification of the quantitative claims, kinetic parameters, structural interpretations, and sequencing quality metrics. The mechanistic interpretations, particularly regarding salt bridge formation and electrostatic interactions, are speculative and not supported by direct structural or biophysical evidence. The manuscript would benefit from clearer presentation of experimental replicates, statistical analysis, and direct comparisons to previously reported engineered polymerases.

- **Who would be interested in the results, and why** Researchers in DNA polymerase engineering, enzyme evolution, and next-generation sequencing technology development would be interested. The identified mutation sites and the semi-rational workflow could inform future engineering of B-family polymerases for modified nucleotide substrates. The demonstration of cross-platform compatibility (BGISEQ-500 and MGISEQ-2000) is relevant for commercial sequencing applications.

- **Major strengths** The study combines experimental screening with computational prediction in a structured multi-round approach. The use of a FRET-based high-throughput assay is a practical screening strategy. The stepwise combination of beneficial mutations is a sound evolutionary approach. The validation on two independent sequencing platforms strengthens the practical relevance of the engineered variant.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that Mut_E10 demonstrates "over 20-fold improvement in enzymatic activity as compared to Mut_C2" and "satisfactory performance" on two sequencing platforms.
- **Evidence pointer** Results sections "Stepwise combination of effective mutations" and "Sequencing performance validation of KOD variants in NGS"; figures 7-9 referenced but not provided
- **Concern** The quantitative claims of fold-improvement and sequencing performance cannot be verified because the figures showing kinetic data, sequencing quality metrics, and comparative analyses are not included in the provided material. The text references specific values (e.g., "over 23-fold" for E(Mut)/PT-2Cy5) but the underlying data, error bars, replicates, and statistical tests are absent. Without access to the figures and supplementary tables, the magnitude of the reported improvements and the quality of sequencing results cannot be independently assessed.
- **Why it matters** The central claims of the manuscript rest on quantitative improvements in enzyme activity and sequencing performance. If these data are not transparently presented with appropriate statistical analysis, the conclusions are not reproducible or verifiable.
- **Resolution test** Provide all figures with raw data points, error bars, and statistical significance indicators. Include supplementary tables with complete kinetic parameters (kcat, Km, kcat/Km) for all reported variants. Present sequencing quality metrics (Q30, error rates, mapping rates) with appropriate controls and replicates.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic interpretation
- **Claim pointer** The manuscript claims that the A485E mutation forms a salt bridge with Q332, "preventing the rotation of the finger domain," and that this locking "has the potential to enhance the stability of the modified substrate access channel."
- **Evidence pointer** Discussion section; Figure 3B referenced but not provided
- **Concern** The proposed salt bridge between A485E and Q332 is presented as a structural interpretation, but no direct evidence (e.g., crystal structure, mutagenesis of Q332, molecular dynamics trajectory analysis) is provided to support this interaction. The claim that finger domain locking enhances modified substrate access is speculative. The manuscript acknowledges that A485E "had a detrimental effect on the catalytic activity" with natural nucleotides, but the mechanistic rationale for why this benefits modified nucleotide incorporation is not experimentally tested.
- **Why it matters** The mechanistic claims are presented as explanatory for the observed improvements. If these interpretations are not supported by direct evidence, they may mislead future engineering efforts. Speculative mechanisms should be clearly labeled as hypotheses.
- **Resolution test** Provide structural or biophysical evidence for the proposed salt bridge (e.g., co-crystal structure, mutagenesis of Q332, or molecular dynamics free energy calculations). Alternatively, temper the mechanistic claims and present them explicitly as hypotheses requiring further validation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Computational methodology
- **Claim pointer** The manuscript claims that computational screening using MM-GBSA binding energy calculations predicted beneficial mutations in the DNA-binding region, and that "variants with more negative computational free energy values are expected to exhibit stronger binding affinities to dsDNA."
- **Evidence pointer** Materials and methods section "MM-GBSA screening method"; Figures 5 and S2-S3 referenced but not provided
- **Concern** The computational screening methodology is described only briefly. Key details are missing, including the force field parameters used, the length and convergence criteria of the MD simulations, the specific MM-GBSA implementation, and the validation of the computational predictions against experimental results. The correlation between predicted binding energies and experimentally measured activities is not shown. The selection threshold of -260 kcal/mol is stated without justification.
- **Why it matters** The computational predictions are a central component of the semi-rational design strategy. Without adequate methodological detail and validation, the reliability of the computational screening cannot be assessed, and the approach cannot be reproduced by others.
- **Resolution test** Provide complete computational methods including software versions, force fields, simulation parameters, convergence criteria, and validation of the MM-GBSA approach. Show the correlation between predicted binding energies and experimental activities for the tested variants.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparative benchmarking
- **Claim pointer** The manuscript claims that Mut_E10 "exhibited satisfactory performance" on BGISEQ-500 and MGISEQ-2000 platforms and that the sequencing data is "comparable to the 'gold standard' set by NGS analysis generated using the Illumina platform."
- **Evidence pointer** Results section "Sequencing performance validation of KOD variants in NGS"; Figures 8-9 referenced but not provided
- **Concern** The sequencing performance is described qualitatively as "satisfactory" and "comparable," but no quantitative comparison to the standard enzyme used in the commercial kits is provided. The claim of comparability to Illumina platforms is based on a single reference to a previous study without direct side-by-side comparison. The manuscript does not report key sequencing metrics such as read length distribution, base call accuracy by position, or error profiles.
- **Why it matters** For a claim of practical applicability in commercial sequencing platforms, quantitative benchmarking against the current standard enzyme is essential. Qualitative descriptions without statistical comparison do not establish equivalence or superiority.
- **Resolution test** Provide quantitative sequencing metrics for Mut_E10 compared to the kit-supplied enzyme under identical conditions, including error rates, Q30 distributions, and mapping statistics with appropriate replicates and statistical tests.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract and Results section "Mutant screening strategy establishment"
- **Evidence pointer** Abstract; Figure 1 referenced but not provided
- **Issue** The abstract states that Mut_E10 carries "eleven mutation sites" but the text elsewhere refers to "nine mutation sites (besides 141A, 143A)" in the Discussion. The total count is consistent (2 + 9 = 11) but the presentation is confusing. Additionally, the abstract mentions "over 20-fold improvement" while the Results section reports "over 23-fold" for a specific metric; the relationship between these values is unclear.
- **Required correction** Clarify the mutation count consistently throughout the manuscript. Specify which fold-improvement value refers to which assay condition and metric.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and methods section "Enzyme activity screening of KOD variants"
- **Evidence pointer** Materials and methods; Figure 1 referenced but not provided
- **Issue** The FRET-based screening assay is described, but the excitation and emission wavelengths are given (530 nm and 676 nm, respectively). However, the manuscript does not specify the filter bandwidths, the plate reader model, or the data analysis method for determining "maximum slope." The assay temperature is not stated for the screening steps (the sequencing step is stated as 55°C).
- **Required correction** Provide complete assay conditions including temperature, filter specifications, and data analysis algorithms to enable reproduction.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results sections describing kinetic assays
- **Evidence pointer** Results sections "Mutant screening of the first-round of mutagenesis" and "Stepwise combination of effective mutations"
- **Issue** The manuscript reports kinetic parameters and fold-improvements but does not describe the number of replicates, standard deviations, or statistical tests used to determine significance. The phrase "over 16-fold" and "over 23-fold" suggests a single measurement or a best value rather than a statistically robust estimate.
- **Required correction** Report the number of independent replicates, standard errors or confidence intervals, and the statistical tests used for comparisons between variants.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction; Discussion
- **Issue** The manuscript mentions previous work on 9°N DNA polymerase variants but does not provide a quantitative comparison of the performance of Mut_E10 to previously reported engineered polymerases for modified nucleotide incorporation. The claim that this study provides "valuable guidance" would be strengthened by contextualizing the achieved improvements relative to the state of the art.
- **Required correction** Add a quantitative comparison to previously reported engineered polymerases, including specific activity or efficiency values where available.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Materials and methods section "Sequencing in the NGS platform"
- **Evidence pointer** Materials and methods; accession number CNP0000668
- **Issue** The sequencing data are deposited under accession CNP0000668, but the manuscript does not state when the data will be publicly released or whether they are currently accessible. For a study claiming practical applicability, immediate data availability is important.
- **Required correction** State the data release date or confirm immediate public access.

## Risk / unsupported claims
- The claim of "over 20-fold improvement" in enzymatic activity for Mut_E10 relative to Mut_C2 is not verifiable without the kinetic data shown in the referenced figures.
- The claim of "satisfactory performance" on BGISEQ-500 and MGISEQ-2000 platforms is not quantitatively supported without sequencing quality metrics and comparison to standard enzymes.
- The proposed salt bridge between A485E and Q332 is unsupported by direct structural or biophysical evidence.
- The claim that computational MM-GBSA predictions reliably identified beneficial mutations is not validated by showing the correlation between predicted and experimental values.
- The statement that sequencing data is "comparable to the 'gold standard' set by NGS analysis generated using the Illumina platform" is an overreach without direct comparative experiments.
- The mechanistic categorization of mutations into three distinct functional classes (DNA binding, catalytic pocket, finger domain conformational change) is presented as established but is largely speculative.