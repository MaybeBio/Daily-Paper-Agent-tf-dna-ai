## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) as provided
- **Assessment boundary** Scientific content, methodological soundness, evolutionary and transcriptomic claims, structural biology interpretations, and alignment with Nature-style criteria
- **Shared manuscript claim summary** The authors report that TPST originated in chlorophytes, while sulfated peptide substrates (PSK, PSY, CIF, RGF) emerged later in seed plants; they characterize the TPST-sulfated peptide system in *Liriodendron chinense* via phylogenomics, promoter cis-element analysis, synteny, molecular docking, transcriptomics, and co-expression networks, proposing conserved and lineage-specific regulatory features
- **Visible evidence base** Main text figures referenced (Figures 1–9), supplementary tables and figures referenced (Tables S1–S3, Figures S1–S5), methods descriptions, and transcriptomic dataset identifiers
- **Missing materials affecting confidence** Actual figures and supplementary data not provided; raw RNA-seq processing details incomplete; docking validation metrics absent; statistical details for enrichment and network analyses partially described; genome assembly versions and annotation quality metrics not stated

## Reviewer

- **Overall assessment** This manuscript presents a broad phylogenomic and transcriptomic survey of the TPST-sulfated peptide system, with a useful focus on the magnoliid *Liriodendron chinense*. The evolutionary timeline proposed (TPST in chlorophytes, substrates in seed plants) is plausible and of interest, but the evidence base is uneven. The docking analysis is presented with insufficient rigor, the transcriptomic integration lacks key methodological detail, and several claims about functional specialization extend beyond what the data can support. The work is descriptive and hypothesis-generating rather than mechanistically definitive. With substantial revision, particularly around structural validation and expression analysis transparency, the manuscript could be suitable for a specialized plant science journal, though its current form does not meet the bar for a high-impact general journal.

- **Who would be interested in the results, and why** Plant evolutionary biologists studying peptide hormone signaling, researchers working on sulfated peptide function in development and stress, and the *Liriodendron* genomics community. The phylogenetic framework for TPST and its substrates, and the expression data from a woody magnoliid, will be of value to those interested in the origin and diversification of peptide signaling in plants.

- **Major strengths**
  1. Broad taxonomic sampling (126 species across green plants) for gene family identification, providing a solid evolutionary framework.
  2. The observation that TPST predates its canonical peptide substrates is an interesting and potentially significant evolutionary insight.
  3. The use of *L. chinense* as a phylogenetically informative magnoliid is well justified and adds value beyond typical eudicot or monocot studies.
  4. Integration of multiple data types (phylogeny, synteny, expression, co-expression, docking) is ambitious and provides a multi-layered view.
  5. The authors acknowledge limitations of cis-element analysis and bulk transcriptomics, showing appropriate caution in some interpretations.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that molecular docking identified key TPST-PSK interaction sites and that PSY and CIF share a similar "sandwich-like" binding mode with TPST.
