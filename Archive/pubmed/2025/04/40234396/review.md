## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure/table legends
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and structural/functional evidence presented in the manuscript
- **Shared manuscript claim summary** The authors report the first crystal structure of human MUTYH bound to a transition state analog, identify an H-bond network connecting the [4Fe-4S] cluster to the catalytic Asp236, and propose that this network constitutes an allosteric pathway required for adenine glycosylase activity. Functional profiling of 12 cancer-associated variants near the [4Fe-4S] cluster reveals that most disrupt metal retention and activity, while R241Q and N238S retain metal and DNA binding but are catalytically inactive.
- **Visible evidence base** Crystal structures (human MUTYH-TSAC at 1.9 Å; GsMutY R241Q analog at 1.51 Å), ICP-MS metal analysis, glycosylase activity assays, EMSA binding assays, rifampicin resistance mutation suppression assays, CD spectroscopy, coevolutionary analysis, and MD simulations
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; PDB validation reports not available; raw MD trajectory data not accessible; detailed kinetic fitting parameters not shown; source data files not available for independent verification

## Reviewer
- **Overall assessment** This manuscript presents a valuable structural resource for the DNA repair field, providing the first human MUTYH structure in complex with DNA. The identification of an H-bond network connecting the [4Fe-4S] cluster to the catalytic aspartate is an interesting observation with potential mechanistic significance. However, the central claim of allostery between the cofactor and active site is not fully established by the data presented. The functional profiling of cancer-associated variants is useful but largely confirmatory of previous studies. The structural evidence for the proposed allosteric mechanism is indirect, and the MD simulations, while supportive, do not provide direct evidence of communication between the two sites. The manuscript would be strengthened by additional experiments that directly test the proposed allosteric mechanism, such as examining the effect of cluster oxidation state on active site dynamics or structure.

- **Who would be interested in the results, and why** Researchers in the DNA repair field, particularly those studying base excision repair glycosylases and the role of iron-sulfur clusters in DNA repair enzymes. Cancer geneticists and clinicians interested in MUTYH-associated polyposis and the functional consequences of MUTYH variants will also find the variant profiling useful. Structural biologists studying protein-DNA complexes and metalloproteins may be interested in the structural details. The proposed allosteric mechanism could be of interest to those studying long-range communication in enzymes, though the evidence for this is not yet conclusive.

