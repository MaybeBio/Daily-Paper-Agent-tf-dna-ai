## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) from bioRxiv preprint
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text; no supplementary figures or tables were available for direct inspection
- **Shared manuscript claim summary** The authors map genomic binding of 38 designed ORC mutants using ChEC-seq to define ORC elements required for in-vivo DNA binding. They identify three classes of binding sites: silencing-associated sites requiring the BAH domain, asymmetric motif replication origins requiring both Orc1-BP4 and Orc4-IH, and symmetric motif origins where Orc1-BP3 can substitute for Orc4-IH. They propose a model where disordered basic patches in the Orc1 N-terminus facilitate sliding along minor grooves of T-stretches.
- **Visible evidence base** Abstract, introduction, results narrative, discussion, methods, and figure legends referenced in text (Figures 1-6, S1-S4); no raw data, supplementary tables, or full figure panels were available
- **Missing materials affecting confidence** Supplementary figures (S1-S4), Table S1 (strain genotypes), Document S1 (synthetic ORC1 sequence), raw ChEC-seq data, full figure panels, and statistical details for all comparisons

## Reviewer
- **Overall assessment** This manuscript addresses a significant question in DNA replication initiation: how ORC achieves specific DNA binding in vivo despite limited base contacts in the cryo-EM structure. The systematic mutagenesis approach combined with high-resolution ChEC-seq mapping is commendable and provides novel insights into the differential requirements for ORC elements at distinct classes of binding sites. The identification of symmetric versus asymmetric motif classes and the compensatory role of Orc1-BP3 at symmetric motifs is a valuable contribution. However, several technical concerns regarding data presentation, statistical rigor, and the interpretation of molecular dynamics simulations need to be addressed before the conclusions are fully established.
- **Who would be interested in the results, and why** Researchers studying DNA replication initiation, ORC function, protein-DNA recognition mechanisms, and the role of intrinsically disordered regions in DNA binding. The findings on how disordered basic patches contribute to sequence-specific binding have broader implications for understanding how proteins achieve specificity without rigid structural determinants.
- **Major strengths** 1) Systematic mutagenesis of 38 ORC mutants provides comprehensive coverage of functional elements. 2) High-resolution ChEC-seq method captures ORC footprints at nucleotide resolution. 3) Identification of two dominant motif classes with distinct binding requirements is a novel finding. 4) Combination of in-vivo binding data with structural analysis and MD simulations provides multiple lines of evidence. 5) The proposed model for BP-mediated sliding along minor grooves is mechanistically plausible and testable.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical validation of motif classification), R1-M2 (MD simulation methodology and interpretation), R1-M3 (quantitative comparison of binding across mutants)
- **Assessment against Nature-style criteria** Originality: High. The study provides a new framework for understanding ORC-DNA recognition by revealing differential element requirements at distinct motif classes. Scientific importance: High. Understanding how ORC achieves specificity is fundamental to DNA replication initiation and has implications for genome stability. Interdisciplinary readership: Moderate. The work will primarily interest replication and chromatin biologists, though the disordered region binding mechanism may attract a broader protein-nucleic acid interaction audience. Technical soundness: Moderate. The ChEC-seq approach is well-established, but the MD simulation methodology and statistical analyses require clarification and strengthening. Readability for nonspecialists: Good. The manuscript is clearly written with logical progression, though some figure descriptions assume familiarity with genomics methods.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding statistical validation of motif classification, MD simulation methodology, and quantitative binding comparisons.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims that replication origins contain two dominating ORC-bound motif sequences that differ in symmetry, and that these classes show differential binding requirements.
- **Evidence pointer** Results section "Replication origins contain two dominating ORC-bound motif sequences that differ in symmetry"; Figure 1D
- **Concern** The classification of motifs into symmetric and asymmetric classes appears to be based on sequence inspection rather than a formal statistical or computational approach. The authors state that "two variants dominate strongly bound origins" but do not provide quantitative criteria for this classification, such as motif frequency distributions, enrichment scores, or statistical tests comparing the two classes. Additionally, the relationship between motif class and binding strength is described qualitatively without reporting effect sizes or confidence intervals.
- **Why it matters** The central claim of the paper, that different ORC elements are required at different motif classes, depends entirely on the validity of this classification. If the classification is not robust or if the two classes are not statistically distinguishable, the subsequent differential requirement claims lose their foundation.
- **Resolution test** Provide a formal motif discovery and classification analysis with statistical support, including position weight matrices, enrichment scores relative to genomic background, and statistical comparison of binding intensities between the two motif classes. Report the number of origins in each class and the distribution of motif scores.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology
- **Claim pointer** The manuscript claims that MD simulations show that intact BP4 maintains DNA confinement while mutations at base-contacting residues lose this confinement, and that additional BP4 mutations retain confinement despite experimental evidence of reduced binding.
- **Evidence pointer** Results section "Orc1-BP4 is required for binding at replication origins, but is dispensable at silenced loci"; Figure 4E-I
- **Concern** The MD simulation methodology is described with insufficient detail to assess its validity. The simulations are stated to be 500 steps in length, which is extremely short for assessing conformational stability or binding affinity. The measure of "confinement" (standard deviation of RMSD) is not a standard metric for binding stability, and no comparison to experimental binding affinities or free energy calculations is provided. The discrepancy between MD predictions (all non-core mutants retain confinement) and experimental results (17 of 23 mutations reduce binding) is acknowledged but not resolved mechanistically.
- **Why it matters** The MD simulations are used to support the claim that local BP4-base interactions are sufficient for DNA binding, but the methodology as described cannot adequately test this claim. The short simulation time and non-standard analysis metrics undermine confidence in the conclusions drawn from these simulations.
- **Resolution test** Provide detailed MD simulation parameters, including force field, water model, equilibration protocol, and production run length. Use established metrics for binding stability such as contact persistence, hydrogen bond occupancy, or potential of mean force calculations. Compare simulation results with experimental binding data quantitatively, and address the discrepancy between predicted and observed effects of non-core mutations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative analysis
- **Claim pointer** The manuscript claims that Orc1-BP4 is required for binding at most replication origins, that Orc4-IH is required for asymmetric but not symmetric motifs, and that Orc1-BP3 can compensate for Orc4-IH at symmetric motifs.
- **Evidence pointer** Results sections "The Orc4 insertion helix is required for binding at asymmetric, but not symmetric motif sequence" and "BP3 is essential for ORC binding in the absence of Orc4-IH interacting residues"; Figures 3, 5, 6
- **Concern** The quantitative assessment of binding changes across the 38 mutants is not described with sufficient rigor. The manuscript reports "reduced binding," "high loss of binding," and "retained strong binding" without providing quantitative thresholds, statistical tests, or effect sizes. The correlation analysis between binding loss and growth phenotypes is mentioned but the methods for this analysis are not described. The PCA analysis attributing 88% of variation to a single component is mentioned but the interpretation and significance of this finding are not discussed.
- **Why it matters** The conclusions about differential element requirements depend on reliable quantification of binding changes across mutants. Without clear statistical criteria for what constitutes "reduced" versus "retained" binding, the classification of motif-specific requirements cannot be independently evaluated.
- **Resolution test** Provide a clear statistical framework for classifying binding changes, including thresholds for significance, effect sizes with confidence intervals, and appropriate multiple testing corrections. Describe the correlation and PCA analyses in sufficient detail to be reproducible, and discuss the biological interpretation of the PCA results.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1
- **Evidence pointer** Results section "Replication origins contain two dominating ORC-bound motif sequences that differ in symmetry"; Figure 1B-F
- **Issue** The manuscript describes high-resolution ChEC-seq data capturing ORC footprints of 45-50 bp, but the figure panels showing these footprints are not described in sufficient detail. The distinction between "strongly bound" and "weakly bound" origins is not visually quantified.
- **Required correction** Add scale bars and quantitative signal tracks to figure panels, and provide a clear visual representation of binding strength differences between motif classes.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodology
- **Affected element** ChEC-seq analysis
- **Evidence pointer** Methods section "Process and analysis of ChEC-seq data"
- **Issue** The normalization approach for ChEC-seq data is described as "normalized to one million reads," but the rationale for this normalization and its adequacy for comparing across mutants with potentially different overall binding levels is not discussed.
- **Required correction** Justify the normalization strategy and discuss potential biases when comparing mutants with globally reduced binding.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion section
- **Evidence pointer** Discussion, final paragraph
- **Issue** The claim that basic patches are conserved across eukaryotes and that the proposed mechanism may be general is speculative and not directly supported by the data presented, which focuses on S. cerevisiae.
- **Required correction** Clearly distinguish between conclusions supported by the current data and hypotheses that require future testing in other organisms.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 6E model
- **Evidence pointer** Results section "BP3 is essential for ORC binding in the absence of Orc4-IH interacting residues"; Figure 6E
- **Issue** The proposed model in Figure 6E is described in the text but the figure itself is not available for inspection. The model's key features and predictions should be clearly articulated in the text.
- **Required correction** Provide a detailed textual description of the model, including the proposed roles of each basic patch and how they interact with the symmetric and asymmetric motifs.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Growth phenotype correlation
- **Evidence pointer** Results section "Orc1-BP4 is required for binding at replication origins, but is dispensable at silenced loci"; Figure 4H
- **Issue** The correlation between binding loss and growth phenotypes is reported with R2=0.90 and p=7.5*10-9, but the number of data points and the nature of the correlation (linear, rank-based) are not specified.
- **Required correction** Report the number of mutants included in the correlation analysis and the type of correlation test used.

## Risk / unsupported claims
- The claim that "disordered basic patches are key for ORC-motif binding in-vivo" is supported by the mutagenesis data but the mechanistic interpretation involving transient interactions and sliding is speculative and not directly tested.
- The claim that "Orc1-BP3 and Orc4-IH can both complement Orc1-BP4 in stabilizing ORC binding" is based on genetic interaction data but the molecular mechanism of this complementation is not characterized.
- The generalization of the proposed mechanism to other eukaryotes based on conservation of basic patches is not supported by direct experimental evidence in this manuscript.
- The statement that "transient BP4 interactions with semi-specific DNA sites guide ORC to its high-affinity binding" is presented as a conclusion but is framed as a hypothesis in the discussion; this distinction should be made clearer.
- The claim that the BAH domain "fully explains" ORC binding at silencing-associated sites is strong given that only deletion and overexpression experiments are presented, without testing other potential contributing factors.