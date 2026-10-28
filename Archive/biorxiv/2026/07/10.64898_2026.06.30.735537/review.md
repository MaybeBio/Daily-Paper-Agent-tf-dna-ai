## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary figure descriptions
- **Assessment boundary** Scientific claims, methodological soundness, and interpretational validity based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors use coarse-grained molecular dynamics simulations with backmapping to investigate how phosphorylation at CLOCK S38/42 and BMAL1 S78 remodels the CLOCK–BMAL1–nucleosome complex, reporting asymmetric effects on DNA binding, altered histone interactions, rewired allosteric communication networks, and a structural priming model for CRY1 recruitment
- **Visible evidence base** Methods descriptions, results narrative, figure references (Figures 1–9), supplementary figure references, and data availability statement
- **Missing materials affecting confidence** Actual figures and supplementary figures not provided; quantitative values for contact numbers, angles, and correlation coefficients not provided; simulation convergence metrics not provided; force field validation details not provided; backmapping validation not provided

## Reviewer

- **Overall assessment** This manuscript presents a computational investigation of phosphorylation effects on the CLOCK–BMAL1–nucleosome complex using coarse-grained molecular dynamics simulations. The topic is timely and relevant to the circadian biology field, and the authors address an important gap by explicitly including the nucleosomal context. However, the manuscript as presented has substantial limitations in methodological transparency, quantitative reporting, and validation of the simulation approach. The central claims regarding asymmetric phosphorylation effects and allosteric remodeling are plausible but cannot be fully evaluated from the provided text alone. The authors also report a discrepancy with prior experimental findings that is acknowledged but not resolved mechanistically. The structural model for CRY1 recruitment is speculative and requires clearer caveats.

- **Who would be interested in the results, and why** Circadian biology researchers studying post-translational regulation of the molecular clock, computational biophysicists interested in protein–DNA and protein–nucleosome interactions, and structural biologists studying transcription factor complexes on chromatin. The potential therapeutic implications for circadian-related disorders may also interest pharmaceutical researchers targeting clock proteins.

- **Major strengths**
  1. The study addresses a biologically important question: how phosphorylation of CLOCK and BMAL1 modulates their interaction with nucleosomal DNA in a chromatin context, which goes beyond previous biochemical studies using naked DNA.
  2. The use of a recently resolved cryo-EM structure as a starting point for simulations is appropriate and leverages state-of-the-art structural data.
  3. The systematic comparison of four phosphorylation states (WT, single, and double phosphomimetic) is a well-designed computational strategy.
  4. The authors acknowledge and discuss a discrepancy with prior experimental results, which demonstrates scientific honesty.
  5. The integration of multiple analysis techniques (contact analysis, pulling simulations, correlation analysis, allosteric pathway analysis) provides a multi-faceted view of the system.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The authors claim that their simulations reveal phosphorylation-dependent remodeling of the CLOCK–BMAL1–nucleosome complex based on coarse-grained MD simulations and backmapping.
