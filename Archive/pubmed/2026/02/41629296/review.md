## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented; no assessment of editorial fit or publication decision
- **Shared manuscript claim summary** The authors identify PCBP1 as a selective i-motif-binding protein that unfolds specific i-motif structures in a pH- and sequence-dependent manner, requiring coordinated action of its three KH domains, and link this activity to G1/S checkpoint progression and genome stability
- **Visible evidence base** Biochemical binding assays (EMSA, MST, ITC), biophysical spectroscopy (CD, NMR), molecular dynamics simulations, chromatin immunoprecipitation (ChIP) in HeLa cells, cell cycle analysis, and gene expression measurements
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; source data not available; Supplementary Movies 1-4 not accessible; full ChIP-seq analysis details not shown

## Reviewer

- **Overall assessment** This manuscript addresses an important and timely question in the field of non-canonical DNA structure biology: how i-motif structures are recognized and resolved by proteins in a cellular context. The authors present a multi-faceted approach combining in vitro biochemistry, biophysics, computational modeling, and cell-based assays to characterize PCBP1 as a selective i-motif-binding and unfolding protein. The central claim that PCBP1 unfolds specific i-motifs through a coordinated KH1+2 and KH3 mechanism is interesting and potentially significant. However, several technical concerns and gaps in the evidence weaken the current support for the strongest conclusions, particularly regarding the in vivo relevance and the mechanistic model. The manuscript would benefit from additional controls, clearer quantification, and more direct evidence linking the proposed mechanism to the observed cellular phenotypes.

- **Who would be interested in the results, and why** Researchers studying non-canonical DNA structures (i-motifs, G-quadruplexes), DNA replication and repair, cell cycle regulation, and RNA/DNA-binding proteins, particularly those in the hnRNP family. The work also has relevance for understanding genome instability mechanisms in cancer, given the links between i-motif dynamics and oncogene promoters.

- **Major strengths**
  1. The study addresses a significant gap in the field: protein-mediated regulation of i-motif structures, which is under-explored compared to G-quadruplex biology.
  2. The multi-technique approach (EMSA, MST, ITC, CD, NMR, MD simulations, ChIP, cell-based assays) provides a comprehensive view of the PCBP1-i-motif interaction.
  3. The identification of sequence- and structure-specific selectivity for i-motifs over unfolded forms is a valuable contribution.
  4. The hierarchical model of KH1+2 remodeling followed by KH3-driven unfolding is a novel mechanistic proposal.
  5. The cell cycle-dependent regulation of i-motif occupancy at specific loci connects the biochemical findings to a physiological context.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency for in vivo claims
