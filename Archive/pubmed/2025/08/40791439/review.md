## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Results, Discussion, Methods, Resource Availability) as provided
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text. No external data or supplementary files were available for verification.
- **Shared manuscript claim summary** The authors used massively parallel reporter assays (MPRAs) to identify ~2,000 cis-regulatory elements (CREs) across 27 double-stranded DNA viruses from four families. They report that viral genomes have higher CRE density than the human genome, that most viral CREs are promoter-like, that many overlap protein-coding sequences, and that regulatory architecture differs across viral families and types. They further identify transcription factor motifs contributing to activity, demonstrate activity conservation across isolates, and show that mutating predicted motifs in the adenovirus Ψ region improves transgene inducibility in a viral vector.
- **Visible evidence base** Results sections describing MPRA tiling, cell line comparisons, CRE classification, saturation mutagenesis, isolate analyses, and adenoviral vector experiments. Methods sections describing library design, MPRA protocols, and computational analyses. Figure callouts (Figures 1–7, S1–S7) and table callouts (Tables S1–S16) are referenced but not provided.
- **Missing materials affecting confidence** All figures, tables, and supplementary materials. Specific numerical data (activity values, correlation coefficients, p-values, effect sizes) are not available. Details of the Malinois model architecture and training are only partially described. The web resource (vcre-vis.org) was not accessed.

## Reviewer

- **Overall assessment** This manuscript presents a substantial and potentially valuable resource: a systematic functional map of cis-regulatory elements across 27 dsDNA viruses. The experimental approach is appropriate and the scale of the study is impressive. However, the provided text lacks the quantitative detail necessary to fully evaluate the strength of the claims. Several conclusions, particularly regarding CRE classification, regulatory differences across viruses, and the vector engineering application, require the missing figures and tables to be properly assessed. The manuscript is likely to be of interest to virologists, gene regulation researchers, and synthetic biology groups, but the current evidence base is insufficient to fully establish all claims.

- **Who would be interested in the results, and why** Virologists studying viral gene regulation, latency, and reactivation would find the comprehensive CRE map valuable. Researchers in gene therapy and vaccine development would be interested in the demonstration that predicted regulatory motifs can be mutated to improve transgene inducibility. The computational biology community may be interested in the CRE classification approach and the application of interpretability methods to a pre-trained model. The resource itself (vcre-vis.org) could serve as a reference for future studies on viral transcriptional regulation.

- **Major strengths**
  1. The scale of the study is a clear strength: 66,026 tiles across 27 viruses, tested in six cell lines, represents a systematic effort that goes well beyond previous single-gene or single-virus studies.
  2. The combination of MPRA with saturation mutagenesis and machine learning-based motif discovery is methodologically sophisticated and appropriate for the questions asked.
  3. The validation of computational predictions through adenoviral vector engineering provides a functional demonstration of the utility of the resource.
  4. The inclusion of multiple isolates for polyomaviruses and papillomaviruses allows assessment of within-type regulatory variability, which is an important and often overlooked aspect.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "we used massively parallel reporter assays to identify ~2,000 CREs across 27 dsDNA viruses"
