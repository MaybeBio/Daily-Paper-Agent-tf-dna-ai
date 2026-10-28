## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract, assessed against the stated scope of a genome-wide identification and characterization study
- **Shared manuscript claim summary** The authors report identification of 11 CBP60 family members in tomato, with three homologs showing closest amino acid identity to Arabidopsis CBP60g and SARD1. AlphaFold predictions indicate close structural similarity between these tomato and Arabidopsis homologs. Conserved domain analyses show CAM-binding and DNA-binding domains. Five tomato CBP60 genes are pathogen-responsive and temperature-sensitive. The authors conclude that these proteins may function as Ca(2+)-sensing transcriptional regulators.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods section, sequence alignment data, AlphaFold structure predictions, gene expression data, statistical analyses, and any supplementary information

## Reviewer

- **Overall assessment** The abstract presents a potentially valuable genome-wide identification of the CBP60 family in tomato, an agriculturally important crop. The combination of phylogenetic analysis, structural prediction, and expression profiling under biotic and abiotic stress is a reasonable approach. However, the abstract alone provides insufficient detail to evaluate the technical rigor of the analyses, the statistical support for expression claims, or the biological significance of the findings. The claim of "close structural similarity" based on AlphaFold requires careful validation, and the functional implications remain speculative without experimental evidence.
- **Who would be interested in the results, and why** Plant molecular biologists studying calcium signaling and immunity, particularly those working on crop species beyond Arabidopsis. Researchers interested in the CBP60 family and its role in salicylic acid and NHP biosynthesis would find the identification of tomato orthologs useful. The structural predictions may interest computational biologists working on transcription factor families, though the functional claims would need experimental validation to attract a broader audience.
- **Major strengths** The study addresses a clear gap in knowledge by extending CBP60 family characterization from Arabidopsis to tomato, a crop of significant agricultural importance. The use of AlphaFold for structural prediction is a modern and potentially powerful approach. The inclusion of both biotic and abiotic stress conditions in expression profiling is commendable and aligns with known roles of Arabidopsis CBP60g and SARD1.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide evidence for the statistical significance of expression changes, the criteria for defining "pathogen-responsive" and "temperature-sensitive," or the validation of AlphaFold predictions against experimental structures or biochemical data. The functional claim of "Ca(2+)-sensing transcriptional regulators" is not supported by any direct experimental evidence in the abstract.
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The work extends known findings from Arabidopsis to tomato, which is useful but not conceptually novel.
  - Scientific importance: Moderate. CBP60 family characterization in a crop species has practical relevance, but the abstract does not demonstrate new mechanistic insights.
  - Interdisciplinary readership: Limited. The work is primarily of interest to plant immunity and calcium signaling specialists.
  - Technical soundness: Not assessable from the abstract alone. Key methodological details and statistical support are absent.
  - Readability for nonspecialists: The abstract is clearly written and accessible, though some jargon (e.g., NHP, pattern-triggered immunity) is used without full explanation.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially useful study, but the evidence base is insufficient to assess technical rigor or biological significance. A full manuscript review would be required to determine whether the claims are supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "AlphaFold deep learning-assisted prediction of protein structures highlighted close structural similarity between these tomato and Arabidopsis CBP60 homologs."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract claims close structural similarity based on AlphaFold predictions, but no details are provided on the metrics used to define "close similarity" (e.g., RMSD, TM-score, or pLDDT confidence scores). AlphaFold predictions are computational models and require careful interpretation, especially for proteins with intrinsically disordered regions or multiple domains. Without validation against experimental structures or at least rigorous structural alignment statistics, this claim is not verifiable.
- **Why it matters** The structural similarity claim is central to the paper's argument that tomato CBP60 homologs may function analogously to Arabidopsis CBP60g and SARD1. If the structural comparison is not robust, the functional inference is weakened.
- **Resolution test** Provide quantitative structural comparison metrics (e.g., TM-score, RMSD) with confidence intervals, and discuss the reliability of AlphaFold predictions for these specific proteins. Ideally, include experimental validation such as circular dichroism or limited proteolysis to support the predicted folds.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "five tomato CBP60 genes were pathogen-responsive and temperature-sensitive, reminiscent of Arabidopsis CBP60g and SARD1."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract states that five genes are pathogen-responsive and temperature-sensitive, but no information is provided on the magnitude of expression changes, statistical significance, or the criteria used to define responsiveness. It is unclear whether these genes show coordinated regulation or distinct patterns, and whether the responses are biologically meaningful (e.g., fold-change thresholds, time points, or replicates).
- **Why it matters** The expression data are the only functional evidence presented. Without statistical rigor, the claim of stress regulation is not established, and the comparison to Arabidopsis CBP60g and SARD1 is anecdotal.
- **Resolution test** Provide detailed expression data with statistical analyses (e.g., ANOVA or t-tests with multiple testing correction), define response thresholds, and show time-course or dose-response data. Include validation by qRT-PCR or independent replicates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** "we provide evidence on their regulation and potential function as Ca(2+)-sensing transcriptional regulators."
- **Evidence pointer** Abstract only; location not provided
- **Concern** The abstract claims potential function as Ca(2+)-sensing transcriptional regulators, but no experimental evidence is presented for calcium binding, calcium-dependent conformational changes, or transcriptional activity. The presence of CAM-binding and DNA-binding domains is suggestive but not sufficient to establish function.
- **Why it matters** The functional claim is the main scientific contribution of the study. Without direct evidence, the paper is limited to a descriptive genomic analysis, which is of lower impact.
- **Resolution test** Provide experimental data such as calcium-binding assays (e.g., electrophoretic mobility shift assays with calcium, or isothermal titration calorimetry), transcriptional activation assays in planta or in heterologous systems, or genetic complementation studies in Arabidopsis mutants.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract text
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract uses abbreviations such as NHP and pattern-triggered immunity without defining them, which may limit accessibility for readers outside plant immunity.
- **Required correction** Define NHP and pattern-triggered immunity at first use, or provide a brief explanatory phrase.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Phylogenetic analysis
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states that three homologs have the closest amino acid identity to Arabidopsis CBP60g and SARD1, but the method for determining "closest" is not described (e.g., BLAST E-values, phylogenetic tree topology, or pairwise identity percentages).
- **Required correction** Specify the criteria and method used for identifying the closest homologs, and provide supporting data such as a phylogenetic tree or identity matrix.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Study scope
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract does not discuss the potential functional divergence among the 11 tomato CBP60 members, which would be important for understanding their roles in immunity and stress.
- **Required correction** Add a brief statement on the expected functional diversity or redundancy among the family members, based on sequence or expression differences.

## Risk / unsupported claims

- The claim of "close structural similarity" between tomato and Arabidopsis CBP60 homologs is unsupported without quantitative structural comparison metrics or experimental validation.
- The claim that five tomato CBP60 genes are "pathogen-responsive and temperature-sensitive" is unsupported without statistical details and defined thresholds.
- The claim of "potential function as Ca(2+)-sensing transcriptional regulators" is speculative and not supported by direct experimental evidence in the abstract.
- The general statement that CBP60 family members "can regulate plant immune responses" in Arabidopsis is presented as established fact, but the abstract does not provide citations or context for this claim, making it unverifiable from the supplied material.