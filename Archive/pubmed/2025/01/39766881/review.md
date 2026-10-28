## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and conclusions
- **Assessment boundary** Scientific content, methodological rigor, evidence quality, and internal consistency of the reported analyses
- **Shared manuscript claim summary** The authors report a genome-wide identification and evolutionary analysis of BBM-like (BBML) genes across 10 plant species, identifying 24 BBML proteins, characterizing their phylogenetic relationships, gene structures, conserved motifs, cis-acting elements, miRNA binding sites, duplication events, protein–protein interactions, 3D structures, molecular docking, and expression patterns. They conclude that segmental duplication drove BBML expansion, purifying selection shaped their evolution, and tissue-specific expression implies roles in root and embryo development.
- **Visible evidence base** Main text figures (Figures 1–8), supplementary tables referenced (Tables S1–S8), supplementary figures referenced (Figures S1–S3), and methodological descriptions in Section 2
- **Missing materials affecting confidence** Supplementary materials (Tables S1–S8, Figures S1–S3) were not provided for inspection. Raw sequence data, alignment files, phylogenetic tree files, and statistical outputs were not available. Expression data source details and quality metrics were not fully described.

## Reviewer

- **Overall assessment** This manuscript presents a descriptive bioinformatics survey of BBML genes across 10 plant species. The work is competent in its application of standard comparative genomics tools, but the scientific advance over existing literature is modest. The core claims regarding evolutionary conservation, duplication mechanisms, and expression specificity are largely consistent with prior knowledge of BBM genes. The manuscript would benefit from clearer hypothesis-driven framing, stronger validation of key findings, and more careful interpretation of several analyses. The paper is likely of interest to researchers working on plant transcription factors, somatic embryogenesis, and apomixis, but the current evidence base does not fully establish several of the broader conclusions drawn.

- **Who would be interested in the results, and why** Researchers studying plant transcription factor families, particularly the AP2/ERF superfamily, will find the phylogenetic and structural characterization useful as a reference. Those working on somatic embryogenesis, transformation efficiency improvement, and apomixis engineering will be interested in the expression patterns and conserved motif data. The comparative analysis across monocots and eudicots may also appeal to evolutionary biologists studying gene family dynamics following whole-genome duplication events.

- **Major strengths**
  1. The study covers a reasonable taxonomic breadth with 10 species spanning basal angiosperms, monocots, and eudicots.
  2. The analytical pipeline is comprehensive, integrating phylogenetics, gene structure, regulatory element prediction, duplication analysis, and protein interaction modeling.
  3. The identification of conserved bbm-1 motifs and AP2 domain architecture provides useful reference data.
  4. The expression analysis across multiple tissues in five species offers a consistent comparative view of BBML transcriptional patterns.
  5. The molecular docking approach, while preliminary, represents an attempt to move beyond purely sequence-based inference.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that "whole genome/segmental duplication were the primary drivers of BBML genes' evolution in the tested species."
