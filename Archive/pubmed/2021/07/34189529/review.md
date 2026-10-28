## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and methods as presented in the abstract; no full text, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose an integrative multi-omics approach to construct gene regulatory networks (GRNs) linking AD risk SNPs, transcription factors, and regulatory elements to target genes and modules across three brain regions, with a focus on neuroimmunology and a Covid-19 proxy analysis
- **Visible evidence base** Abstract text only; no quantitative results, validation metrics, or methodological details are available
- **Missing materials affecting confidence** Full manuscript, all figures and tables, supplementary data, code availability, and detailed statistical methods

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting framework for integrating genotype, transcriptomics, and epigenomics to infer gene regulatory mechanisms in AD. The focus on cross-region comparisons and neuroimmunology is timely. However, the abstract lacks sufficient quantitative detail to evaluate the robustness of the methods or the validity of the key claims. The Covid-19 proxy analysis, while creative, raises concerns about causal inference and biological plausibility that cannot be assessed from the provided material.
- **Who would be interested in the results, and why** Researchers in AD genomics, gene regulatory network inference, and neuroimmunology would find this relevant. The potential identification of novel biomarkers for AD-Covid interactions could interest translational researchers, though the evidence base is currently too thin to support clinical implications.
- **Major strengths** The integrative multi-omics design is ambitious and addresses a real gap in linking risk variants to phenotypes. The cross-region comparative analysis is a useful angle, and the open-source availability of results is commendable.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide any statistical measures of GRN prediction accuracy, no validation against experimental data, and no clear definition of how "interruption" of TF binding is determined. The Covid-19 severity classification lacks methodological detail and effect sizes.
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The integration of multi-omics for GRN inference is not entirely novel, but the specific focus on AD neuroimmunology and Covid-19 proxy is somewhat distinctive.
  - Scientific importance: Potentially high if validated, but the current evidence does not establish significance.
  - Interdisciplinary readership: The topic bridges genomics, immunology, and neurology, which could attract a broad audience, but the abstract is too technical for nonspecialists without clearer context.
  - Technical soundness: Not assessable from the abstract; no details on data preprocessing, network inference algorithms, or statistical controls.
  - Readability for nonspecialists: The abstract is dense and assumes familiarity with GRN concepts and AD genetics; it would benefit from clearer framing of the problem and implications.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a promising direction, but the lack of quantitative results and methodological transparency prevents a supportive recommendation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim to "predict GRNs" and identify "SNPs that interrupt TF binding sites," but no details on the prediction method, validation, or error rates are provided.
- **Evidence pointer** Method and Results sections, abstract only
- **Concern** The abstract does not describe how GRNs are constructed or validated. There is no mention of gold-standard comparisons, cross-validation, or statistical significance thresholds for network edges or TF binding disruption.
- **Why it matters** Without validation, the predicted GRNs and SNP effects could be artifacts of the computational pipeline, undermining all downstream claims.
- **Resolution test** Provide precision-recall or AUROC metrics against known regulatory interactions, and demonstrate that predicted TF binding disruptions are enriched for experimentally confirmed effects.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors state that "AD-Covid genes along with linked SNPs can be potential novel biomarkers for neuroimmunology in AD," but the evidence for this is limited to a decision curve analysis with no quantitative results.
- **Evidence pointer** Results section, abstract only
- **Concern** The Covid-19 proxy analysis is used to infer neuroimmunological mechanisms, but the biological link between Covid-19 severity and AD neuroimmunology is not established. The claim of "outperform" is unsupported without specific metrics (e.g., AUC, sensitivity, specificity).
- **Why it matters** Overinterpretation of a proxy analysis could mislead readers into believing a causal or predictive relationship exists where none is demonstrated.
- **Resolution test** Report the full performance metrics for the machine learning model, include confidence intervals, and discuss the biological rationale for why Covid-19 severity is a valid proxy for AD neuroimmunology.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors claim results are "open-source available as a comprehensive functional genomic map," but no data access details or code repository are provided in the abstract.
- **Evidence pointer** Results section, abstract only
- **Concern** The abstract mentions open-source availability but does not specify where the data, code, or interactive map can be accessed. This is critical for reproducibility and for the community to verify the claims.
- **Why it matters** Without access to the resources, the "comprehensive map" cannot be evaluated or reused, limiting the scientific impact.
- **Resolution test** Provide a stable URL or accession number for the data and code, and describe the format and query interface of the functional genomic map.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Background section
- **Evidence pointer** Background, abstract only
- **Issue** The phrase "deeper phenotypes such as disease progression and immune response" is vague; it is unclear what specific phenotypes are analyzed.
- **Required correction** Specify the exact phenotypes (e.g., Braak stage, cognitive decline scores, cytokine levels) used in the analysis.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Readability
- **Affected element** Method section
- **Evidence pointer** Method, abstract only
- **Issue** The term "gene co-expression network" is used without explaining how it is constructed or clustered, which may confuse nonspecialist readers.
- **Required correction** Briefly describe the network inference method (e.g., WGCNA) and the clustering approach in one sentence.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section
- **Evidence pointer** Results, abstract only
- **Issue** The abstract mentions "comparative analyses revealed cross-region-conserved and region-specific GRNs," but does not state how many genes or networks are conserved or specific.
- **Required correction** Include a summary statistic, such as the number of conserved versus specific edges or modules, to give readers a sense of scale.

## Risk / unsupported claims
- The claim that specific SNPs "disrupt" TF binding is unsupported without experimental or computational validation details.
- The claim that AD-Covid genes "outperform" known Covid-19 genes is unsupported without quantitative metrics.
- The claim of a "comprehensive functional genomic map" is unverifiable without access information.
- The biological relevance of using Covid-19 as a proxy for AD neuroimmunology is not justified in the abstract.