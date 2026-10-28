## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, conclusions) as provided by the user. No supplementary files, figures, or tables were available for inspection beyond in-text references.
- **Assessment boundary** The review assesses the scientific claims, methodological soundness, and presentation quality of the manuscript as submitted. It does not evaluate code functionality directly, as the software repository was not accessed.
- **Shared manuscript claim summary** The authors present ARIP, a Python-based tool for calculating interatomic contact areas and volumes in proteins, using a modified dr_sasa algorithm and a novel atomic overlap weighted algorithm. They claim improved precision through solvent-radius customization, applicability to multi-model PDB files (e.g., NMR, MD), and utility in four biological contexts: NMR ensemble analysis (P4HB/PDI), protein–drug binding (CYP17A1), protein–DNA binding (SPI1), and MD trajectory analysis (BRD4). They also propose contact volume as a more informative metric than contact area for interaction analysis and scoring function development.
- **Visible evidence base** The manuscript text includes descriptions of datasets (approximately 5000 X-ray structures, 1151 NMR structures, 100 X-ray and 50 NMR structures for benchmarking), four application cases, and equations for volume and area calculations. Figures and tables are referenced but not provided in the submitted material.
- **Missing materials affecting confidence** Figures 1–6, Figures S1–S14, Tables 1, 2, S1, S2, and the software repository (GitHub) were not provided. This limits verification of algorithmic details, benchmark results, and application outcomes. No quantitative performance metrics (e.g., accuracy vs. experimental data, comparison with dr_sasa outputs) are presented in the text.

## Reviewer
- **Overall assessment** The manuscript describes a potentially useful software tool for structural biology, with a reasonable conceptual basis and a broad set of application examples. However, the current text lacks quantitative validation, detailed algorithmic descriptions, and clear comparisons with existing tools. The claims regarding the superiority of contact volume over contact area and the biological insights derived from the four cases are not substantiated with data in the provided material. The manuscript is more descriptive than analytical, and the scientific case is not yet established.
- **Who would be interested in the results, and why** Computational structural biologists, protein engineers, and researchers studying protein–protein, protein–ligand, or protein–DNA interactions may find ARIP useful for identifying contact residues and quantifying interaction interfaces. Those developing scoring functions or analyzing MD trajectories could also benefit from the volume-based metrics. The tool's open-source nature and multi-model support may appeal to a niche but active community.
- **Major strengths** 
  1. The concept of calculating contact volume in addition to contact area is physically meaningful and could offer complementary insights into interaction strength and electron delocalization.
  2. The tool supports multi-model PDB files and batch processing, which is practical for NMR ensembles and MD simulations.
  3. The authors address a real limitation in existing tools by allowing solvent-radius customization based on empirical water distribution data.
  4. The application to four distinct biological systems demonstrates versatility, though the depth of analysis is currently limited.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The manuscript claims that ARIP provides "precise" contact area and volume calculations, and that the modified dr_sasa algorithm and atomic overlap weighted algorithm are improvements over existing methods.
  - **Evidence pointer** Section 2.2 (Performance), Section 4.3 (Function and Principle), location not provided for algorithmic details.
  - **Concern** The manuscript does not provide a detailed description of the modified dr_sasa algorithm, the grid resolution parameters, or the atomic overlap weighted method's mathematical formulation beyond Equation (2). No validation against experimental data (e.g., mutagenesis, binding affinities) or comparison with dr_sasa or other tools (e.g., CSU&LPC) is presented. The performance benchmark (Table 2) is referenced but not shown, and the claim of "precision" is unsupported.
  - **Why it matters** Without quantitative validation and algorithmic transparency, readers cannot assess whether ARIP's outputs are reliable or superior to existing tools. The core scientific contribution hinges on the accuracy and utility of the calculations.
  - **Resolution test** Provide a detailed algorithmic description, including grid parameters and convergence tests. Compare ARIP's contact areas and volumes with those from dr_sasa and experimental data (e.g., known binding interfaces, mutational effects) for a benchmark set. Report correlation coefficients, error metrics, and runtime comparisons.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Scientific importance
  - **Claim pointer** The authors claim that contact volume is "more informative" than contact area for analyzing interactions and developing scoring functions, and that ARIP's application to four cases provides novel biological insights.
  - **Evidence pointer** Section 2.3–2.6 (Application cases), Section 3 (Discussion), location not provided for specific results.
  - **Concern** The four application cases are described qualitatively without presenting quantitative results (e.g., specific contact volumes, residue lists, statistical significance). For example, the CYP17A1 analysis mentions interaction volumes for N202, D298, and Y201 but does not provide values or comparisons with known binding data. The SPI1 and BRD4 cases similarly lack concrete findings. The claim that volume is more informative is a hypothesis, not a demonstrated conclusion.
  - **Why it matters** The manuscript's scientific value depends on demonstrating that ARIP yields biologically meaningful insights beyond what existing tools provide. Without data, the cases read as anecdotal rather than evidence-based.
  - **Resolution test** Present quantitative results for each case, including specific contact volumes/areas, identification of key residues, and comparisons with experimental or literature data. For the volume-vs-area claim, provide a statistical analysis showing that volume better discriminates functional contacts (e.g., known hot spots) than area.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** The manuscript states that ARIP is available on GitHub and can be installed automatically, implying ease of use and reproducibility.
  - **Evidence pointer** Section 2 (Results), URL provided, but repository not accessed.
  - **Concern** The manuscript does not include installation instructions, dependency lists, or example commands. The "accessed on 6 May 2024" date suggests the repository may have been checked, but no version or DOI is provided. Reproducibility is a key requirement for software tools.
  - **Why it matters** Readers cannot easily test ARIP without clear documentation. Lack of versioning and usage examples undermines the tool's practical utility.
  - **Resolution test** Add a detailed "Availability" section with installation steps, dependencies, example input/output, and a versioned release (e.g., Zenodo DOI). Include a link to a test dataset.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Section 2.2 (Performance)
  - **Evidence pointer** Table 2, location not provided.
  - **Issue** The runtime comparison is mentioned but not interpreted. The authors note ARIP is slower than dr_sasa but do not discuss whether this trade-off is acceptable or how it scales with system size.
  - **Required correction** Add a brief discussion of runtime implications, including scaling behavior and potential optimizations.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Section 4.3.1 (Contact Judgement)
  - **Evidence pointer** Equation (1) and surrounding text.
  - **Issue** The definition of "contact" is based on a distance threshold of 2.8 Å, but the rationale for this specific value is not explained. The relationship between this threshold and the solvent-radius customization is unclear.
  - **Required correction** Justify the 2.8 Å threshold with references or sensitivity analysis, and clarify how it interacts with the solvent-radius settings.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interdisciplinary readership
  - **Affected element** Section 2.3.2 (P4HB/PDI analysis)
  - **Evidence pointer** Figure 5, location not provided.
  - **Issue** The biological significance of the identified residue pairs (A13R–A69E, A25K–A59E) is not explained. Readers unfamiliar with PDI may not understand why these contacts matter.
  - **Required correction** Add a brief biological context for these residues and their potential role in PDI function or pH sensitivity.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Section 4.3.2 (Contact Volumes Calculation)
  - **Evidence pointer** Equation (2) and surrounding text.
  - **Issue** The atomic overlap weighted algorithm is described as "novel," but no comparison with other volume calculation methods (e.g., Voronoi tessellation, alpha shapes) is provided. The novelty claim is not substantiated.
  - **Required correction** Cite related methods and explain how the proposed approach differs and why it is advantageous.
