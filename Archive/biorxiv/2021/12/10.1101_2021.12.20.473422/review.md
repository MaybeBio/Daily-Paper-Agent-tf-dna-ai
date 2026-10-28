## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supporting information captions
- **Assessment boundary** Scientific validity, methodological soundness, statistical rigor, performance claims, and reproducibility of the described computational tool "Grit"
- **Shared manuscript claim summary** The authors present a new computational tool, Grit, that identifies transcription factor binding sites (TFBS) in orthologous gene promoter sequences using a mixed Student's t-test statistical method. The tool is claimed to outperform existing motif scanning tools including Pscan and FIMO on benchmark ChIP-Seq datasets, and to be computationally efficient.
- **Visible evidence base** Abstract, full methods section, results section with figures referenced, discussion, and supporting information captions. No actual data files, code, or supplementary tables were provided for independent verification.
- **Missing materials affecting confidence** The actual software code, complete benchmark datasets, supplementary tables (Table S1, S2, S3), the Supplementary Document describing the statistical properties, and the full figures (Fig 1, 2, 3) were not provided. The equations (Equations 1-4) are referenced but not shown in the supplied text.

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful computational approach for TFBS prediction that combines comparative genomics with a novel statistical test. The core idea of using orthologous gene promoter sets and a mixed t-test to identify conserved and non-conserved binding sites is interesting and could be valuable to the field. However, the manuscript as presented has significant gaps in methodological detail, statistical justification, and validation evidence. The performance claims, while potentially promising, cannot be fully evaluated from the provided material. The statistical method is not rigorously derived or compared to existing approaches, and the benchmark comparisons lack critical details about data processing, parameter settings, and statistical significance of differences. The manuscript would benefit from substantial revision and additional analysis before it could be considered for publication in a high-impact venue.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on transcription factor binding site prediction, regulatory genomics, and comparative genomics would be the primary audience. Researchers studying gene regulation and transcriptional networks would also find the tool potentially useful for identifying functional TFBS in orthologous gene sets. The claim of improved performance over existing tools like FIMO and Pscan would be of interest to those who routinely use such tools in their research.

