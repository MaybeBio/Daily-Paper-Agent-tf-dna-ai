## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Database resource paper describing the updated Factorbook catalog
- **Shared manuscript claim summary** The authors present an updated version of Factorbook, a transcription factor-centric database, with expanded motif catalogs derived from ENCODE Phase II/III ChIP-seq and HT-SELEX data, genome-wide candidate regulatory motif sites integrated with the ENCODE cCRE registry, and novel tools for machine learning integration, variant annotation, and heritability analysis.
- **Visible evidence base** Abstract, Introduction, Overview, sections on motif catalog construction, genome-wide motif instances in ChIP-seq peaks and cCREs, GWAS integration tools, nucleosome/epigenetic profiling, machine learning tools, genomic visualization, future plans, data availability, funding
- **Missing materials affecting confidence** Methods section, figures, supplementary data, detailed statistical analyses, validation metrics, comparison details

## Reviewer
- **Overall assessment** This manuscript describes a substantial update to the Factorbook database, a valuable community resource for transcription factor motif analysis. The authors have significantly expanded coverage of TFs and cell types, integrated motifs with the ENCODE cCRE registry, and added novel functionality including deep learning-derived motifs and heritability analysis tools. The resource addresses a clear need in the regulatory genomics community. However, the manuscript as presented lacks critical methodological detail and quantitative validation that would be necessary to fully assess the quality and utility of the resource. The claims of novelty and comprehensiveness require stronger evidence, particularly regarding the ZMotif pipeline, which is described as "manuscript in preparation," and the comparative analyses against existing databases.

- **Who would be interested in the results, and why** Researchers in regulatory genomics, transcription factor biology, and computational biology would find this resource valuable. Specifically, those studying gene regulation, developing deep learning models for regulatory sequence analysis, interpreting non-coding variants from GWAS, and those working with ENCODE data would benefit from the expanded motif catalog and integrated tools. The heritability analysis functionality would appeal to statistical geneticists, and the machine learning integration tools would interest computational biologists developing predictive models.

