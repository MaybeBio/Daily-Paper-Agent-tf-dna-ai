## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific soundness, methodological rigor, validity of conclusions, and adherence to Nature-style criteria based solely on the provided manuscript
- **Shared manuscript claim summary** The authors report a comprehensive in silico characterization of coding and non-coding SNPs in the human TP63 gene. They identify eight nsSNPs predicted deleterious by multiple tools, with three (R319H, G349E, C347F) showing reduced DNA binding affinity via molecular docking and disrupted complex stability via MD simulation. They also report five non-coding SNPs in miRNA binding sites and five eQTL SNPs in specific tissues.
- **Visible evidence base** Main text, Tables 1-4, Figures 1-8, supplementary references (Figures S1-S6, Tables S1-S6)
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; no raw data, tool output files, or simulation parameter files; no sequence alignment details; no validation of predicted pathogenic variants against functional assays

## Reviewer
- **Overall assessment** The manuscript presents a systematic in silico pipeline for SNP characterization in TP63, combining multiple prediction tools with molecular docking and MD simulation. The workflow is logical and the integration of coding and non-coding SNP analysis is commendable. However, the study is entirely computational with no experimental validation, and several methodological details are insufficiently described. The conclusions regarding pathogenicity and disease association are overstated given the predictive nature of the tools used. The manuscript would benefit from clearer presentation of filtering criteria, more rigorous statistical treatment of docking and simulation results, and tempering of causal language.
- **Who would be interested in the results, and why** Researchers in cancer genetics and bioinformatics would find the prioritized SNP list useful for designing targeted sequencing or functional studies. Those studying TP63-related developmental disorders may also reference the identified variants. The methodological pipeline could serve as a template for similar in silico SNP characterization studies in other genes.
- **Major strengths** 1) Comprehensive multi-tool approach covering sequence, structural, and regulatory effects. 2) Integration of molecular docking and MD simulation adds dynamic insight beyond static predictions. 3) Inclusion of non-coding SNP analysis via multiple databases (RegulomeDB, PolymiRTS, GTEx) broadens the scope. 4) Clear prioritization of three nsSNPs for detailed structural analysis.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of experimental validation), R1-M2 (insufficient methodological detail for reproducibility), R1-M3 (overstated conclusions from predictive tools), R1-M4 (inadequate statistical treatment of docking scores)
- **Assessment against Nature-style criteria** **Originality**: Moderate. The application of established in silico tools to TP63 is novel in its specific combination but does not introduce new methodology. **Scientific importance**: Limited. The findings are hypothesis-generating but do not establish biological or clinical significance without experimental confirmation. **Interdisciplinary readership**: Narrow. Primarily relevant to computational biologists and TP63 researchers; limited appeal to broader biomedical audience. **Technical soundness**: Partially adequate. The pipeline is reasonable but lacks critical controls, statistical rigor, and reproducibility details. **Readability for nonspecialists**: Acceptable. The writing is generally clear, though some sections assume familiarity with bioinformatics tools.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires substantial revisions including experimental validation or clear framing as hypothesis-generating, full methodological transparency, and tempered conclusions before it could be considered for publication in a high-impact venue.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength
- **Claim pointer** The authors claim that three nsSNPs (R319H, G349E, C347F) "have a significantly harmful effect on the stability of TP63-DNA complexes" and "may potentially cause diseases such as cancers."
- **Evidence pointer** Section 3.6, Figures 8A-C, Section 4 Discussion
- **Concern** All conclusions are derived from computational predictions without any experimental validation. The pathogenicity claims rest entirely on in silico tools whose predictive accuracy is variable and often modest. No functional assays, cell-based experiments, or animal models are presented to confirm the predicted effects on DNA binding, protein stability, or disease association.
- **Why it matters** In silico predictions are hypothesis-generating, not confirmatory. Without experimental evidence, the central claims of the paper remain unsubstantiated. The title and conclusions imply a level of certainty that the methodology cannot support.
- **Resolution test** Provide experimental validation (e.g., electrophoretic mobility shift assay for DNA binding, thermal stability assays, cell-based reporter assays) for at least the three prioritized nsSNPs, or explicitly reframe the study as hypothesis-generating and remove definitive pathogenicity claims.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The methods section describes the use of multiple tools and simulation parameters, but critical details are missing.
- **Evidence pointer** Section 2.2-2.6
- **Concern** The manuscript lacks sufficient detail to reproduce the analysis. Specific tool versions are not provided for most tools. The criteria for filtering 28 to 17 to 8 nsSNPs are not fully transparent. MD simulation parameters (e.g., equilibration protocol, temperature coupling specifics, pressure control) are incompletely described. The selection of the three nsSNPs for MD simulation is not clearly justified beyond "significant" predictions.
- **Why it matters** Reproducibility is a cornerstone of scientific publication. Without complete methodological transparency, other researchers cannot verify or build upon these findings.
- **Resolution test** Provide a detailed supplementary methods section with tool versions, exact filtering thresholds, complete MD simulation parameters, and a step-by-step workflow diagram with decision criteria.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Conclusion validity
- **Claim pointer** The authors state that "R319H was found to be a significantly deleterious nsSNP of TP63 protein compared to the other two" and that the identified non-coding SNPs "affect the normal regulation of TP63 gene expression and protein production."
- **Evidence pointer** Section 5 Conclusions, Section 3.7
- **Concern** The comparative claim that R319H is "significantly" more deleterious than G349E or C347F is not supported by any statistical test. The differences in RMSD, Rg, or SASA values between mutants are descriptive, not inferential. For non-coding SNPs, the eQTL analysis identifies associations, not causal effects on gene expression. The PolymiRTS predictions are not validated experimentally.
- **Why it matters** Overstated conclusions mislead readers and can direct inappropriate research priorities. Statistical rigor is essential for comparative claims.
- **Resolution test** Perform appropriate statistical comparisons (e.g., bootstrap analysis of simulation trajectories, multiple independent simulations with error estimates) to support any comparative claims. Reframe eQTL and PolymiRTS findings as associations requiring functional validation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical rigor
- **Claim pointer** The molecular docking results report binding affinities for wild-type and mutant TP53 peptides with DNA.
- **Evidence pointer** Section 3.5, Table 4
- **Concern** Docking scores from AutoDock Vina are presented as binding affinities without error estimates or replicate runs. The significance of differences between wild-type and mutant binding affinities is not assessed statistically. The manuscript does not state how many docking runs were performed or whether results were consistent across runs.
- **Why it matters** Docking scores are approximate and can vary between runs. Without replicates and statistical analysis, the reported differences may not be meaningful.
- **Resolution test** Provide multiple independent docking runs with mean and standard deviation for each complex, and perform appropriate statistical tests (e.g., t-test or Mann-Whitney U) to assess significance of differences.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2
- **Evidence pointer** "SIFT, Polyphen2, and CADD" (location not provided)
- **Issue** Tool names are inconsistently capitalized and some are abbreviated without full names at first use.
- **Required correction** Standardize tool names and provide full names with versions at first mention.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Section 3.4.2
- **Evidence pointer** Figure 4
- **Issue** The conservation analysis results are described in text but the figure is not referenced in the text at the appropriate location.
- **Required correction** Add explicit figure callouts in the text where the results are described.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Section 3.7.1
- **Evidence pointer** "Out of 23 SNPs" (location not provided)
- **Issue** The text states 21 SNPs were selected but then refers to 23 SNPs. This numerical inconsistency is confusing.
- **Required correction** Clarify the correct number and ensure consistency throughout the text and tables.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language precision
- **Affected element** Section 3.6.1
- **Evidence pointer** "reached an apex of 23.6 Å at 33.2 ns" (location not provided)
- **Issue** The term "apex" is informal; "maximum" or "peak" would be more appropriate in scientific writing.
- **Required correction** Replace "apex" with "maximum" or "peak".

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.4
- **Evidence pointer** "USCF Chimera 1.14" (location not provided)
- **Issue** The acronym "USCF" appears to be a typo for "UCSF" (University of California, San Francisco).
- **Required correction** Correct the typo to "UCSF Chimera".

## Risk / unsupported claims
- The claim that the three nsSNPs "have a significantly harmful effect" is unsupported without experimental validation or statistical testing.
- The claim that R319H is "significantly" more deleterious than the other two mutants is unsupported by any inferential statistics.
- The statement that non-coding SNPs "affect the normal regulation of TP63 gene expression" is an overinterpretation of eQTL associations, which are correlational.
- The claim that the identified SNPs "may potentially cause diseases such as cancers" is speculative and not directly tested.
- The novelty claim that "no study has been performed for the analysis of nsSNPs with molecular docking and MD simulation approaches for the TP63 protein" is unverifiable from the provided material and would require a comprehensive literature search to substantiate.
- The conclusion that the study "will serve as a benchmark" is an overstatement given the lack of experimental validation and the preliminary nature of computational predictions.