- **Claim pointer** The authors claim that PCBP1 depletion causes G1/S arrest and increased DNA damage, and that this is due to impaired i-motif resolution at specific loci
- **Evidence point** Figure 5A-D; Results section "PCBP1 depletes i-motif formation at specific loci during the cell cycle"
- **Concern** The causal link between PCBP1-mediated i-motif unfolding and G1/S arrest is not directly established. The authors show that PCBP1 knockdown leads to G1/S arrest and elevated γH2AX, and separately that i-motif occupancy increases at cMYC and ILPR loci. However, they do not demonstrate that the increased i-motif formation at these specific loci is the cause of the cell cycle arrest or DNA damage. Alternative explanations, such as PCBP1's known roles in RNA metabolism, mRNA stability, or other DNA repair functions, are not excluded. The manuscript would be substantially strengthened by experiments showing that preventing i-motif formation at these loci (e.g., through mutation of the i-motif-forming sequences) rescues the G1/S arrest phenotype in PCBP1 knockdown cells.
- **Why it matters** The central physiological claim of the paper is that PCBP1's i-motif unfolding activity is essential for proper G1/S transition. Without direct evidence linking the two, the in vivo significance of the biochemical findings remains correlative rather than causal.
- **Resolution test** Provide rescue experiments where i-motif-forming sequences at cMYC and ILPR are mutated to non-i-motif-forming variants in PCBP1 knockdown cells, and assess whether G1/S arrest and γH2AX levels are reduced. Alternatively, complement PCBP1 knockdown with i-motif-unfolding-deficient PCBP1 mutants to show that the unfolding activity specifically is required for cell cycle progression.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic model support
- **Claim pointer** The authors propose a hierarchical mechanism where KH1+2 domains remodel i-motifs, recruiting KH3 to facilitate unfolding
- **Evidence point** Figures 6-7; Results sections "PCBP1 unfolds different i-motifs with varied kinetics" and "Molecular basis of i-motif unfolding by coordination of KH domains"
- **Concern** The evidence for the proposed two-step mechanism is indirect. The ITD experiments show that KH1+2 alone causes delayed unfolding, and the combination of KH1+2 and KH3 restores full activity, but the authors do not directly demonstrate that KH1+2 binding precedes KH3 recruitment or that KH1+2-induced remodeling is a required intermediate. The MD simulations provide a plausible model but are based on a single i-motif sequence (ILPR) with mutations, and the relevance to the other i-motifs studied is unclear. Additionally, the claim that KH3 "cannot bind" i-motifs is based on MST data, but the authors do not show whether KH3 can bind to the KH1+2-remodeled intermediate.
- **Why it matters** The mechanistic model is a key novel contribution of the paper. Without direct evidence for the sequential steps, the model remains speculative and could be explained by alternative mechanisms, such as simultaneous binding of both domains or a simple avidity effect.
- **Resolution test** Perform kinetic experiments with pre-formed KH1+2-i-motif complexes and then add KH3, measuring binding and unfolding in real time. Use FRET or single-molecule approaches to directly visualize the proposed remodeling and recruitment steps. Additionally, test whether KH3 can bind to i-motifs that have been pre-incubated with KH1+2 but not unfolded.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Control adequacy for i-motif specificity
- **Claim pointer** The authors claim that PCBP1 selectively binds i-motifs over their unfolded forms and that this selectivity is structure-specific
- **Evidence point** Figures 2-3; Results section "PCBP1 selectively binds i-motifs over their unfolded forms in vitro"
- **Concern** The comparison between "folded" and "unfolded" states relies heavily on pH differences (6.4 vs 8.0). However, pH changes can affect protein conformation and charge distribution independently of DNA structure. The authors show PCBP1 stability at pH 6.4 and above, but do not directly demonstrate that PCBP1's conformation is identical at pH 6.4 and 8.0. Additionally, the mutC control (a C-rich sequence that does not form i-motifs) is only tested at pH 6.4 and 8.0, but the authors do not show that mutC remains unfolded at pH 6.4 under their exact experimental conditions. The claim of structure-specificity would be strengthened by using a mutant i-motif sequence that cannot form the structure at the same pH, or by using a competitive binding assay with a known i-motif ligand.
- **Why it matters** The selectivity for i-motif structures over unfolded forms is a foundational claim of the paper. If the observed differences are due to pH effects on the protein rather than DNA structure, the interpretation would be fundamentally different.
- **Resolution test** Perform binding assays at a single pH using i-motif-forming sequences and their mutant variants that cannot form i-motifs (e.g., with C-to-T mutations that disrupt C:CH+ pairing). Alternatively, use a pH-jump experiment where the i-motif is pre-formed at low pH and then the pH is raised to 6.4 in the presence of PCBP1, comparing to a sequence that cannot form i-motifs at any pH.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor in binding measurements
- **Claim pointer** The authors report apparent dissociation constants (KD,app) for PCBP1-i-motif interactions ranging between 150-300 nM
- **Evidence point** Figure 2E-F; Results section "PCBP1 selectively binds i-motifs over their unfolded forms in vitro"
- **Concern** The MST experiments are described but the fitting details, error analysis, and the number of independent measurements are not fully reported. The KD,app values are presented as a range, but the statistical comparison between conditions (pH 6.4 vs 7.0 vs 8.0) is not clearly described. Additionally, the MST data in Figure 2E appear to show incomplete binding curves for some conditions, which could affect the reliability of the fitted KD,app values. The authors should provide the full MST data with confidence intervals and clearly state the number of replicates for each condition.
- **Why it matters** The quantitative comparison of binding affinities across different i-motifs and pH conditions is central to the claim of selectivity. Unreliable KD,app values would undermine the quantitative conclusions.
- **Resolution test** Provide complete MST binding curves with error bars for all conditions, report the number of replicates, and include confidence intervals for all fitted KD,app values. If possible, validate the MST results with an orthogonal method such as surface plasmon resonance or fluorescence anisotropy.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of NMR data
- **Claim pointer** The authors interpret NMR spectral changes as evidence of i-motif unfolding upon PCBP1 binding
- **Evidence point** Figure 3A; Results section "PCBP1 unfolds different i-motifs with varied kinetics"
- **Concern** The NMR data show broadening and shifts of imino proton resonances, but the interpretation that this reflects unfolding is not fully justified. Line broadening could also result from intermediate exchange between bound and free states, or from non-specific aggregation. The authors do not provide a quantitative analysis of the NMR data (e.g., peak assignments, integration, or relaxation measurements) to support the unfolding interpretation. Additionally, the NMR experiments appear to be conducted at a single protein:DNA ratio, and no titration series is shown.
- **Why it matters** The NMR data are used to support the claim that PCBP1 directly unfolds i-motifs. If the spectral changes are due to other effects, the unfolding conclusion would be weakened.
- **Resolution test** Perform a full NMR titration series with increasing PCBP1 concentrations, and use 2D NMR methods to assign key imino protons and monitor their disappearance or shift. Consider using selective 1H-15N or 1H-13C experiments to distinguish between unfolding and binding-induced broadening.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure presentation
- **Affected element** Figure 2C-D
- **Evidence point** Figure 2C-D
- **Issue** The EMSA gels are described as showing "complete band-shifts" at lower PCBP1 concentrations at pH 6.4, but the figure resolution appears insufficient to clearly distinguish between different shifted species. The two shifted bands at pH 6.4 are mentioned but not clearly annotated.
- **Required correction** Provide higher-resolution gel images with clear annotations of all shifted species, and include a schematic or labeled markers to indicate the positions of free DNA, bound complexes, and any intermediate species.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figure 5A-B
- **Evidence point** Figure 5A-B
- **Issue** The cell cycle analysis shows representative histograms, but the statistical analysis of the cell cycle distribution across replicates is not clearly described. The bar plots show means and SD, but the number of replicates and the statistical test used are not stated in the figure legend.
- **Required correction** Clearly state the number of biological replicates, the statistical test used, and the p-values for all comparisons in the figure legend or methods section.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** MD simulation methods
- **Evidence point** Methods section "Docking and MD simulations"
- **Issue** The description of the MD simulations lacks important details, including the specific force field parameters for the protonated cytosines, the equilibration protocol, the number of replicas, and the convergence criteria. The choice of the ILPR i-motif structure (PDB 8AYG) and the rationale for the G-to-A mutations are not fully explained.
- **Required correction** Provide a more detailed description of the simulation setup, including the protonation treatment, the equilibration and production protocols, the number of replicas, and the analysis methods. Justify the choice of the ILPR structure and the mutations made.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Control for ChIP experiments
- **Affected element** Figure 5F-G
- **Evidence point** Figure 5F-G
- **Issue** The ChIP experiments use HTR6 as a negative control, but the authors do not show whether PCBP1 knockdown affects the expression or stability of the i-motif-forming genes themselves, which could confound the interpretation of the ChIP results.
- **Required correction** Include mRNA expression levels of cMYC, BCL2, and ILPR in control and PCBP1 knockdown cells to rule out transcriptional feedback effects.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence point** Discussion section
- **Issue** The authors do not discuss the potential limitations of using HeLa cells, which are transformed and have altered cell cycle checkpoints, for studying G1/S transition. They also do not address the possibility that PCBP1's effects on cell cycle could be independent of its i-motif binding activity.
- **Required correction** Add a paragraph discussing the limitations of the study, including the use of a single cell line, the potential for off-target effects of PCBP1 knockdown, and the need for future studies in non-transformed cells or in vivo models.