- **Evidence pointer** Section 3.5, Table 1, Figure 4
- **Concern** The duplication analysis relies on MCScanX with default parameters, but the manuscript does not report key parameters such as the minimum number of gene pairs required for a syntenic block, the maximum gap size, or the significance thresholds used. More critically, the claim that segmental duplication is the "primary driver" requires a quantitative comparison with other duplication modes (tandem, dispersed, proximal). The manuscript does not provide a breakdown of duplication types for each species, nor does it report the proportion of BBML genes attributable to each mechanism.
- **Why it matters** The central evolutionary conclusion of the paper rests on this claim. Without a rigorous classification of duplication modes and a statistical comparison, the conclusion is not adequately supported. Tandem duplications, for example, are known to contribute to transcription factor family expansion in plants and should be explicitly quantified.
- **Resolution test** Provide a complete duplication mode classification for all 24 BBML genes across all 10 species, with clear criteria for each category. Report the relative proportions of each duplication type and perform a statistical test (e.g., chi-square or Fisher's exact test) to support the claim that segmental duplication is significantly more prevalent than other modes.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the expression patterns of BBML genes revealed significant tissue specificity, particularly in the root and embryo."
- **Evidence pointer** Section 3.8, Figure 8
- **Concern** The expression analysis is based on publicly available RNA-seq data, but the manuscript does not describe the specific datasets used, the number of biological replicates, the tissue types and developmental stages sampled, or the normalization method applied. The claim of "significant tissue specificity" implies statistical testing, yet no statistical analysis is described. The figure appears to show heatmaps or bar plots, but without access to the underlying data or statistical comparisons, the claim cannot be evaluated.
- **Why it matters** Tissue-specific expression is a key functional inference in this study. If the conclusion is based on visual inspection of expression values without statistical support, it is not a rigorous finding. Moreover, the choice of tissues and developmental stages varies across species, which complicates direct comparison.
- **Resolution test** Describe the RNA-seq datasets used for each species, including accession numbers, tissue types, developmental stages, and replicate numbers. Report the normalization method and perform differential expression analysis (e.g., DESeq2 or edgeR) to statistically test for tissue specificity. Provide adjusted p-values or effect sizes for the claimed tissue-specific patterns.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors state that "the expansion of the BBMLs mainly occurred via segmental duplication events and undergoing strong purification selection."
- **Evidence pointer** Section 3.5, Tables 1 and S5
- **Concern** The Ka/Ks analysis reports values ranging from 0.0588 to 0.3811, which the authors interpret as evidence of purifying selection. However, the manuscript does not report the standard errors or confidence intervals for these estimates, nor does it describe how many synonymous substitutions were observed for each pair. For pairs with very few synonymous substitutions, Ka/Ks estimates are unreliable. Additionally, two pairs are reported as NaN due to "high sequence divergence," but the authors do not explain how these pairs were treated in the interpretation.
- **Why it matters** The strength of the purifying selection claim depends on the reliability of Ka/Ks estimates. Without measures of uncertainty or information on substitution counts, the reader cannot assess whether the values are meaningfully different from 1 or from each other. The treatment of NaN pairs is also unclear and could bias the interpretation.
- **Resolution test** Report the number of synonymous and nonsynonymous substitutions for each gene pair, along with standard errors or confidence intervals for Ka/Ks estimates. Provide a clear explanation for the NaN pairs and state whether they were excluded from the analysis or treated separately. Consider using a more robust method such as PAML or codeml for selection analysis.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors conclude that "our research delved into the molecular mechanism, evolutionary relationships, functional differentiation, and expression patterns of BBML genes across plants, laying the groundwork for further investigations."
- **Evidence pointer** Sections 4 and 5
- **Concern** The manuscript is largely descriptive and does not generate testable hypotheses or novel biological insights beyond what is already known about BBM genes. The finding that BBML genes are conserved, expressed in embryos and roots, and evolved under purifying selection is consistent with prior studies in Arabidopsis, rice, and maize. The molecular docking and protein interaction predictions are speculative and not experimentally validated. The paper does not identify new functional domains, regulatory mechanisms, or evolutionary scenarios that would substantially advance the field.
- **Why it matters** For a genome-wide survey to be impactful, it should either reveal unexpected patterns, provide a comprehensive resource that enables new experiments, or generate hypotheses that can be tested. The current manuscript does not clearly articulate what is novel about its findings relative to existing literature, and the discussion does not position the work within a broader conceptual framework.
- **Resolution test** Clearly articulate in the introduction and discussion what specific knowledge gap this study fills. Provide explicit hypotheses generated by the data that can be experimentally tested. Highlight any unexpected findings (e.g., lineage-specific expansions, unusual motif arrangements, or novel regulatory elements) that challenge current understanding.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1
- **Evidence pointer** "The multiple sequence alignment of identified AP2 proteins was operated by Muscle v5 with the default parameters"
- **Issue** The phrase "was operated by" is awkward and unclear. It should be "was performed using" or "was conducted with."
- **Required correction** Revise to "Multiple sequence alignment of identified AP2 proteins was performed using MUSCLE v5 with default parameters."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.4
- **Evidence pointer** "TBtools' simple Ka/Ks calculator was employed to compute the synonymous (Ks) and nonsynonymous (Ka) mutation rates"
- **Issue** The manuscript does not specify the version of TBtools used or the parameters for the Ka/Ks calculation (e.g., the genetic code, the method for estimating substitutions). This limits reproducibility.
- **Required correction** Specify the TBtools version and provide the parameters used for Ka/Ks calculation, or cite the original method (e.g., Yang and Nielsen 2000).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.1
- **Evidence pointer** "The analysis identified 249 proteins whose sequence contained two AP2 domains."
- **Issue** The manuscript does not report how many AP2 proteins were initially identified before filtering, nor the criteria for retaining a representative transcript per gene. This information is important for assessing the completeness of the identification.
- **Required correction** Report the initial number of AP2 candidates identified, the filtering criteria applied, and the number retained after removing redundant transcripts.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 3.6
- **Evidence pointer** "The significantly enriched gene ontology (GO) terms showed that interacting proteins in A. thaliana and G. max were mainly described as being involved the regulation of circadian rhythm"
- **Issue** The connection between circadian rhythm regulation and BBML function is not explained or discussed. This finding appears disconnected from the known roles of BBM in embryogenesis and could be a spurious enrichment.
- **Required correction** Provide interpretation of why circadian rhythm-related GO terms are enriched among BBML interactors, or acknowledge this as an unexpected finding that requires further investigation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.6
- **Evidence pointer** "AlphaFold3 was utilized to model three-dimensional structures of BBML proteins and selected interacting proteins."
- **Issue** The manuscript does not describe the confidence metrics (e.g., pLDDT scores) for the predicted structures. Without this information, the reliability of the structural models and subsequent docking results cannot be assessed.
- **Required correction** Report pLDDT scores or other confidence measures for the predicted structures, and discuss any regions of low confidence that may affect the docking interpretation.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.2
- **Evidence pointer** "Among all branches, 14 genes possessed both 3′ and 5′ untranslated regions (UTRs), whereas BBMLs from A. trichofila, A. tatarinowii, N. nucifera, V. vinifera, and S. lycopersicum lacked a UTR sequence."
- **Issue** The sentence is confusing. It is unclear whether the 14 genes with UTRs are a subset of the 24 total, and whether the statement about lacking UTRs applies to all genes in those species or only some. The phrasing "lacked a UTR sequence" is also imprecise.
- **Required correction** Clarify the distribution of UTR presence/absence across all 24 genes, and specify whether the absence of UTRs is a feature of the gene models or an artifact of incomplete annotation.

## Risk / unsupported claims
- The claim that segmental duplication is the "primary driver" of BBML evolution is not quantitatively supported without a full duplication mode classification.
- The claim of "significant tissue specificity" is unsupported without statistical testing.
- The interpretation of Ka/Ks values as evidence of "strong purifying selection" lacks measures of uncertainty.
- The functional significance of the molecular docking results is speculative and not experimentally validated.
- The statement that "the expansion of the BBMLs mainly occurred via segmental duplication events" is not supported by a comparison with other duplication mechanisms.
- The conclusion that BBML functions differ between monocots and eudicots based on GO enrichment of interactors is weakly supported, as the enrichment analysis was only performed for four of the ten species and the connection to BBML function is unclear.
- The claim that "BBML genes were greatly influenced by purification selection" contains a typographical error ("purification" should be "purifying") and the strength of the claim is not justified by the data presented.