- **Evidence pointer** Methods section, "Coarse-Grained Molecular Dynamics Simulations and Backmapping"
- **Concern** The manuscript lacks critical validation of the coarse-grained simulation approach. No information is provided on the equilibration protocol beyond a brief description, no convergence analysis is shown, and the backmapping procedure is described without any validation that the backmapped atomistic structures faithfully reproduce the CG ensemble. The authors state that energy drift was minimal, but this is insufficient to establish that the simulations sampled equilibrium distributions. Additionally, the choice of the Martini 2.2 force field with the ElNeDyn elastic network for a large protein–DNA–nucleosome complex requires justification, particularly regarding whether the elastic network might bias the observed dynamics.
- **Why it matters** Without demonstrated convergence and validation of the simulation methodology, the quantitative and even qualitative conclusions drawn from the trajectories cannot be considered reliable. The central claims of the paper depend entirely on the fidelity of these simulations.
- **Resolution test** Provide RMSD and RMSF time series for all systems showing equilibration, block-averaging or similar convergence analysis for key observables, validation of backmapping by comparing structural properties between CG and atomistic representations, and a discussion of force field limitations and potential artifacts.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative evidence
- **Claim pointer** The authors report specific changes in contact numbers, inter-domain angles, and correlation patterns across phosphorylation states, including claims such as "phosphorylation equalizes the mechanical stability" and "increases the separation between the CLOCK HI loop and the H3 α1–L1 elbow."
- **Evidence pointer** Results section, Figures 2–5, Supplementary Figures 8–13
- **Concern** The manuscript does not provide any quantitative values, statistical measures, or error estimates for the reported observables. Contact numbers are described qualitatively as "bimodal distributions centered at approximately 10 and 30 contacts," but no standard deviations, standard errors, or statistical comparisons between systems are given. The pulling simulation results are described without force–distance curves, rupture forces, or statistical analysis across replicates. The PCA results are described without variance explained or projection densities.
- **Why it matters** The scientific claims are inherently quantitative, and without numerical values and appropriate statistics, the reader cannot assess the magnitude, significance, or robustness of the reported effects. This is particularly important given the acknowledged discrepancy with prior experimental results.
- **Resolution test** Provide mean and standard deviation or standard error for all key observables across the five replicates, perform appropriate statistical tests comparing systems, show representative force–distance curves from pulling simulations with statistics across the ten replicates, and report variance explained for PCA modes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretational validity
- **Claim pointer** The authors propose a structural model in which CLOCK phosphorylation acts as a priming event that facilitates CRY1 recruitment by increasing the separation between the CLOCK HI loop and the H3 α1–L1 elbow, thereby providing a more permissive environment for CRY1 binding.
- **Evidence pointer** Results section, "Phosphorylation-induced modulation of protein dynamics reshapes global conformational motions"; Discussion; Figure 9
- **Concern** The proposed model for CRY1 recruitment is based on a single computational observation (increased HI loop–H3 elbow separation) and a static model of the CRY1–CLOCK–BMAL1–nucleosome complex. The authors do not simulate the CRY1-bound state, do not provide free energy calculations, and do not test whether the observed separation is sufficient or necessary for CRY1 binding. The claim that phosphorylation "provides a more permissive environment" is speculative and goes beyond what the simulation data can support. Additionally, the authors note that the separation in their model (ca. 40 Å) exceeds that observed in simulations (ca. 20 Å), which raises questions about the relevance of the model.
- **Why it matters** This model is presented as a key mechanistic insight of the paper. If the connection between phosphorylation-induced conformational changes and CRY1 recruitment is not rigorously established, the central narrative of the paper is weakened.
- **Resolution test** Either temper the claims to clearly state this as a hypothesis requiring experimental validation, or provide additional computational evidence such as docking calculations, free energy perturbation, or enhanced sampling simulations of CRY1 binding to the phosphorylated versus unphosphorylated complex.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors state that "each frame taken from the CG simulations was converted into an all-atom representation" using the cg2at workflow, and that the trajectories are deposited in an OSF repository.
- **Evidence pointer** Methods section, "Coarse-Grained Molecular Dynamics Simulations and Backmapping"; Data Availability Statement
- **Concern** The methods description lacks sufficient detail for reproduction. The cg2at workflow is referenced but not described in terms of its specific parameters or settings. The selection of frames for backmapping is not specified (all frames? every nth frame?). The number of frames backmapped is not stated. The OSF repository link is provided, but it is unclear whether the deposited data includes all input files, parameter files, and analysis scripts needed for full reproduction.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without complete methodological details and accessible data, other researchers cannot verify or build upon these results.
- **Resolution test** Provide a complete description of the cg2at parameters, specify the frame selection and total number of backmapped frames, and ensure the repository contains all necessary input files, topology files, and analysis scripts.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Literature integration
- **Claim pointer** The authors state that "phosphorylation of the CLOCK/BMAL1 complex is a reversible post-translational modification that plays a central role in regulating circadian oscillations" and that their findings "provide a mechanistic framework for circadian transcriptional repression."
- **Evidence pointer** Abstract; Introduction; Discussion
- **Concern** The manuscript does not adequately engage with the existing computational and experimental literature on CLOCK–BMAL1 dynamics and phosphorylation. The authors mention the prior study by Otobe et al. but do not discuss other relevant studies on CLOCK–BMAL1 conformational dynamics, phosphorylation effects on bHLH transcription factors, or computational studies of transcription factor–nucleosome interactions. The discussion of how their findings relate to the broader circadian field is limited.
- **Why it matters** The novelty and significance of the findings can only be assessed in the context of prior work. Without proper contextualization, the reader cannot determine what is genuinely new versus what confirms or extends existing knowledge.
- **Resolution test** Expand the introduction and discussion to include relevant prior computational and experimental studies on CLOCK–BMAL1 dynamics, phosphorylation effects on DNA binding, and nucleosome interactions, and clearly articulate how the present findings advance beyond this prior work.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The abstract states that phosphorylation is "a reversible post-translational modification that plays a central role in regulating circadian oscillations" but does not specify which kinase or phosphatase is responsible, nor does it mention the broader context of CLOCK–BMAL1 regulation by multiple post-translational modifications.
- **Required correction** Briefly mention the relevant kinase(s) or clarify that the study focuses on the structural consequences of phosphorylation rather than its enzymatic regulation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results section
- **Evidence pointer** Results, "Phosphorylation exhibits asymmetric effects" section
- **Issue** The term "bimodal binding mode" is used to describe the contact distribution, but the manuscript does not define what constitutes a "binding mode" in this context or how the two modes differ structurally beyond contact counts.
- **Required correction** Provide a brief definition of what distinguishes the two binding modes structurally, or use more neutral terminology such as "two populations of contact states."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 9
- **Evidence pointer** Results, "Phosphorylation-induced modulation of protein dynamics reshapes global conformational motions"
- **Issue** The description of Figure 9 is minimal and does not explain how the CRY1–CLOCK–BMAL1–nucleosome model was constructed, what structural data were used, or what the key features of the model are.
- **Required correction** Provide a detailed figure legend explaining the model construction, the source of the CRY1 structure, and the key interactions shown.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section
- **Evidence pointer** Results, "Phosphorylation of CLOCK and BMAL1 bHLH Domains Remodels Nucleosomal Interactions"
- **Issue** The manuscript states that phosphorylation "reduces interactions" and "increases contact" without providing any numerical values or statistical significance for these changes.
- **Required correction** Add quantitative values with appropriate statistical measures for all reported changes in contacts, distances, and correlations.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results and Discussion
- **Evidence pointer** Results, "Phosphorylation rewires allosteric communication networks"; Discussion
- **Issue** The authors refer to "CLOCK S38/S42" in some places and "CLOCK S38/42" in others, and similarly use "BMAL1 S78" and "BMAL1 S78E" inconsistently. This creates confusion about whether the discussion refers to the phosphomimetic mutations or the wild-type residues.
- **Required correction** Standardize the nomenclature throughout the manuscript, clearly distinguishing between the wild-type residues and the phosphomimetic substitutions.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Language
- **Affected element** Throughout
- **Evidence pointer** Multiple sections
- **Issue** The manuscript contains several typographical errors and awkward phrasings, such as "Principle component analysis" instead of "Principal component analysis," "biochemica" instead of "biochemical," and "atomistic-leve" instead of "atomistic-level."
- **Required correction** Thorough proofreading and language editing.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability Statement
- **Evidence pointer** Data Availability Statement
- **Issue** The statement says "Softwares used in the study are owned by their respective developers," which is not a data availability statement. It does not clarify what analysis scripts, parameter files, or processed data are available.
- **Required correction** Provide a proper data availability statement that lists all deposited data, analysis scripts, and any additional materials needed for reproduction.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Reference formatting
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, references 1–28; Discussion, references 44–56
- **Issue** The reference list is not provided in the manuscript text, and the in-text citations are numbered without a corresponding reference list. This makes it impossible to verify the cited literature.
- **Required correction** Include a complete reference list with full bibliographic details.

## Risk / unsupported claims
- The claim that "phosphorylation equalizes the mechanical stability of CLOCK and BMAL1 interactions with DNA" is not supported by quantitative data from the pulling simulations, as no force values, work values, or statistical comparisons are provided.
- The claim that CLOCK phosphorylation "may initiate the formation of space required for CRY binding" is speculative and not directly tested in the simulations.
- The claim that phosphorylation "rewires allosteric communication networks" is based on correlation and pathway analyses, but the statistical significance and robustness of these network changes are not established.
- The claim that the double phosphomimetic system "converges" with the BMAL1 S78E system in communication profile is not quantitatively demonstrated.
- The biological relevance of the observed conformational changes for circadian regulation is inferred but not experimentally validated.
- The discrepancy with the Otobe et al. experimental results is acknowledged but not mechanistically resolved, leaving the relationship between the simulation findings and experimental observations unclear.
- The simulation timescales (10 μs per replicate) may be insufficient to capture the full conformational landscape of such a large complex, and this limitation is not discussed.