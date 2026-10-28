## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, discussion, and supplementary table/figure legends as provided.
- **Assessment boundary** Scientific validity, methodological soundness, interpretation of results, and alignment with claims made in the abstract and discussion. No assessment of formatting or editorial style beyond readability.
- **Shared manuscript claim summary** The authors propose that TF footprinting of ATAC-seq data, using the TOBIAS tool, can identify novel cis-regulatory elements (CREs) in the Drosophila embryo. They report that most footprinted TF binding sites lie outside known enhancers, and that clusters of footprints, filtered by conservation and histone marks, yield candidate CREs. Five candidates were validated by reporter assays, all showing patterned expression.
- **Visible evidence base** Abstract, introduction, methods (partial), results (narrative), discussion, data availability statement, funding, and supplementary table/figure legends. No raw data, no full figure panels, no detailed statistical outputs, no full methods for all steps.
- **Missing materials affecting confidence** Full methods for TOBIAS parameter settings, detailed statistical tests, raw ATAC-seq processing details, complete reporter assay protocols, full figure panels with scale bars and controls, and supplementary tables (S1–S5) referenced but not provided. These omissions limit independent verification of several key claims.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and practical question: can existing ATAC-seq data be mined for novel CREs using footprinting tools? The authors use a well-characterized system (Drosophila segmentation) as a test bed, which is appropriate. The finding that most footprints lie outside known enhancers is interesting, and the validation of five candidates is encouraging. However, several methodological details are under-specified, and the interpretation of the negative control (footprint-free region driving expression) raises questions about the specificity of the pipeline. The claim that this approach "can uncover new regulatory regions" is supported, but the broader utility and false-positive rate remain unclear from the provided evidence.
- **Who would be interested in the results, and why** Researchers studying gene regulation, enhancer biology, and chromatin accessibility. Those working on Drosophila development specifically will find the validation data relevant. The broader community interested in repurposing ATAC-seq data for regulatory element discovery may also find the pipeline useful, though the generalizability to other systems is not demonstrated.
- **Major strengths** 1. The study addresses a practical gap: using ATAC-seq footprinting to find new CREs, which is timely given the abundance of ATAC-seq data. 2. The use of a well-annotated system (Drosophila) allows for meaningful comparison against known enhancers. 3. The inclusion of functional validation (reporter assays) for five candidates strengthens the claim that the pipeline can identify active regulatory elements. 4. The authors acknowledge limitations, including conservation bias and potential false negatives.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (specificity of footprint clusters), R1-M2 (negative control interpretation), R1-M3 (motif selection and validation), R1-M4 (statistical rigor for enrichment).
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. The idea of using footprinting to find CREs is not entirely new, but the specific application to ATAC-seq data in a well-characterized system, with validation, adds some novelty.  
  - Scientific importance: Moderate. The approach could be useful, but the study does not demonstrate broad applicability beyond Drosophila, and the false-positive rate is unclear.  
  - Interdisciplinary readership: Limited. The work is primarily of interest to developmental biologists and genomics researchers.  
  - Technical soundness: Partially sound. The core pipeline is reasonable, but several methodological details are under-specified, and the negative control result complicates interpretation.  
  - Readability for nonspecialists: Acceptable. The writing is clear, but some sections (e.g., footprinting methods) assume familiarity with the tools.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising, and the validation data are encouraging, but the current evidence does not fully establish the specificity and generalizability of the approach.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The authors claim that "TF footprint clusters may be uncharacterized CREs" and that their pipeline identifies candidate CREs with high confidence.