- **Technical failings that need to be addressed before the case is established** 
  1. Lack of quantitative validation for contact area and volume calculations (R1-M1).
  2. Absence of concrete results in the four application cases (R1-M2).
  3. Insufficient algorithmic detail for reproducibility (R1-M1, R1-M3).
  4. No comparison with existing tools or experimental benchmarks (R1-M1).
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The concept of contact volume is not entirely new, but the atomic overlap weighted algorithm and solvent-radius customization offer incremental novelty. However, the manuscript does not clearly position these contributions against prior work.
  - Scientific importance: Limited as presented. The tool could be useful, but the claimed advantages (e.g., volume over area) are not demonstrated. The biological insights from the cases are qualitative and lack depth.
  - Interdisciplinary readership: The tool is relevant to structural biology, biophysics, and computational chemistry, but the manuscript's technical opacity and lack of quantitative results may limit broader appeal.
  - Technical soundness: Not established. The algorithms are described at a high level, and no validation or benchmarking data are provided in the text.
  - Readability for nonspecialists: The manuscript is generally readable but includes jargon (e.g., "mosaic distance," "DSM") without clear definitions. The significance of the results is not made accessible to a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript describes a potentially useful tool, but the scientific claims are unsupported by quantitative data. Major revisions are required to validate the algorithms, present concrete results, and clarify the tool's advantages over existing methods. I would be supportive if these technical concerns are resolved.

## Risk / unsupported claims
- The claim that ARIP provides "precise" calculations is unsupported without validation data.
- The claim that contact volume is "more informative" than contact area is a hypothesis, not demonstrated.
- The biological insights from the four cases (P4HB, CYP17A1, SPI1, BRD4) are qualitative and lack quantitative support.
- The "novel" atomic overlap weighted algorithm is not compared with existing methods.
- The solvent-radius parameters derived from ~5000 structures are described but not validated or compared with standard values.
- The performance benchmark (Table 2) and dataset details (Table S1) are referenced but not provided, making runtime claims unverifiable.