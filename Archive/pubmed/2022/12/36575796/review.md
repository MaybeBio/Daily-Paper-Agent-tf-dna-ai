## Review setup

- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report construction of a wheat integrative gene regulatory network (wGRN) combining updated genome annotation with diverse functional datasets, containing 7.2 million interactions across 5947 transcription factors and 127,439 target genes. They claim validation via known regulatory relationships, condition-specific expression, gene functional information, and experiments; assignment of genes to 3891 biological pathways; prioritization of trait-associated candidate genes in genome-wide association studies; enhanced interpretation of a spike temporal transcriptome dataset; identification of novel regulators improving spike phenotypic trait prediction via machine learning; and provision of an interactive webserver.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or supplementary data provided
- **Missing materials affecting confidence** Full manuscript, all figures and tables, methods description, validation experiment details, machine learning approach and performance metrics, webserver functionality, and any statistical analyses

## Reviewer

- **Overall assessment** The abstract describes a potentially valuable community resource for wheat functional genomics. The scale of the network and the integration of multiple data types are commendable. However, the abstract alone provides insufficient detail to assess the technical rigor of network construction, the validity of validation approaches, or the robustness of the trait-associated gene discovery claims. Several assertions, particularly regarding validation and predictive performance, cannot be evaluated without access to the underlying data and methods.
- **Who would be interested in the results, and why** Wheat geneticists and breeders interested in trait-associated gene discovery; plant systems biologists studying gene regulatory networks; computational biologists developing integrative network approaches for crops; and the broader plant science community seeking resources for functional annotation and candidate gene prioritization.
- **Major strengths** The integration of multiple complementary functional data types is a sound strategy for improving network coverage and reliability. The reported scale of the network, covering nearly 6000 transcription factors and over 127,000 target genes, represents a substantial resource. The provision of an interactive webserver enhances community accessibility and utility. The application to spike phenotypic trait prediction using machine learning demonstrates a practical translational direction.
- **Major Concerns** The abstract lacks quantitative evidence for validation claims, provides no details on how network interactions were scored or thresholded, and does not specify the machine learning framework or its performance metrics. The claim of accurate prioritization of trait-associated genes is not supported by specific examples or statistical measures. The biological significance of the novel regulators is asserted without functional validation details.
- **Minor Comments** The abstract would benefit from clearer specification of the wheat accessions used for phenotypic prediction. The relationship between the spike temporal transcriptome dataset and the integrative network could be more explicitly described. The webserver URL is provided, but no usage statistics or user features are mentioned.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The integrative approach combining multiple functional datasets for wheat is novel in scope, though similar strategies exist in model systems. Scientific importance: High potential importance for wheat improvement, but importance is contingent on demonstrated reliability and utility. Interdisciplinary readership: Likely to appeal to plant molecular biologists, geneticists, and computational biologists. Technical soundness: Cannot be assessed from the abstract alone; validation and methodology details are essential. Readability for nonspecialists: The abstract is generally accessible, though some terms such as "chromatin accessibility" and "evolutionarily conserved regulation" may require background knowledge.
- **Recommendation posture** Supportive if technical concerns are resolved; currently not established from the provided evidence

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim the network was "further verified using known regulatory relationships, condition-specific expression, gene functional information, and experiments."
- **Evidence pointer** Abstract; location not provided
- **Concern** The abstract provides no quantitative results from these verification approaches. No enrichment statistics, precision-recall values, or experimental outcomes are reported. The phrase "verified" is used without specifying what proportion of interactions were tested or what thresholds defined success.
- **Why it matters** Verification is central to establishing network reliability. Without quantitative evidence, readers cannot judge whether the network is sufficiently accurate for downstream trait-associated gene discovery.
- **Resolution test** Provide specific validation metrics, such as overlap with known regulatory interactions, enrichment of condition-specific expression patterns, functional coherence scores, and results from experimental validation including number of tested and confirmed interactions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim wGRN was used to "accurately prioritize candidate genes associated with complex phenotypic traits in genome-wide association studies."
- **Evidence pointer** Abstract; location not provided
- **Concern** No details are given on the trait(s) analyzed, the number of loci examined, the prioritization method, or the accuracy metrics used. The term "accurately" is unsupported without comparison to baseline methods or independent validation.
- **Why it matters** The translational value of the network depends on demonstrated improvement over existing prioritization approaches. Without benchmarks, the claim of accuracy cannot be evaluated.
- **Resolution test** Describe the GWAS dataset, the prioritization algorithm, and provide quantitative comparisons against alternative methods, including receiver operating characteristic curves, precision-recall, or validated hit rates.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim "novel regulators that enhance the power of spike phenotypic trait prediction using machine learning."
- **Evidence pointer** Abstract; location not provided
- **Concern** The machine learning framework is not described, including the feature set, model type, training and test partitions, or performance metrics. The improvement in prediction power is not quantified.
- **Why it matters** Predictive modeling claims require clear methodological detail and performance statistics to be reproducible and credible. Without these, the contribution of the novel regulators cannot be assessed.
- **Resolution test** Specify the machine learning approach, input features, cross-validation scheme, and report prediction accuracy or correlation metrics with and without the novel regulators.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state the network was constructed by combining "an updated genome annotation and diverse complementary functional datasets."
- **Evidence pointer** Abstract; location not provided
- **Concern** No information is provided on the data sources, preprocessing steps, interaction scoring methods, or thresholds used to define the 7.2 million interactions. The criteria for including a transcription factor or target gene are unspecified.
- **Why it matters** Reproducibility is a core requirement for community resources. Without methodological transparency, other researchers cannot reconstruct or independently evaluate the network.
- **Resolution test** Provide a detailed methods section describing all input datasets, normalization procedures, interaction inference algorithms, and significance thresholds.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract statement on pathway assignment
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states genes were assigned to 3891 biological pathways but does not indicate the pathway database or ontology used.
- **Required correction** Specify the pathway annotation source and the method of assignment.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract statement on spike phenotypic differences
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract mentions "spike phenotypic differences among modern wheat accessions" but does not specify the number of accessions or the phenotypic traits measured.
- **Required correction** Provide accession count and trait descriptions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Webserver description
- **Evidence pointer** Abstract; location not provided
- **Issue** The webserver is mentioned with a URL, but no details on query types, output formats, or data download options are given.
- **Required correction** Briefly describe the main functionalities of the webserver.

## Risk / unsupported claims

- The claim that the network was "verified" using multiple approaches is unsupported without quantitative validation data.
- The claim of "accurate" prioritization of trait-associated genes is unsupported without benchmark comparisons.
- The claim that novel regulators "enhance the power" of phenotypic prediction is unsupported without model performance metrics.
- The biological significance of the novel regulators contributing to spike phenotypic differences is asserted without functional evidence.
- The overall utility of the network as a community resource cannot be fully assessed without methodological transparency and validation details.