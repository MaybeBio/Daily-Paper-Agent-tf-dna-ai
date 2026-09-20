## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and conclusions
- **Assessment boundary** Scientific content, methodological rigor, validity of claims, and adherence to Nature-style criteria
- **Shared manuscript claim summary** The authors report the first genome-wide identification of 15 RGF genes in hexaploid wheat, classify them into five homeologous groups on chromosomes 2 and 6, show root-enriched expression of TaRGF5 with drought-induced repression, predict a unique BES1 cis-element in TaRGF5B, and use docking and molecular dynamics to propose a TaRGF5–TaRGI3 interaction
- **Visible evidence base** Results sections 2.1 through 2.10, including figures referenced as Figures 1–11, Tables S1–S5, and Video S1; materials and methods sections 4.1 through 4.8
- **Missing materials affecting confidence** Figures, tables, and supplementary data files (S1–S4) are referenced but not provided; raw RNA-seq data processing details are incomplete; statistical analysis details for qRT-PCR are not fully described; molecular dynamics simulation parameters are partially described

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive bioinformatics analysis of the RGF gene family in wheat, with a focus on TaRGF5 as a candidate root-associated signaling component. The work is systematic and addresses a genuine gap in wheat genomics. However, the study is predominantly computational and descriptive, with limited experimental validation. The central claims regarding TaRGF5 function and the TaRGF5–TaRGI3 interaction rest on predictive modeling rather than direct biological evidence. The manuscript would benefit from experimental validation of the predicted interactions and functional assays to support the proposed roles.
- **Who would be interested in the results, and why** Researchers in plant peptide signaling, root development, wheat genomics, and drought stress biology would find this work relevant. The identification of the TaRGF family provides a foundation for functional studies in wheat, and the proposed TaRGF5–TaRGI3 module offers a candidate target for breeding programs aimed at improving root architecture under water-limited conditions.
- **Major strengths** The study fills a clear gap in wheat genomics by systematically identifying and characterizing the RGF family. The use of multiple bioinformatics tools for sequence analysis, phylogenetic reconstruction, and structural prediction is thorough. The integration of expression data from public RNA-seq datasets with qRT-PCR validation strengthens the expression claims. The computational prediction of the TaRGF5–TaRGI3 interaction, including molecular dynamics simulations, provides a testable hypothesis for future experimental work.
- **Major Concerns** The manuscript relies heavily on computational predictions without experimental validation of the key functional claims. The RNA-seq analysis methodology is not fully described, and the qRT-PCR validation lacks statistical detail. The molecular docking and dynamics results are presented as evidence for a biological interaction, but these are predictive and require experimental confirmation. The claim of a unique BES1 element in TaRGF5B is based on promoter prediction tools with no functional validation.
- **Minor Comments** Several typographical errors and inconsistencies in terminology are present. The discussion of drought-induced root growth inhibition as an adaptive strategy is speculative and could be better supported. The conclusion section overstates the implications of the computational findings.
- **Technical failings that need to be addressed before the case is established** The RNA-seq analysis pipeline is not described in sufficient detail to assess reproducibility. The qRT-PCR data lack error bars and statistical tests. The molecular dynamics simulation is based on a single trajectory, which limits confidence in the results. The docking analysis uses predicted structures without experimental validation of the binding mode.
- **Assessment against Nature-style criteria** Originality: The work is original in its focus on wheat RGF genes, which have not been previously characterized. Scientific importance: The findings are of moderate importance, providing a genomic resource and a testable hypothesis, but the lack of functional validation limits the immediate impact. Interdisciplinary readership: The work is primarily of interest to plant molecular biologists and wheat geneticists, with limited broader appeal. Technical soundness: The bioinformatics approaches are generally sound, but the lack of experimental validation and incomplete methodological details reduce confidence. Readability for nonspecialists: The manuscript is written in a clear style, but the heavy reliance on computational methods may limit accessibility for readers without bioinformatics expertise.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that TaRGF5 homeologs are negatively regulated by drought stress based on RNA-seq and qRT-PCR data.
- **Evidence pointer** Section 2.5, Figure 6, Figure 7
- **Concern** The RNA-seq analysis methodology is not described in sufficient detail. The authors state that three BioProjects were selected, but the specific sample numbers, biological replicates, and processing steps are not fully detailed. The qRT-PCR validation lacks information on the number of biological replicates, statistical analysis, and error representation. The claim of drought-induced repression is based on a single cultivar (Sids-13) without comparison to other genotypes.
- **Why it matters** The central claim of drought-responsive regulation of TaRGF5 requires robust experimental evidence. Without clear methodological details and statistical support, the reliability of the expression data cannot be assessed, and the conclusion that TaRGF5 is drought-repressed is not firmly established.
- **Resolution test** Provide a complete description of the RNA-seq processing pipeline, including quality control metrics, alignment parameters, and quantification methods. Include details on the number of biological replicates for both RNA-seq and qRT-PCR experiments. Present qRT-PCR data with error bars and appropriate statistical tests (e.g., t-test or ANOVA). Ideally, validate the drought response in additional wheat cultivars or under controlled growth conditions.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors propose that TaRGF5 interacts with TaRGI3 based on molecular docking and molecular dynamics simulations.
- **Evidence pointer** Section 2.9, Section 2.10, Table 1, Figure 10, Figure 11
- **Concern** The docking and molecular dynamics results are presented as evidence for a biological interaction, but these are purely computational predictions. The HADDOCK score for the wheat complex is substantially less favorable than the Arabidopsis reference, and the authors do not provide experimental validation such as co-immunoprecipitation, yeast two-hybrid, or surface plasmon resonance. The molecular dynamics simulation is based on a single 100 ns trajectory, which may not be sufficient to establish stable binding.
- **Why it matters** The proposed TaRGF5–TaRGI3 interaction is a key claim of the manuscript. Without experimental validation, the interaction remains speculative, and the functional significance of this module in root development and drought response is not established.
- **Resolution test** Provide experimental evidence for the TaRGF5–TaRGI3 interaction using biochemical or cellular assays. If experimental validation is not feasible, clearly frame the interaction as a computational prediction and temper the conclusions accordingly. Consider running multiple independent molecular dynamics simulations to assess the robustness of the binding mode.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation
- **Claim pointer** The authors state that the unique BES1 cis-element in TaRGF5B links brassinosteroid signaling to peptide-mediated root regulation.
- **Evidence pointer** Section 2.7, Figure 8
- **Concern** The identification of a BES1 binding site is based solely on promoter prediction tools. The authors do not provide experimental evidence that BES1 actually binds to this element or that brassinosteroid signaling regulates TaRGF5B expression. The functional significance of this predicted element is therefore speculative.
- **Why it matters** The proposed link between brassinosteroid signaling and TaRGF5B regulation is an interesting hypothesis, but without experimental support, it remains unsubstantiated. Overinterpreting predicted cis-elements can lead to misleading conclusions about gene regulation.
- **Resolution test** Perform experimental validation such as electrophoretic mobility shift assays, chromatin immunoprecipitation, or reporter gene assays to confirm BES1 binding and functional relevance. Alternatively, treat plants with brassinosteroid agonists or antagonists and measure TaRGF5B expression to test the regulatory link.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Completeness
- **Claim pointer** The authors claim that the TaRGF gene family is restricted to chromosomes 2 and 6, with no additional members elsewhere.
- **Evidence pointer** Section 2.1, Figure 1
- **Concern** The identification of 15 TaRGF genes relies on homology-based screening with Arabidopsis sequences. The authors do not describe the search parameters, inclusion criteria, or how they ensured completeness of the family. It is possible that divergent members were missed, particularly if they lack conserved motifs.
- **Why it matters** A complete gene family inventory is essential for the validity of the phylogenetic and functional analyses. Incomplete identification could lead to incorrect conclusions about gene family evolution and functional redundancy.
- **Resolution test** Provide a detailed description of the search strategy, including BLAST parameters, domain validation, and manual curation steps. Consider using additional search tools such as HMMER with hidden Markov models to ensure comprehensive identification.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, Figure 4
- **Evidence pointer** Section 2.2, Figure 4
- **Issue** The phylogenetic tree is described as having two major clades, but the figure is not provided for review. The description of clade composition is somewhat confusing, particularly regarding the placement of TaRGF4 isoforms across clades C1 and C1.2.
- **Required correction** Clarify the clade assignments and ensure the figure legend clearly indicates the bootstrap support values and the sequences used for tree construction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Accuracy
- **Affected element** Section 2.3, Figure 5
- **Evidence pointer** Section 2.3, Figure 5
- **Issue** The text mentions expression values of −49.8 as a threshold for non-detection, but this value is unusual and may reflect a specific transformation. The authors should clarify the units and transformation used.
- **Required correction** Explain the transformation applied to expression values and justify the threshold for non-detection.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Section 2.5, Figure 6
- **Evidence pointer** Section 2.5, Figure 6
- **Issue** The text states that "the overall pattern clearly indicates a decline in average TaRGF expression under drought," but the error bars are described as showing variability. The statistical significance of this decline is not reported.
- **Required correction** Provide statistical analysis to support the claim of drought-induced decline, and report p-values or confidence intervals.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.3.1, Table S3
- **Evidence pointer** Section 4.3.1, Table S3
- **Issue** The RNA-seq datasets are described as coming from three BioProjects, but the specific accessions and sample details are only in the supplementary table, which is not provided.
- **Required correction** Include the BioProject accessions in the main text and ensure the supplementary table lists all sample accessions, conditions, and replicate numbers.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 4.7.3, Table S5
- **Evidence pointer** Section 4.7.3, Table S5
- **Issue** The active residues for TaRGI3 are listed as 205, 207, 208, 228, 230, 232, 254, and 256, but the rationale for selecting these specific residues is not explained.
- **Required correction** Justify the selection of active residues based on structural or sequence conservation data.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language
- **Affected element** Section 2.3, Figure 5C
- **Evidence pointer** Section 2.3, Figure 5C
- **Issue** The text contains a typographical error: "members osf TaRGF1" should be "members of TaRGF1."
- **Required correction** Correct the typographical error.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.8.2
- **Evidence pointer** Section 4.8.2
- **Issue** The molecular dynamics simulation protocol states a non-bonded cutoff of 1.0–1.2 nm, which is a range rather than a specific value. This is unusual and should be clarified.
- **Required correction** Specify the exact cutoff value used in the simulations.

## Risk / unsupported claims
- The claim that TaRGF5 homeologs are negatively regulated by drought stress is supported by RNA-seq and qRT-PCR data, but the lack of statistical details and limited cultivar testing reduces confidence.
- The proposed TaRGF5–TaRGI3 interaction is based solely on computational predictions and is not experimentally validated.
- The unique BES1 cis-element in TaRGF5B is predicted but not functionally confirmed.
- The completeness of the TaRGF gene family identification cannot be fully assessed without detailed search parameters.
- The claim that TaRGF5 may play a role in root-associated signaling similar to AtRGF5 is speculative and requires functional evidence.
- The molecular dynamics simulation results are based on a single trajectory and should be interpreted with caution.