- **Major strengths** The manuscript addresses a relevant problem in regulatory genomics. The idea of using orthologous gene sets without sequence alignment is a reasonable approach for cross-species comparisons, particularly for distantly related species. The mixed Student's t-test is a novel statistical contribution that attempts to combine information from both conservation and score differences. The tool is benchmarked against multiple existing tools using public ChIP-Seq datasets, which is a good validation strategy. The computational efficiency claim (3.2 Mb/s) is potentially attractive for whole-genome scanning applications.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical methodology
- **Claim pointer** The manuscript claims that the mixed Student's t-test is a new statistical method that detects high-scoring conserved and non-conserved binding sites among species.
- **Evidence pointer** Section 2.3, Equations 2 and 3 (not shown in supplied text)
- **Concern** The statistical derivation of the mixed Student's t-test is not presented. The equations for the t-statistic and degrees of freedom are referenced but not shown. The manuscript does not explain how the one-sample and two-sample t-tests are combined, what assumptions are made about the underlying distributions, or how the degrees of freedom are calculated. The claim that the test behaves as a one-sample t-test when distributions are the same and a two-sample t-test when the observation is at the mean of the obs set is stated but not mathematically justified. Without a clear derivation and statement of assumptions, the statistical validity of the method cannot be assessed.
- **Why it matters** The entire method is built on this statistical test. If the test is not properly derived or its assumptions are violated, the p-values produced could be invalid, leading to incorrect identification of TFBS. The manuscript needs to provide a rigorous mathematical derivation, discuss the conditions under which the test is valid, and compare its properties to existing statistical approaches.
- **Resolution test** Provide the full derivation of the mixed t-test statistic and its null distribution. Show that the test controls Type I error rates under simulated data with known ground truth. Compare the statistical power of the mixed t-test to standard one-sample and two-sample t-tests under various scenarios.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Benchmarking methodology
- **Claim pointer** The manuscript claims that Grit outperforms Pscan (4.8%) and FIMO (17.8%) in analyzing ChIP-Atlas human genome ChIP-Seq datasets, as measured by ACCg.
- **Evidence pointer** Section 3.3, Table 2
- **Concern** The benchmark comparison methodology is insufficiently described. The definition of true positives (80% overlap with ChIP-Seq peaks) is given, but the details of how the six tools were configured, what parameters were used, how the background was defined for each tool, and how the p-value thresholds were set are not provided. The claim that Grit outperforms FIMO by 17.8% in ACCg is presented without confidence intervals or statistical tests of significance. The manuscript states that "a random subset of the transcription factors (35 TFs)" was used for PWMScan and Clover, but the selection criteria and whether this subset is representative are not discussed. The comparison of tools with different design philosophies (single-species vs. multi-species) may not be fair without careful normalization of parameters.
- **Why it matters** The performance claims are the central evidence for the utility of Grit. If the benchmark is not conducted rigorously, the claims of superiority over existing tools cannot be trusted. The field relies on careful benchmarking to guide tool selection, and misleading comparisons can lead researchers to use suboptimal tools.
- **Resolution test** Provide complete details of the benchmark setup, including all parameters for each tool, the exact datasets used, and the criteria for selecting the 35 TF subset. Report confidence intervals or perform statistical tests (e.g., paired t-test or Wilcoxon signed-rank test) on the ACCg differences across all datasets. Make the benchmark code and data publicly available for reproducibility.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation and ground truth
- **Claim pointer** The manuscript claims that Grit identifies TFBS that are validated by ChIP-Seq datasets, and that the tool is "amongst the top-ranked TF-binding site predictors."
- **Evidence pointer** Sections 3.2 and 3.3, Figures 2 and 3
- **Concern** The validation relies entirely on overlap with ChIP-Seq peaks, which is a reasonable but limited approach. ChIP-Seq peaks can be broad and may not precisely localize the actual TFBS. The manuscript does not report the number of TFBS predicted per TF, the distribution of predicted sites relative to transcription start sites, or the enrichment of known TFBS motifs in the predicted regions. The comparison with EPD (93.2% overlap) is presented as validation of the promoter set, but this does not validate the TFBS predictions themselves. The manuscript does not include any experimental validation or independent computational validation (e.g., using DNase-seq footprints or evolutionary conservation analysis) of the predicted TFBS.
- **Why it matters** Without robust validation, the biological relevance of the predicted TFBS is uncertain. ChIP-Seq overlap alone can be misleading, as many predicted sites may fall within peaks by chance. The field expects multiple lines of evidence to support the functional significance of predicted TFBS.
- **Resolution test** Provide additional validation using independent datasets (e.g., DNase-seq, ATAC-seq, or evolutionary conservation). Report the precision-recall curves for each tool across a range of thresholds. Include analysis of the positional distribution of predicted TFBS relative to TSS and known regulatory regions. If possible, include experimental validation of a subset of predictions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Computational efficiency
- **Claim pointer** The manuscript claims that Grit performs sequence scanning at a rate of 3.2 Mb/s on a quad-core Amazon server.
- **Evidence pointer** Abstract, Section 3.2
- **Concern** The computational efficiency claim is presented without details on the hardware specifications, the size of the input data, the number of PWMs scanned, or the memory usage. The claim of 3.2 Mb/s is a single point estimate without variance or comparison to other tools under the same conditions. The total runtime of 22 hours for the human genome analysis is mentioned, but the number of TFs (537) and the size of the promoter set are not clearly stated in the context of this runtime.
- **Why it matters** Computational efficiency is a key selling point for whole-genome scanning tools. If the efficiency claim is not reproducible or is not compared fairly to other tools, it cannot be used to justify the advantage of Grit.
- **Resolution test** Provide detailed benchmark conditions, including hardware specifications, memory usage, and the exact input data. Report runtime and memory usage for all six tools under identical conditions. Include scaling analysis with different genome sizes and numbers of PWMs.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and availability
- **Claim pointer** The manuscript claims that Grit is publicly available at http://www.thua45.cn/grit under an academic free license.
- **Evidence pointer** Abstract, Section 4.3
- **Concern** The availability of the tool is claimed, but no version number, release date, or documentation is provided. The website URL is given, but the manuscript does not state whether the source code is available, what programming language is used, or what dependencies are required. The methods section does not provide sufficient detail for independent implementation of the algorithm. The exact steps for building the orthologous gene promoter sets, the BLAST parameters, and the statistical testing procedure are described at a high level but lack the specificity needed for reproduction.
- **Why it matters** Reproducibility is a core requirement for computational tools. Without access to the source code and detailed documentation, other researchers cannot verify the claims or use the tool effectively. The field increasingly expects tools to be released with open source code and comprehensive documentation.
- **Resolution test** Provide the source code in a public repository (e.g., GitHub) with a version number, license, and documentation. Include a detailed user manual with examples and instructions for running the tool on custom data. Provide a Docker container or virtual machine image for easy deployment.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Section 1
- **Issue** The abstract and introduction contain several grammatical errors and awkward phrasings. For example, "Identification their function" in the Author Summary and "the tool is amongst the top-ranked TF-binding site predictors" are unclear or informal. The introduction does not clearly state the specific limitations of existing tools that Grit addresses.
- **Required correction** Revise the abstract and introduction for clarity and grammatical correctness. Clearly state the specific limitations of existing tools (e.g., computational cost, inability to handle non-conserved sites, lack of individual site p-values) and how Grit addresses each.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Figure and table presentation
- **Affected element** Figures 1, 2, 3 and Tables 1, 2
- **Evidence pointer** Sections 2.1, 3.1, 3.2, 3.3
- **Concern** The figures and tables are referenced but not shown in the supplied text. The captions are not provided. Table 1 is mentioned as summarizing parameters of 18 tools, but the parameters are not described in the text. The figures are essential for evaluating the results, particularly Figure 1C showing the relationship between p-values, CCV, and SD, and Figure 2 showing the benchmark results.
- **Required correction** Provide all figures and tables with complete captions. Ensure that the text refers to specific panels and explains the key findings from each figure. Include the full Table 1 with all tool parameters.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 3.2 and 3.3
- **Evidence pointer** Sections 3.2, 3.3
- **Concern** The manuscript reports p-values for comparisons between tools (e.g., "p-value ≤ 0.05") but does not specify which statistical test was used, whether multiple testing correction was applied, or the sample size (number of datasets) for each comparison. The statement "Grit outperformed FIMO 29% as evaluated by ACCg" is presented without a measure of variability.
- **Required correction** Specify the statistical tests used for all comparisons, report the number of datasets, and provide confidence intervals or effect sizes. If multiple comparisons are made, apply and report appropriate corrections.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Background model description
- **Affected element** Section 2.2
- **Evidence pointer** Section 2.2
- **Concern** The description of the raw score (RS) calculation is incomplete. The text states that RS is based on a component of HMM and represents the LLR for a motif being present, but the exact formula is not given. The relationship between RS and the "average of LRs" is unclear, and the notation is not defined.
- **Required correction** Provide the full equations for RS calculation with all variables defined. Explain how the background model is constructed and how the LLR is computed.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Section 4
- **Evidence pointer** Section 4
- **Concern** The discussion does not address potential limitations of the approach, such as the assumption of normal distribution of RS values, the choice of 2 kb promoter length, the impact of the number of reference genomes on statistical power, or the potential for false positives due to repetitive elements or paralogous genes.
- **Required correction** Add a paragraph discussing the limitations of the method and potential sources of error. Suggest directions for future improvement.