- **Technical failings that need to be addressed before the case is established**
  1. Lack of direct causal evidence linking i-motif unfolding at specific loci to G1/S arrest (R1-M1)
  2. Insufficient evidence for the sequential KH1+2 to KH3 mechanism (R1-M2)
  3. Inadequate controls for pH-dependent effects on protein conformation in binding assays (R1-M3)
  4. Incomplete reporting of quantitative binding data and statistical analysis (R1-M4)
  5. Over-interpretation of NMR data without quantitative analysis (R1-M5)

- **Assessment against Nature-style criteria**
  - **Originality**: The work is original in its focus on PCBP1 as a selective i-motif unfolding protein with a proposed multi-domain mechanism. While previous studies have identified i-motif binding proteins, the detailed mechanistic dissection of KH domain coordination and the link to cell cycle regulation is novel.
  - **Scientific importance**: The findings have the potential to be important for understanding i-motif biology and its role in genome stability. However, the current evidence does not fully establish the physiological relevance, and the importance would be significantly enhanced by direct causal links between the biochemical activity and cellular phenotypes.
  - **Interdisciplinary readership**: The topic bridges DNA structure biology, protein biochemistry, and cell cycle research, which could attract readers from multiple disciplines. The use of diverse techniques (biochemistry, biophysics, computation, cell biology) broadens the potential audience.
  - **Technical soundness**: The experimental design is generally sound, but several technical concerns need to be addressed, particularly regarding controls for pH effects, quantitative rigor in binding measurements, and the interpretation of NMR data. The MD simulations are a strength but need more detail for reproducibility.
  - **Readability for nonspecialists**: The manuscript is generally well-written and accessible, with clear figures and logical flow. However, some sections (particularly the MD simulation description) may be challenging for non-experts. The abstract effectively summarizes the key findings.

- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses an important question and presents a plausible model, but the current evidence does not fully establish the causal link between PCBP1-mediated i-motif unfolding and G1/S checkpoint regulation. The authors should address the major concerns regarding in vivo causality, mechanistic support, and experimental controls before the case is fully established.

## Risk / unsupported claims
- The claim that PCBP1 knockdown causes G1/S arrest specifically due to impaired i-motif resolution is not directly supported; alternative mechanisms are not excluded
- The proposed hierarchical mechanism of KH1+2 remodeling followed by KH3 recruitment is not directly demonstrated and remains speculative
- The claim of structure-specific binding selectivity is weakened by the lack of controls for pH-dependent protein conformational changes
- The physiological relevance of the in vitro unfolding kinetics to in vivo conditions is not established
- The statement that PCBP1 occupancy "peaks" at G1/S is based on limited time points and would benefit from more detailed temporal analysis
- The interpretation of NMR spectral changes as evidence of unfolding is not quantitatively supported
- The MD simulation results are based on a single i-motif sequence with mutations, and their generalizability to other i-motifs is unclear