- **Evidence pointer** Results section "TF footprint clusters may be uncharacterized CREs"; Methods "Candidate Cis-regulatory Element (cCRE) Search"
- **Concern** The initial search for footprint clusters using parameters derived from known enhancers (14 footprints, 11 bp spacing) yielded no clusters beyond known enhancers. The authors then relaxed the criteria to 7 footprints and 18 bp spacing, which yielded 450 clusters. This relaxation is substantial and may increase the false-positive rate. The rationale for the relaxed thresholds is only partially justified (median across all CREs and a previous report). It is unclear how sensitive the results are to these parameter choices, and whether the final 41 cCREs are robust to small changes in thresholds.
- **Why it matters** The core claim is that the pipeline can identify novel CREs. If the thresholds are arbitrary or overly permissive, the specificity of the pipeline is questionable, and the number of false positives could be high. This directly affects the utility of the approach for other systems.
- **Resolution test** Provide a sensitivity analysis showing how the number of cCREs changes with varying footprint count and spacing thresholds. Additionally, justify the relaxed thresholds with reference to known enhancer properties or provide a statistical framework for cluster definition.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of results
- **Claim pointer** The authors state that "the footprint-free region of open chromatin drove a distinct pair-rule like pattern of gene expression" and interpret this as a potential false negative of the pipeline.
- **Evidence pointer** Results section "Reporter assays confirm the in vivo activity of hCREs"; Discussion "Study limitations"
- **Concern** The negative control (footprint-free region) driving patterned expression is a significant issue. The authors offer several possible explanations, but do not test any of them. This result suggests that the pipeline may miss functional regulatory elements, which is not fully reconciled with the claim that the approach is useful for finding novel CREs. The possibility that the region acts as a "shadow enhancer" or that the reporter assay is prone to false positives is not addressed experimentally.
- **Why it matters** If the negative control can drive expression, the specificity of the pipeline is called into question. The authors need to either demonstrate that this is an isolated case or provide additional controls to rule out systematic false negatives or assay artifacts.
- **Resolution test** Perform additional validation on the footprint-free region, such as testing it in a different genomic context or with a different reporter, to determine if the activity is reproducible. Alternatively, provide a larger set of negative controls to assess the baseline activity of footprint-free regions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Data quality and methodology
- **Claim pointer** The authors state that "to assess which TF motif yielded the most accurate predictions, we compared TF footprints to orthogonal ChIP-seq datasets" and used the motif with the fewest unique predicted binding sites for TFs lacking ChIP-seq data.
- **Evidence pointer** Methods "TF Motif Collection and Testing"; Supplementary Tables S1–S3
- **Concern** The selection of motifs based on ChIP-seq overlap or fewest unique sites is pragmatic, but the criteria are not fully validated. For TFs without ChIP-seq data, the "fewest unique sites" criterion may bias toward motifs that are too restrictive, potentially missing true binding sites. Additionally, the quality of the ChIP-seq datasets used for comparison is not described (e.g., stage matching, antibody quality). The impact of motif choice on the final footprint clusters is not assessed.
- **Why it matters** The accuracy of footprinting depends heavily on motif quality. If motifs are poorly chosen, the footprint calls may be unreliable, affecting all downstream analyses and the final cCRE list.
- **Resolution test** Provide a comparison of footprint calls using different motifs for a subset of TFs, and show how the final cCRE list changes. Also, describe the ChIP-seq datasets used for validation, including stage and quality metrics.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors report that promoters, CREs, and 5' UTRs are "significantly enriched with TF footprints" based on a chi-square test.
- **Evidence pointer** Results section "The majority of TF footprints lie outside of characterized CREs"; Figure 1D
- **Concern** The statistical test is described only briefly. It is unclear how the expected values were calculated, whether the test accounts for multiple comparisons across genomic features, and whether the effect sizes are meaningful. The post-hoc test with Bonferroni correction is mentioned, but the details are not provided.
- **Why it matters** The enrichment analysis is used to support the claim that footprints are concentrated in known regulatory regions, which is a key part of the validation. Without proper statistical rigor, this claim is weakened.
- **Resolution test** Provide full details of the chi-square test, including expected value calculation, degrees of freedom, and effect sizes. Also, report the results of the post-hoc tests for each genomic feature.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods "ATAC-seq Dataset"
- **Evidence pointer** Methods "ATAC-seq Dataset"
- **Issue** The description of the ATAC-seq data processing is minimal. It is unclear how the data were aligned, filtered, and how footprints were called. The authors state that coverage was 50-90 million reads, but do not describe the bioinformatics pipeline in detail.
- **Required correction** Provide a more detailed description of the ATAC-seq processing and footprint calling steps, including software versions and parameters.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data and Code Availability
- **Evidence pointer** Data and Code Availability
- **Issue** The authors state that scripts and BED files are available on GitHub, but the link is not verified. Additionally, the raw ATAC-seq data are not mentioned as being deposited in a public repository.
- **Required correction** Confirm the GitHub link is active and provide accession numbers for the raw ATAC-seq data.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion "A potential regulatory role of TF footprints in 5' UTRs"
- **Evidence pointer** Discussion "A potential regulatory role of TF footprints in 5' UTRs"
- **Issue** The discussion of 5' UTR footprints is speculative. The authors suggest a potential regulatory role but do not provide functional evidence or a clear hypothesis for how these footprints might act.
- **Required correction** Either provide additional data to support the speculation or temper the language to clearly indicate this is a hypothesis for future work.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 3
- **Evidence pointer** Results "Reporter assays confirm the in vivo activity of hREs"
- **Issue** The figure legend is not provided in the manuscript text. It is unclear what the panels show, what the scale bars represent, and how the expression patterns were scored.
- **Required correction** Provide a full figure legend for Figure 3, including details on the reporter construct, the number of embryos imaged, and the criteria for scoring expression patterns.

## Risk / unsupported claims
- The claim that "this approach may be helpful in using existing ATAC-seq data to find novel CREs" is supported by the five validated candidates, but the false-negative rate (as suggested by the footprint-free region driving expression) is not addressed.
- The claim that "most footprinted TF binding sites lie outside of known enhancers" is supported by the data, but the biological significance of this observation is not explored.
- The claim that 5' UTRs have a high density of TF footprints is supported, but the functional relevance is speculative.
- The generalizability of the pipeline to other organisms or cell types is not demonstrated and should not be inferred from the current data.