- **Major strengths**
  1. First crystal structure of human MUTYH bound to DNA, filling an important gap given the clinical significance of this enzyme
  2. Comprehensive functional profiling of 12 cancer-associated variants combining biochemical, biophysical, and cellular assays
  3. Identification of a conserved H-bond network connecting the [4Fe-4S] cluster to the active site, with evolutionary analysis supporting its significance
  4. Integration of structural, functional, and computational approaches to address a mechanistic question
  5. Clear writing and logical organization of results

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The authors claim that the [4Fe-4S] cluster functions to "position and activate the catalytic Asp" through an allosteric network, and that this constitutes a regulatory mechanism for DNA repair function.
- **Evidence pointer** Figures 2, 5; Discussion section
- **Concern** The central claim of allostery between the [4Fe-4S] cluster and the active site is not directly tested. The H-bond network is observed in a static crystal structure, and the MD simulations show changes in dynamics upon mutation, but no experiment directly demonstrates that the cluster state (e.g., oxidation state, occupancy) influences active site geometry or catalysis. The R241Q and N238S mutations could affect catalysis through local structural changes rather than through disruption of a long-range allosteric pathway. The authors do not provide evidence that the cluster itself communicates with the active site, as opposed to the residues merely being part of a structural scaffold.
- **Why it matters** The term "allosteric" implies a regulatory mechanism where a signal at one site affects function at another. Without direct evidence that changes in the cluster (e.g., redox state, ligand binding) alter active site function, the claim of allostery is not established. This is the central conceptual advance claimed by the manuscript, and it requires stronger support.
- **Resolution test** Provide direct experimental evidence that altering the cluster state (e.g., oxidation, removal, or substitution) changes active site structure or catalysis. Alternatively, demonstrate that mutations at the cluster site affect active site dynamics in a way that is consistent with a defined allosteric pathway, using methods such as NMR, HDX-MS, or single-molecule FRET. Computational approaches could also be strengthened by performing perturbation response scanning or other methods that directly map communication pathways.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Technical rigor
- **Claim pointer** The authors state that R241Q and N238S "retained the metal cluster and bound substrate DNA tightly, but were completely inactive."
- **Evidence pointer** Table 1; Figures 3, 4; Supplementary Tables 2-3
- **Concern** The evidence for "complete inactivity" of R241Q and N238S relies on assays with detection limits that are not clearly defined. The activity assays shown in Figure 3A appear to be endpoint assays at a single time point (1 h), and the sensitivity of the assay is not established. It is possible that these variants retain very low but measurable activity that is below the detection limit of the assay. Additionally, the statement that these variants "bound substrate DNA tightly" is based on KD measurements with the fA:OG substrate analog, but the KD values are reported as upper limits for some variants (e.g., <10 pM for WT, V246F, R309C), making quantitative comparisons difficult.
- **Why it matters** The distinction between "completely inactive" and "severely compromised activity" is important for understanding the mechanism. If R241Q and N238S retain trace activity, the interpretation that the allosteric network is completely disrupted would need to be modified. The assay sensitivity should be established to support the strong claim of complete inactivity.
- **Resolution test** Perform activity assays with higher sensitivity (e.g., longer incubation times, higher enzyme concentrations, more sensitive detection methods) to establish the lower limit of detection. Report the limit of detection for the assay. For binding, provide more precise KD measurements or clearly state the detection limits and how they affect interpretation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive caution
- **Claim pointer** The authors propose that the allosteric network "regulates" MUTYH activity in response to cellular conditions, specifically suggesting that redox changes in the [4Fe-4S] cluster could modulate activity.
- **Evidence pointer** Discussion section, paragraphs 3-5
- **Concern** The proposal that redox changes in the cluster regulate activity is speculative and not directly supported by data in this manuscript. While previous work has shown that the cluster can undergo redox cycling, the authors do not provide evidence that this redox change affects the H-bond network or active site function. The discussion of "oxidative stress" as a regulatory condition is not tied to any experimental observation in this study.
- **Why it matters** The manuscript makes claims about the physiological relevance of the proposed allosteric mechanism that extend beyond the data. While speculation in the discussion is acceptable, the authors should clearly distinguish between what is directly supported by their data and what is hypothesis.
- **Resolution test** Either provide experimental evidence linking cluster redox state to activity (e.g., activity assays under oxidizing/reducing conditions, or with cluster-oxidized protein) or temper the language in the discussion to clearly present this as a hypothesis requiring further testing.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical rigor
- **Claim pointer** The authors use MD simulations to support the allosteric network model, claiming that mutations disrupt communication between the cluster and active site.
- **Evidence pointer** Figure 5; Methods section "Molecular dynamics simulations"
- **Concern** The MD simulation methodology has several limitations that are not adequately addressed. The simulations are relatively short (500 ns per replicate), which may not be sufficient to sample the conformational space relevant to allosteric communication. The force field parameters for the [4Fe-4S] cluster are derived from a 2006 publication and may not be optimal for this system. The network analysis methodology is not described in sufficient detail to evaluate its validity. Most importantly, the simulations are performed on the WT and mutant structures, but the initial structures for the mutants are generated by in silico mutation, which may not capture the actual conformational changes induced by the mutations.
- **Why it matters** The MD simulations provide key supporting evidence for the allosteric mechanism. If the simulations are not robust, the support for the central claim is weakened. The field has become increasingly aware of the limitations of MD simulations in studying allostery, and the authors should address these limitations.
- **Resolution test** Provide more detailed methodology for the network analysis, including validation of the approach. Consider longer simulations or enhanced sampling methods. Validate the in silico mutant structures against experimental data where available. Discuss the limitations of the force field parameters for the [4Fe-4S] cluster.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Completeness
- **Claim pointer** The authors state that the H-bond network is "conserved in structure across evolution" and that this conservation supports its functional significance.
- **Evidence pointer** Figure 2E; Supplementary Figure 5
- **Concern** The conservation analysis is limited to a small number of sequences and does not include a quantitative phylogenetic analysis. The authors show a sequence logo and alignment for a few representative species, but this is not a comprehensive evolutionary analysis. The claim of conservation would be strengthened by a more systematic analysis across a larger and more diverse set of MUTYH/MutY sequences.
- **Why it matters** Evolutionary conservation is used as evidence for functional significance. A more rigorous analysis would strengthen this argument and help distinguish functionally important residues from those that are merely structurally constrained.
- **Resolution test** Perform a comprehensive phylogenetic analysis across a large set of MUTYH/MutY sequences, including statistical tests for conservation of the specific residues in the H-bond network. Alternatively, use methods such as EVcouplings or similar approaches to assess coevolutionary constraints.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, last sentence
- **Issue** The abstract states that the results "suggest that allosteric cross-talk between the DNA binding [4Fe-4S] cofactor and the base excision site of MUTYH regulate its DNA repair function." The word "regulate" implies a dynamic regulatory mechanism, but the data primarily show a structural connection. Consider using more cautious language such as "may regulate" or "is consistent with a regulatory role."
- **Required correction** Revise the abstract to more carefully reflect the strength of the evidence, using language that distinguishes between direct demonstration and inference.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, activity assays
- **Evidence pointer** Methods section "Glycosylase assay and binding experiments"
- **Issue** The description of the activity assay conditions is incomplete. The buffer composition, temperature, and time course details are not fully specified. The equation for the kinetic scheme is provided, but the fitting procedure and error analysis are not described in sufficient detail.
- **Required correction** Provide complete details of assay conditions and data fitting procedures to allow replication.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 3
- **Evidence pointer** Figure 3A, 3B
- **Issue** The activity and binding data are presented as bar graphs with error bars, but the individual data points are not shown. Given the small number of replicates (n=3), showing individual data points would help assess the variability and the robustness of the conclusions.
- **Required correction** Consider showing individual data points alongside the bar graphs, or using dot plots.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretive caution
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph on therapeutic implications
- **Issue** The suggestion that the [4Fe-4S] cluster could be "targeted in cancer cells" is highly speculative and not supported by any data in this manuscript. While this is presented as a possibility, it may be premature and could be seen as overreach.
- **Required correction** Either remove this speculation or clearly label it as a distant possibility requiring substantial further investigation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, MD simulations
- **Evidence pointer** Methods section "Molecular dynamics simulations"
- **Issue** The description of the MD simulation protocol is brief. Details such as the specific AMBER force field version, water model, salt concentration, equilibration protocol, and analysis tools are not fully specified. The convergence of the simulations is not discussed.
- **Required correction** Provide a more complete description of the simulation protocol and include convergence analysis.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, variant classification
- **Evidence pointer** Figure 6
- **Issue** The classification of variants into functional groups is clear, but the criteria for grouping are not explicitly stated in the text. It would be helpful to define the thresholds used to categorize variants as "inactive," "partially active," or "WT-like."
- **Required correction** Add explicit criteria for variant classification in the text or figure legend.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, crystallography
- **Evidence pointer** Methods section "Crystallography"
- **Issue** The crystallographic refinement statistics are referenced to Supplementary Table 4, but the quality of the electron density for the H-bond network residues is not discussed. Given the importance of this network to the central claim, a more detailed description of the density for these residues would be valuable.
- **Required correction** Add a description of the electron density quality for the key residues in the H-bond network, possibly with a supplementary figure showing the density.

## Risk / unsupported claims
1. The claim of "allostery" between the [4Fe-4S] cluster and active site is not directly demonstrated; the data show a structural connection and correlated dynamics in simulations, but no experiment directly tests whether cluster state affects active site function.
2. The proposal that redox changes in the [4Fe-4S] cluster regulate MUTYH activity in response to cellular conditions is speculative and not supported by direct experimental evidence in this manuscript.
3. The statement that R241Q and N238S are "completely inactive" may be too strong given the lack of defined assay detection limits.
4. The claim that the H-bond network is "conserved across evolution" is based on limited sequence analysis and would benefit from a more comprehensive phylogenetic study.
5. The therapeutic speculation regarding targeting the [4Fe-4S] cluster in cancer cells is not supported by data presented here.
6. The functional significance of the alternative [4Fe-4S] cluster conformations observed in the GsMutY R241Q structure is inferred but not directly tested.
7. The relationship between the proposed allosteric mechanism and the previously proposed redox-based DNA scanning mechanism is not experimentally addressed, leaving the physiological relevance of the allosteric network unclear.