- **Evidence pointer** Results section "Identification of CREs from dsDNA viruses"; Figure 1; Table S4
- **Concern** The central claim of identifying ~2,000 CREs cannot be verified from the provided text. The criteria for calling a tile "active" are not described in the main text (thresholds are mentioned as 1% FDR but the specific method for establishing this from control distributions is not detailed). The number of CREs per virus, the distribution of activities, and the reproducibility across replicates are not presented numerically. Without the actual data in Figure 1 and Table S4, the robustness of the CRE calls cannot be assessed.
- **Why it matters** The entire manuscript rests on the reliability of the CRE identification. If the activity thresholds are too permissive or too stringent, all downstream analyses (classification, motif discovery, comparisons) would be affected. The reader needs to see the distribution of activities, the separation between positive and negative controls, and the effect of threshold choice on the number of CREs identified.
- **Resolution test** Provide the activity distributions for positive and negative controls in each cell line, the receiver operating characteristic or precision-recall analysis for threshold selection, and the number of CREs per virus with confidence intervals. Show that the CRE calls are stable across reasonable variations in the threshold.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "Using saturation mutagenesis and machine learning models, we report viral CRE regulators, including SP, ETS, bZIPs, and TFs acting downstream of signal-activated pathways."
- **Evidence pointer** Results section "Multiple TFs contribute to viral CRE activity"; Figure 2F–J; Table S6
- **Concern** The motif discovery pipeline is described only at a high level. The authors state that they used "in silico saturation mutagenesis using Malinois" and "TF-MoDISco-lite" to identify motifs, but the details of how contribution scores were calculated, how motifs were called, and how they were matched to known TF motifs are not provided in the main text. The validation of these predictions (Figure 2G) is mentioned but the concordance metric is not specified. The claim that ETS factors account for 15% of active binding sites is a specific quantitative statement that cannot be checked without the underlying data.
- **Why it matters** The identification of specific TFs regulating viral CREs is a key contribution of the paper. If the motif discovery or matching procedures have biases, the conclusions about which TFs are important could be incorrect. The comparison to literature (Table S1) is mentioned but the overlap statistics are not given.
- **Resolution test** Provide a detailed description of the motif discovery pipeline, including the contribution score calculation, the motif calling threshold, and the matching procedure. Show the concordance between predicted and measured effects of mutations (Figure 2G) with a quantitative metric. Provide the full list of motifs with their significance scores and the overlap with known TF binding sites.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "we describe regulatory differences between viral families, types, and isolates and the drivers of these differences"
- **Evidence pointer** Results sections on polyomavirus, papillomavirus, adenovirus, and herpesvirus CREs; Figures 4–7
- **Concern** The comparisons between viral families, types, and isolates are described qualitatively in the text but the quantitative support is not visible. For example, the statement that "MCPV tiles showed limited activity variability" (Figure 4D) needs the actual distributions to be meaningful. The claim that "CREs in coding regions are generally less active than those in non-coding regions" (Figure 3C) requires the effect size and statistical significance to be reported. The identification of "drivers of these differences" (e.g., specific motifs enriched in one virus vs. another) is a strong claim that needs supporting data.
- **Why it matters** The comparative analyses are a major part of the paper's contribution. Without the actual data, the reader cannot evaluate whether the observed differences are meaningful or within the noise of the assay. The claim about "drivers" implies a causal or at least associative analysis that needs to be documented.
- **Resolution test** Provide the statistical comparisons (with effect sizes and p-values) for all claims of differences between viruses, types, and isolates. Show the data distributions for the key comparisons. For the "drivers" claim, provide the specific analyses that identify which motifs or sequence features explain the observed differences.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "we engineered an adenoviral vector with reduced background activity, increasing transgene inducibility"
- **Evidence pointer** Results section "CRE activity in adenoviral vectors"; Figure 6G–I
- **Concern** The vector engineering experiment is presented as a validation of the approach, but the details are limited. The authors state that they introduced mutations in the Ψ region predicted to abrogate transcriptional activity, but the specific mutations, the number of mutations, and the criteria for selecting them are not described. The results show a 65% reduction in basal GFP and a 2-fold increase in inducibility, but the experimental conditions (MOI, time points, cell lines) and the statistical analysis are not provided.
- **Why it matters** This experiment is important because it demonstrates the practical utility of the resource. If the effect is not robust or is specific to particular conditions, the claim of general applicability would be weakened. The reader needs to understand the design and the reproducibility of the effect.
- **Resolution test** Provide the specific mutations introduced, the rationale for their selection, and the full experimental protocol. Show the dose-response curves for doxycycline induction and the statistical comparison between wild-type and mutant vectors. Include data on viral titer and any potential effects on viral replication or packaging.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** "Viral genomes have a higher CRE density than the human genome"
- **Evidence pointer** Results section "Identification of CREs from dsDNA viruses"; Figure S1F
- **Concern** This comparison is made in the abstract and introduction but the basis for it is not clear. The human genome CRE density is cited from a previous study [14], but the comparison may not be apples-to-apples: the viral CREs are identified by MPRA in a specific set of cell lines, while the human CRE density may come from different assays or cell types. The statement that viral CRE density is "substantially higher" needs a clear definition of the comparison and its limitations.
- **Why it matters** This is a headline claim that may be overinterpreted if the comparison is not properly contextualized. The reader needs to understand what is being compared and whether the difference is meaningful given the different assay conditions.
- **Resolution test** Provide a clear description of how the human CRE density was calculated and the assumptions made in the comparison. Show the sensitivity of the conclusion to the choice of human CRE set and the cell lines used.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract states that "most dsDNA viruses use the host transcriptional machinery to express viral genes for replication and immune evasion." This is a broad generalization that may not apply to all dsDNA viruses, some of which encode their own transcription factors or RNA polymerases.
- **Required correction** Qualify the statement to acknowledge exceptions, e.g., "most dsDNA viruses that infect humans" or "many dsDNA viruses."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, MPRA library design
- **Evidence pointer** Methods section "MPRA viral tiling library sequence design"
- **Issue** The description of tile generation states that tiles are 200 bp with 50 bp offsets, but the handling of the genome ends is not described. It is unclear whether the last tile is always exactly 200 bp or whether some genomes have shorter terminal tiles.
- **Required correction** Clarify the treatment of terminal regions and whether any tiles shorter than 200 bp were included or excluded.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results, cell line comparisons
- **Evidence pointer** Results section "Viral CRE activity is mostly conserved across cell lines"; Figure 1D
- **Issue** The correlation coefficients (0.48–0.83) are reported but the method for calculating them (Pearson vs. Spearman) and the units of comparison (log2 fold change vs. ranks) are not specified. The statement that GM12878 and MRC-5 are "most different" needs a statistical justification.
- **Required correction** Specify the correlation method and the data transformation used. Provide a statistical test for the claim that specific cell line pairs are more different than others.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, CRE classification
- **Evidence pointer** Results section "Classification of viral CREs"; Figure 2D
- **Issue** The statement that "nearly half of active viral tiles matched shuffled CRE classes" is presented as a limitation of the classifier, but it could also indicate that many viral CREs are genuinely different from human CREs. The interpretation of this result needs more nuance.
- **Required correction** Discuss alternative interpretations of the "undetermined" class and consider whether the classifier's training set (human CREs) is appropriate for classifying viral elements.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, herpesvirus analysis
- **Evidence pointer** Results section "Herpesviruses differ in CRE types and genomic distributions"; Figure 7
- **Issue** The text mentions that "promoter regions of genes expressed at different viral replication stages had varying activity levels" but does not describe how the replication stage was determined for each gene. The classification of genes into immediate early, early, late, and latent categories is referenced to Table S14 but the criteria are not described.
- **Required correction** Briefly describe the source and criteria for gene kinetic classifications in the main text.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Web resource
- **Evidence pointer** Discussion, last paragraph
- **Issue** The web resource (vcre-vis.org) is mentioned but its features and how to use it are not described. For a resource paper, this is an important omission.
- **Required correction** Add a brief description of the web resource's functionality and how users can query and download the data.

## Risk / unsupported claims
- The claim of "~2,000 CREs" across 27 viruses cannot be verified without the activity data and threshold criteria.
- The specific list of TFs reported to regulate viral CREs (SP, ETS, bZIPs, etc.) is not supported by the visible data; the motif discovery results are not shown.
- The statement that "viral genomes have a higher CRE density than the human genome" is a comparison that may not be valid given different assay conditions and cell types.
- The claim that "ETS factors account for 15% of active binding sites" is a specific quantitative statement that cannot be checked.
- The vector engineering result (65% reduction in basal expression, 2-fold increase in inducibility) is presented without the experimental details needed to evaluate its robustness.
- The statement that "most viral CREs have promoter-like features and overlap protein-coding sequences" is made but the quantitative support (proportions, comparisons to human CREs) is not visible.
- The identification of "drivers" of regulatory differences between viruses is a strong claim that requires the supporting comparative analyses to be shown.
- The claim that "94% of CREs reported in the literature were recovered" is mentioned but the comparison set and the method for determining overlap are not described.