- **Evidence pointer** Section 2.6, Figure 6, Section 4.4
- **Concern** The docking analysis is described only as "AlphaFold-based structural predictions and PyMOL-assisted docking" with no docking software, scoring function, or validation metrics reported. No RMSD, binding energy, or comparison with known experimental structures is provided. The claim of a "sandwich-like" topology is qualitative and not supported by quantitative data. The methods section does not describe how the docking was performed, what constraints were applied, or how the complexes were scored and ranked.
- **Why it matters** Structural claims about interaction interfaces and conserved recognition modes require rigorous computational validation. Without docking parameters, scoring, and reproducibility details, the interaction models are not verifiable and the conclusions drawn from them are not reliable.
- **Resolution test** Provide a detailed docking protocol (software, version, search parameters, scoring function), report docking scores for all complexes, include validation against known experimental structures (e.g., AtPSKR1-PSK, PDB 4Z63), and show statistical comparison of docked poses. If docking was not performed with a recognized docking tool, the claims should be reframed as speculative modeling.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that transcriptomic and co-expression network analyses revealed expression patterns and stress-responsive coordination of TPST and peptide genes in *L. chinense*.
- **Evidence pointer** Section 2.7, Section 2.8, Section 4.5, Section 4.6
- **Concern** The RNA-seq analysis is described at a high level but lacks critical details: read trimming and alignment tools, reference genome version, quantification method, normalization approach, and differential expression criteria are not stated. The co-expression network construction uses a Pearson correlation threshold of |PCC| ≥ 0.60 and adjusted p < 0.05, but the number of genes tested, multiple testing correction method, and network topology statistics are not reported. The integration of multiple datasets (different organs, stress, embryogenesis) is not described in terms of batch effects or cross-dataset comparability.
- **Why it matters** Transcriptomic claims are central to the paper's functional interpretations. Without transparent bioinformatics parameters and quality metrics, the expression patterns and network structures cannot be evaluated or reproduced, undermining the validity of the functional conclusions.
- **Resolution test** Provide a complete bioinformatics pipeline (tools, versions, parameters), report quality control metrics, describe normalization and statistical testing, state the number of genes in each network, and provide network statistics (node counts, edge counts, clustering coefficients). If datasets were combined, describe batch correction or justify the comparability.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that the temporal gap between TPST origin (chlorophytes) and substrate emergence (seed plants) suggests TPST may have processed other substrates before the evolution of canonical peptide families.
- **Evidence pointer** Section 2.1, Section 3
- **Concern** This is an interesting hypothesis, but the evidence is entirely negative (absence of detection). The authors acknowledge methodological limitations, but the discussion does not adequately explore alternative explanations, such as the possibility that peptide substrates exist in earlier lineages but are too divergent to detect with current homology-based methods, or that non-canonical sulfated substrates are involved. The claim that TPST "may have processed other sulfated substrates" is speculative and not tested.
- **Why it matters** The evolutionary narrative is a key contribution of the paper. If the central hypothesis is not rigorously distinguished from detection artifacts, the significance of the finding is weakened.
- **Resolution test** Strengthen the discussion by testing alternative hypotheses where possible (e.g., using synteny or microsynteny to assess whether substrate loci are conserved but unrecognized), or explicitly frame the hypothesis as provisional and outline specific tests (e.g., biochemical assays of chlorophyte TPST activity on candidate substrates).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that cis-element analysis revealed enrichment of ABA, gibberellin, and anaerobic induction-related elements in TPST and peptide gene promoters.
- **Evidence pointer** Section 2.4, Figure 4, Section 4.3
- **Concern** The cis-element analysis uses PlantCARE, which is known to produce high false-positive rates. The statistical significance of "enrichment" is not reported; the authors do not state whether enrichment was tested against a background model or random expectation. The functional interpretation of cis-element presence as indicative of regulation is not supported by experimental validation.
- **Why it matters** Cis-element predictions are frequently unreliable, and claims of regulatory potential based solely on promoter motif presence are weak. Without statistical testing or experimental support, these claims do not substantively advance the functional understanding.
- **Resolution test** Report whether enrichment was statistically tested (e.g., against genome-wide promoter background), or reframe the cis-element analysis as descriptive. If possible, validate a subset of predicted regulatory interactions (e.g., via qPCR or reporter assays) or cite existing experimental evidence for the relevant genes.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Section 1
- **Issue** The abstract and introduction assume familiarity with peptide signaling terminology (e.g., PSK, PSY, CIF, RGF, TPST) without a brief explanatory context for the general reader. The significance of the magnoliid position is stated but not explained in terms accessible to a broad audience.
- **Required correction** Add one or two sentences in the introduction explaining what sulfated peptides are and why their evolutionary origin matters. Briefly define the acronyms at first use in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.1, Figure 1
- **Evidence pointer** Section 2.1
- **Issue** The statement that TPST copy number exceeds five in only a few taxa is presented without specifying which taxa or the functional significance. The reader cannot assess whether these expansions are biologically meaningful or annotation artifacts.
- **Required correction** List the taxa with high copy numbers and briefly discuss whether these are likely real expansions or potential assembly/annotation issues.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.5, Figure 5
- **Evidence pointer** Section 2.5
- **Issue** The synteny analysis reports absence of synteny with rice, but the significance of this negative result is not discussed. The choice of species for comparison (O. sativa, M. biondii, A. thaliana, P. trichocarpa) is not justified.
- **Required correction** Briefly explain the rationale for species selection and discuss whether the lack of rice synteny reflects genuine divergence or limitations of the comparison.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Section 2.8, Figure 8
- **Evidence pointer** Section 2.8
- **Issue** The co-expression network figures are described in text but the specific transcription factor families and their positions in the network are not clearly linked to the biological interpretation. The reader cannot assess the significance of the TF enrichment without more detail.
- **Required correction** Provide a table listing the enriched TF families per network and their associated biological processes, or describe the network modules more explicitly in the text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 4.1
- **Evidence pointer** Section 4.1
- **Issue** The methods state that sequences longer than 200 amino acids were excluded for peptide precursors, but the rationale for this cutoff is not given, and the threshold may exclude legitimate longer precursors in some lineages.
- **Required correction** Justify the length cutoff or cite precedent for this threshold in plant peptide precursor identification.

- **Technical failings that need to be addressed before the case is established**
  R1-M1 (docking validation), R1-M2 (transcriptomic pipeline transparency), R1-M4 (cis-element statistical testing)

- **Assessment against Nature-style criteria**
  - **Originality**: Moderate. The evolutionary timeline for TPST and its substrates is a useful synthesis, but the individual components (phylogenomics, cis-element analysis, expression profiling) are standard approaches. The magnoliid focus adds a novel angle.
  - **Scientific importance**: Moderate. The findings are of interest to plant peptide signaling researchers but do not fundamentally alter current understanding. The evolutionary hypothesis is plausible but not definitively established.
  - **Interdisciplinary readership**: Limited. The manuscript is primarily of interest to plant molecular biologists and evolutionary biologists. The structural and transcriptomic components do not broaden the appeal significantly.
  - **Technical soundness**: Currently insufficient. The docking analysis lacks rigor, the transcriptomic methods are underreported, and the cis-element enrichment is not statistically validated. These issues must be resolved before the conclusions can be accepted.
  - **Readability for nonspecialists**: Acceptable but improvable. The writing is generally clear, but the introduction and abstract could better contextualize the significance for a broader audience.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript has merit as a descriptive evolutionary and transcriptomic survey, but the technical issues in structural modeling, transcriptomic analysis, and cis-element interpretation must be resolved. I would be supportive if the authors provide rigorous validation of the docking results, complete bioinformatics details, and statistically grounded cis-element analysis. The evolutionary hypothesis, while interesting, needs to be more carefully distinguished from detection artifacts.

## Risk / unsupported claims
- The claim that PSY and CIF share a similar "sandwich-like" binding mode with TPST is unsupported without quantitative docking data and validation.
- The claim that TPST may have processed other substrates before the evolution of canonical peptide families is speculative and not tested.
- The claim that cis-element enrichment indicates regulatory potential is not statistically supported.
- The claim that LcPSK2 plays a specialized role in seed development and leaf differentiation based on cis-element presence is not experimentally validated.
- The absence of RGF in *L. chinense* is reported but not discussed in terms of whether this reflects true absence or detection limitations.
- The evolutionary timeline (TPST in chlorophytes, substrates in seed plants) is based on negative evidence and should be treated as provisional.