- **Major strengths**
  1. The resource addresses a clear community need for comprehensive, integrated TF motif resources
  2. Substantial expansion in TF and cell type coverage compared to the previous version
  3. Novel integration of ChIP-seq and HT-SELEX derived motifs with the ENCODE cCRE registry
  4. Practical tools for variant annotation and heritability analysis with demonstrated biological relevance
  5. Public availability and planned continued expansion with ENCODE Phase IV

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the ZMotif pipeline identifies motifs from HT-SELEX data that can be used in downstream analysis with deep learning frameworks and conventional tools.
- **Evidence pointer** Overview section, "A comprehensive motif catalog derived from ChIP-seq and HT-SELEX data" section
- **Concern** The ZMotif pipeline is described as "manuscript in preparation," yet it is a cornerstone of the updated Factorbook resource. No methodological details, validation results, or performance benchmarks are provided. The quality and reliability of the 6700 motifs derived from this pipeline cannot be assessed without this information.
- **Why it matters** The scientific validity of a major component of the resource depends on the quality of the ZMotif pipeline. Users would be incorporating potentially unvalidated motif models into their analyses, which could lead to erroneous conclusions. The lack of peer-reviewed validation for a core analytical tool undermines confidence in the resource.
- **Resolution test** Provide a detailed description of the ZMotif architecture, training procedure, and validation results, including comparisons against established motif discovery methods. Ideally, the ZMotif manuscript should be published or at least available as a preprint with full methodological details before this resource paper is accepted.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the Factorbook motif catalog includes nearly 100% of the motifs in HOCOMOCO and JASPAR, and further identifies novel motifs not present therein.
- **Evidence pointer** "A comprehensive motif catalog derived from ChIP-seq and HT-SELEX data" section, Figure 2B
- **Concern** The claim of "nearly 100%" coverage of HOCOMOCO and JASPAR motifs is presented without quantitative details. The comparison methodology is not described, and the threshold for "coverage" is unclear. Additionally, the claim of novel motifs for 101 TFs previously classified as "likely sequence-specific factors" requires validation that these are genuine binding motifs rather than artifacts.
- **Why it matters** These claims establish the comprehensiveness and novelty of the resource relative to existing databases. Without rigorous quantitative comparison, users cannot assess whether Factorbook provides added value over existing resources. Overstated coverage claims could mislead users into assuming completeness when significant gaps may exist.
- **Resolution test** Provide a detailed comparison table showing the number of TFs with motifs in Factorbook versus HOCOMOCO and JASPAR, the overlap statistics, and the methodology for determining motif similarity. For the novel motifs, provide validation evidence such as independent experimental support or strong conservation signals.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that motif instances in cCREs and rDHSs that are not present in ChIP-seq peaks are "true transcription factor binding sites which would be identified if ChIP-seq were performed in the correct biological context."
- **Evidence pointer** "Genome-wide motif instances in candidate cis-regulatory elements" section, Figure 4C-D
- **Concern** This is a strong functional claim based on indirect evidence. The authors show that these motif instances are more conserved and less accessible to DNase I, but this does not establish that they are actual TF binding sites. Many conserved, DNase-protected sequences may not be bound by TFs in any context, and the absence of ChIP-seq evidence could reflect technical limitations or genuine absence of binding.
- **Why it matters** This claim overstates the biological significance of the predicted motif sites. Users may interpret these as validated binding sites rather than computational predictions, leading to overinterpretation of functional relevance in downstream analyses.
- **Resolution test** Soften the claim to reflect that these are candidate binding sites with supporting evidence, or provide direct experimental validation for a subset of these sites. Alternatively, provide computational evidence such as motif activity analysis or comparison with independent binding assays.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that the heritability analysis functionality provides novel insights into disease-relevant TF motifs.
- **Evidence pointer** "Tools for integrating motifs with GWAS results" section, Figure 5D
- **Concern** The heritability analysis results are presented as illustrative examples, but the biological interpretation is limited. The authors show enrichment of heritability in cell-type-specific motifs, but do not discuss potential confounding factors, statistical significance thresholds, or comparison with existing heritability partitioning methods.
- **Why it matters** The heritability analysis is presented as a key novel feature, but without proper statistical context and validation, users may not understand the limitations of this approach. Overinterpretation of cell-type-specific enrichment could lead to incorrect biological conclusions.
- **Resolution test** Provide statistical significance measures for the heritability enrichments, discuss potential confounders, and compare results with existing methods such as baseline-LD models. Include guidance on appropriate interpretation of results.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that aggregating around motif instances rather than peak summits improves the resolution and phasing of epigenetic signals.
- **Evidence pointer** "High-resolution nucleosome and epigenetic profiles around binding sites" section, Figure 6A-B
- **Concern** The improvement in resolution is described qualitatively without quantitative comparison. The biological significance of the observed asymmetry in nucleosome positioning around CTCF motifs is not discussed in sufficient depth.
- **Why it matters** This is presented as a methodological improvement over the previous version, but without quantitative evidence, users cannot assess whether this change provides meaningful benefits for their analyses.
- **Resolution test** Provide quantitative metrics comparing signal resolution and phasing between motif-centered and peak-summit-centered aggregation. Discuss the biological implications of observed asymmetries with appropriate literature support.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract does not mention the specific number of TFs covered or the number of motif instances cataloged, which are key quantitative highlights of the resource.
- **Required correction** Include key quantitative metrics in the abstract to give readers a clearer sense of the resource scope.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Motif quality metrics
- **Evidence pointer** "Genome-wide instances of motifs in ChIP-seq peaks" section
- **Issue** The quality metrics for motif instances are described but not validated. The claim that high-quality instances are "central within peaks, more evolutionarily conserved, and less accessible" is presented without statistical testing.
- **Required correction** Provide statistical comparisons between high-quality and low-quality motif instances for each metric.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure descriptions
- **Evidence pointer** Figures 1-7
- **Issue** Figure descriptions in the text are brief and do not fully explain the visualizations, particularly for readers unfamiliar with the data types.
- **Required correction** Expand figure legends and in-text descriptions to make the visualizations more accessible to nonspecialists.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Comparison with existing resources
- **Evidence pointer** Introduction, "A comprehensive motif catalog derived from ChIP-seq and HT-SELEX data" section
- **Issue** The comparison with existing resources such as HOCOMOCO and JASPAR is limited to motif coverage. No comparison of usability, data formats, or additional features is provided.
- **Required correction** Include a more comprehensive comparison table or discussion of how Factorbook differs from and complements existing resources.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Technical terminology
- **Evidence pointer** Various sections
- **Issue** Some technical terms such as "irreproducible discovery rate" and "partitioned LD score regression" are used without brief explanations for nonspecialist readers.
- **Required correction** Add brief definitions or explanations for key technical terms on first use.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Data availability
- **Evidence pointer** Data Availability section
- **Issue** The data availability statement is minimal and does not specify the exact formats, file sizes, or update schedules for the downloadable data.
- **Required correction** Provide more detailed information about data formats, versioning, and expected update frequency.

## Risk / unsupported claims
- The claim that ZMotif-derived motifs are suitable for transfer learning in deep learning applications is unsupported without validation of the learned filters.
- The claim that "nearly 100%" of HOCOMOCO and JASPAR motifs are covered by the Factorbook catalog is unquantified and lacks methodological detail.
- The claim that motif instances in cCREs not found in ChIP-seq peaks represent "true transcription factor binding sites" is overinterpreted from indirect evidence.
- The claim that aggregating around motif instances improves resolution of epigenetic signals is not quantitatively supported.
- The heritability enrichment results are presented without statistical significance testing or comparison with existing methods.
- The novelty of the machine learning integration tools relative to existing frameworks is not clearly established.
- The planned expansion to ENCODE Phase IV data is mentioned but no timeline or specific plans are provided.