## Risk / unsupported claims
- The claim that Grit is "amongst the top-ranked TF-binding site predictors" is not fully supported by the evidence presented, as the benchmark methodology is incomplete and statistical significance of differences is not established.
- The claim that the mixed Student's t-test is a new statistical method is not verifiable without the full derivation and comparison to existing methods.
- The claim of 3.2 Mb/s scanning rate is not reproducible without detailed benchmark conditions.
- The claim that Grit identifies "high-scoring conserved and non-conserved binding sites" is not clearly demonstrated, as the relationship between CCV, SD, and biological relevance is not established.
- The performance improvement over Pscan (4.8%) and FIMO (17.8%) is presented as a single average value without confidence intervals or statistical testing.
- The validation using EPD (93.2% overlap) is presented as evidence of promoter set accuracy, but this does not validate the TFBS predictions themselves.
- The claim that the tool "can help the researchers in TF-binding site identification and transcriptional regulation mechanism interpretation" is a general statement not directly supported by the results presented.

## Assessment against Nature-style criteria
- **Originality** The mixed Student's t-test approach for combining conservation and score information in TFBS prediction is a novel contribution. The use of orthologous gene promoter sets without sequence alignment is also a reasonable and potentially original approach. However, the novelty is diminished by the lack of a clear comparison to existing statistical methods and the incomplete presentation of the method.
- **Scientific importance** TFBS prediction is an important problem in regulatory genomics, and improved tools are of broad interest. The potential to identify both conserved and non-conserved binding sites is valuable. However, the importance of the contribution is not fully established without robust validation and clear demonstration of advantages over existing tools.
- **Interdisciplinary readership** The topic is relevant to computational biology, bioinformatics, and molecular biology. The manuscript is written in a way that is accessible to these audiences, but the statistical details are not presented clearly enough for a broad readership to evaluate the method.
- **Technical soundness** The technical soundness cannot be fully assessed from the provided material. The statistical method is not rigorously derived, the benchmark methodology is incomplete, and the validation is limited. The computational efficiency claim is not reproducible. These issues need to be addressed before the technical soundness can be established.
- **Readability for nonspecialists** The abstract and author summary are written in a way that is accessible to a broad audience. However, the methods section is not sufficiently detailed for specialists to evaluate the approach, and the results section relies heavily on figures that were not provided. The manuscript would benefit from clearer explanations of the statistical method and the benchmark results.