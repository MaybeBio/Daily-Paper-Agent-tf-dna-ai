## Review setup
- **Input scope** Full manuscript text (abstract, main text, methods, declarations) as provided
- **Assessment boundary** Scientific content, technical soundness, database utility, and claims as presented in the provided text; no supplementary files, figures, or tables were available for inspection
- **Shared manuscript claim summary** The authors present LogoMotif, an open-source database of curated and predicted transcription factor binding sites (TFBSs) in Actinobacteria, with associated position weight matrices (PWMs) and hidden Markov models (pHMMs). The database includes approximately 392 validated and approximately 15,600 predicted regulatory interactions across four Streptomyces model organisms, visualized in interactive networks. The authors claim that LogoMotif serves as a foundation for TFBS prediction, including integration with the antiSMASH v7 genome mining tool, and that it will enable researchers to elucidate gene expression and guide genome mining efforts.
- **Visible evidence base** Abstract, main text sections (Results, Discussion, Materials and Methods), figure legends referenced but figures not provided, code and data availability statements
- **Missing materials affecting confidence** Figures 1-3 (including all panels), supplementary data files, actual database contents, validation statistics, performance benchmarks, and any comparison with existing databases

## Reviewer
- **Overall assessment** The manuscript describes a potentially valuable community resource for actinobacterial regulatory genomics. The concept of combining curated TFBS data with predictive models and integrating with antiSMASH is timely and useful. However, the current text provides insufficient quantitative detail to assess the quality, coverage, and accuracy of the database. Key claims about the number of interactions, the performance of prediction models, and the utility of the resource are not supported by data presented in the manuscript. The absence of figures and supplementary materials in the provided scope prevents a full evaluation of the technical implementation and the biological validity of the curated datasets.
- **Who would be interested in the results, and why** Researchers studying gene regulation in Actinobacteria, particularly Streptomyces species, would be the primary audience. This includes those interested in antibiotic biosynthesis, specialized metabolite production, and regulatory networks. Additionally, developers and users of genome mining tools such as antiSMASH would find the integrated TFBS Finder feature relevant. The database could also serve the broader bacterial regulatory genomics community as a model for similar resources in other taxa.
- **Major strengths** The manuscript addresses a clear gap in the field, as actinobacterial TFBS data are sparse and fragmented across the literature. The combination of curated experimental data with genome-wide predictions in an interactive web interface is a practical and useful approach. The integration with antiSMASH v7 provides immediate utility for a large user base. The authors have made the resource open-source and have provided a command-line tool (MiniMotif) for custom predictions, which enhances reproducibility and accessibility.
- **Major Concerns** The manuscript lacks quantitative validation of the prediction models. No precision, recall, or comparison against known regulons is provided. The claim of approximately 15,600 predicted interactions is presented without any assessment of false positive rates. The curation process is described only briefly, and the criteria for inclusion of binding sites beyond the minimum count of four are not detailed. The database currently covers only 23 regulators, which is a small fraction of the regulatory repertoire of Actinobacteria, and the authors do not discuss how representative this set is. The integration with antiSMASH is mentioned but not demonstrated with examples or performance data. The manuscript does not compare LogoMotif with existing resources such as RegPrecise or Prodoric in terms of content overlap or complementary features.
- **Minor Comments** The abstract states approximately 400 validated and approximately 12,100 predicted interactions, while the main text states 392 validated and approximately 15,600 predicted interactions. This discrepancy should be reconciled. The description of the Shannon entropy-based curation step is vague; the authors should specify the exact threshold and how it was applied. The Methods section mentions that all matches detected from the p-value threshold onwards are reported, but the biological rationale for this permissive approach is not discussed. The authors state that the database will be regularly updated, but no versioning or update policy is described. The competing interest declaration is present but does not specify whether the antiSMASH integration involves any commercial considerations.
- **Technical failings that need to be addressed before the case is established** The absence of any validation metrics for the PWM and pHMM predictions is a critical gap. The manuscript does not demonstrate that the predicted binding sites are biologically meaningful, for example by showing enrichment of predicted sites in promoter regions of known target genes or by comparison with independent experimental data. The discrepancy in interaction counts between the abstract and main text must be resolved. The lack of figures in the provided material means that the network visualizations and sequence logos cannot be assessed for clarity or accuracy.
- **Assessment against Nature-style criteria** Originality: The concept of a dedicated actinobacterial TFBS database with integrated prediction tools is original, though it builds on established approaches from other bacterial systems. Scientific importance: The resource addresses a real need in the field of antibiotic discovery and regulatory biology, but the current evidence does not demonstrate that the database achieves its stated goals with sufficient accuracy. Interdisciplinary readership: The work is primarily of interest to microbiologists and bioinformaticians; the broader interdisciplinary appeal is limited unless the database enables new biological insights that are demonstrated. Technical soundness: The underlying methods are standard and appropriate, but the lack of validation and benchmarking undermines confidence in the results. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some technical details in the Methods could be clarified for a broader audience.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript describes a useful resource, but the core claims regarding the number and quality of predicted interactions are not supported by data presented in the text. The authors must provide validation metrics, clarify the curation and prediction pipelines, and reconcile the reported numbers before the case for the database's utility is convincing.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript claims that LogoMotif provides approximately 15,600 predicted regulatory interactions across four Streptomyces model organisms, and that these predictions are reliable enough to guide experimental work and genome mining.
- **Evidence pointer** Results section, "A comprehensive dataset of characterized and predicted actinobacterial regulatory interactions"; Materials and Methods, "Construction of computational prediction models"
- **Concern** The manuscript provides no quantitative validation of the prediction models. No precision, recall, false discovery rate, or comparison against known or independently verified regulons is presented. The authors state that all matches detected from the p-value threshold onwards are reported, which suggests a permissive threshold that may yield many false positives, but no analysis of this is provided. Without such validation, the biological utility of the predicted interactions cannot be assessed.
- **Why it matters** The central value proposition of LogoMotif is that it provides reliable predictions of TFBSs that can guide experimental design and genome mining. If the predictions are not validated, users cannot trust the results, and the database may mislead rather than inform. The claim of approximately 15,600 interactions is meaningless without an estimate of how many are true positives.
- **Resolution test** The authors should provide validation results, such as receiver operating characteristic curves, precision-recall curves, or comparison with a gold standard set of experimentally verified binding sites. They should also report the number of predicted sites per regulator and per genome, and discuss the expected false positive rate at the chosen thresholds.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Data quality and curation
- **Claim pointer** The manuscript claims that the curated dataset contains 392 experimentally characterized binding sites across 23 regulators, and that these were subjected to a curation process to ensure reliability.
- **Evidence pointer** Results section, "A comprehensive dataset of characterized and predicted actinobacterial regulatory interactions"; Materials and Methods, "Data curation"
- **Concern** The curation process is described only briefly. The authors state that a cut-off of at least four verified binding sites was used, and that an additional manual curation step was performed if the Shannon entropy information content was below half the maximum. However, the details of the literature search, the criteria for "verified" binding sites, and the nature of the manual curation are not specified. It is unclear how many binding sites were excluded and why. The small number of regulators (23) relative to the size of the phylum raises questions about the representativeness of the dataset.
- **Why it matters** The quality of the curated data underpins all downstream predictions. If the curation criteria are not transparent and reproducible, the database cannot be considered a reliable community resource. Users need to know the provenance and confidence level of each curated binding site.
- **Resolution test** The authors should provide a detailed description of the literature search strategy, inclusion and exclusion criteria, and the number of sites excluded at each step. They should also provide a table or supplementary file listing all curated binding sites with their experimental evidence and literature references.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and accessibility
- **Claim pointer** The manuscript claims that LogoMotif is an open-source database with freely accessible data and tools, and that the underlying code is available via MiniMotif on GitHub.
- **Evidence pointer** Materials and Methods, "Web application implementation" and "Code and data availability"
- **Concern** While the authors state that the database and code are freely available, the manuscript does not provide any evidence that the web interface is functional, that the data can be downloaded in a usable format, or that the code is documented and runnable. No URLs are tested, no data schema is described, and no example queries or outputs are shown. The statement that "novel or newly submitted TFBSs will be made available with regular updates" is vague and does not specify a timeline or mechanism.
- **Why it matters** For a database resource, accessibility and reproducibility are essential. If the web interface is not functional or the data cannot be easily downloaded, the resource will not be used. The lack of documentation and testing details makes it impossible to assess whether the resource is ready for community use.
- **Resolution test** The authors should provide a detailed description of the database schema, the API or download options, and the software dependencies. They should also include a link to a working instance of the web interface and a test case demonstrating how to retrieve data for a specific regulator.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison with existing resources
- **Claim pointer** The manuscript claims that LogoMotif complements existing databases such as Prodoric and RegPrecise, which focus on Firmicutes and Proteobacteria, respectively.
- **Evidence pointer** Discussion section
- **Concern** The authors do not provide a systematic comparison with existing TFBS databases, such as RegPrecise, Prodoric, or CollecTF, in terms of content, coverage, or features. It is unclear how many of the 392 curated binding sites are novel relative to these resources, and whether the prediction models offer any advantage over existing tools.
- **Why it matters** To establish the value of LogoMotif as a new resource, the authors must demonstrate what it adds beyond what is already available. Without a comparison, it is difficult to assess whether the database fills a genuine gap or duplicates existing efforts.
- **Resolution test** The authors should provide a table comparing LogoMotif with existing databases in terms of the number of species, regulators, binding sites, and prediction tools. They should also discuss any unique features, such as the pHMM approach for variable-length motifs, and how these improve upon existing methods.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Abstract and Results section
- **Evidence pointer** Abstract; Results section, "A comprehensive dataset of characterized and predicted actinobacterial regulatory interactions"
- **Issue** The abstract states approximately 400 validated and approximately 12,100 predicted interactions, while the main text states 392 validated and approximately 15,600 predicted interactions. These numbers are inconsistent.
- **Required correction** The authors should reconcile the numbers and ensure that the abstract and main text report the same values.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Materials and Methods, "Data curation"
- **Evidence pointer** Materials and Methods, "Data curation"
- **Issue** The description of the Shannon entropy-based curation step is vague. The authors state that an additional manual curation step was performed if the sum of Shannon's entropy information content scores was less than half the maximum, but they do not explain what this step involved or how it was applied.
- **Required correction** The authors should provide a more detailed description of the curation step, including the exact threshold, the rationale, and the outcome of the manual curation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Materials and Methods, "Construction of computational prediction models"
- **Evidence pointer** Materials and Methods, "Construction of computational prediction models"
- **Issue** The authors state that the default network threshold for the PWM is determined by summing the positions with an information content score exceeding half of the max score, but they do not explain how this threshold relates to the p-value cutoff or how it affects the number of reported predictions.
- **Required correction** The authors should clarify the relationship between the p-value threshold and the information content-based threshold, and explain how the two are used together in the prediction pipeline.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section, "Example use cases"
- **Evidence pointer** Results section, "Example use cases"
- **Issue** The example use cases are described in text but the corresponding figures (Figure 3a and 3b) are not provided in the manuscript text. It is difficult to assess the clarity and utility of the described workflows without seeing the figures.
- **Required correction** The authors should ensure that the figures are included and that the text descriptions align with the visual content.

## Risk / unsupported claims
- The claim of approximately 15,600 predicted regulatory interactions is unsupported without validation metrics or a description of the false positive rate.
- The claim that LogoMotif "serves as a foundation for regulatory predictions" in antiSMASH v7 is not demonstrated with examples or performance data.
- The claim that the database will enable "novel discoveries in the field of actinobacterial biology and beyond" is speculative and not supported by evidence in the manuscript.
- The statement that the database is "continuously and actively updated" is not verifiable from the provided text.
- The claim that the pHMM approach improves prediction accuracy for variable-length spacer regions is not supported by any comparative analysis or benchmark.