## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full methods, figures, tables, or supplementary data
- **Shared manuscript claim summary** The authors report an in silico study proposing that ceftriaxone induces conformational changes in NF-kB that enhance its binding to the EAAT-2 promoter region at gene locus -272, thereby explaining ceftriaxone-mediated EAAT-2 expression. They used homology modeling, HADDOCK protein-DNA docking, and 250 ns molecular dynamics simulations to compare pre- and postdocked NF-kB conformations.
- **Visible evidence base** Abstract text only; no quantitative results, structural coordinates, simulation parameters, or validation metrics are provided
- **Missing materials affecting confidence** Full methods, docking scores and energy terms (numerical values), MD simulation trajectories and analyses, structural figures, model validation (e.g., Ramachandran plots, QMEAN/Z-scores), DNA sequence context, and any experimental validation

## Reviewer
- **Overall assessment** The abstract presents a plausible computational hypothesis linking ceftriaxone to NF-kB conformational changes and EAAT-2 promoter binding. However, the evidence base is insufficient to establish the central claim. Key quantitative data, model validation, and methodological details are absent. The study is exploratory and hypothesis-generating, but the current abstract does not support definitive conclusions about the molecular mechanism.
- **Who would be interested in the results, and why** Researchers in neuropharmacology, particularly those studying excitotoxicity, EAAT-2 regulation, and neuroprotective agents. Computational biologists interested in protein-DNA docking and MD simulation approaches may also find the methodological framework relevant. Clinicians exploring ceftriaxone repurposing for neurodegenerative conditions could have peripheral interest.
- **Major strengths** The study addresses a clinically relevant question with potential therapeutic implications. The combination of docking and MD simulations is an appropriate computational strategy for investigating protein-DNA interactions. The focus on a specific DNA locus (-272) provides a testable hypothesis.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 (model validation), R1-M2 (quantitative evidence), R1-M3 (causal inference), R1-M4 (simulation rigor)
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The application of docking and MD to this specific system is not unprecedented, and the abstract does not demonstrate a novel methodological advance.
  - Scientific importance: Potentially relevant to neuroprotection, but the abstract does not establish biological significance beyond a computational prediction.
  - Interdisciplinary readership: The topic bridges pharmacology and computational biology, but the abstract lacks sufficient detail to engage a broad audience.
  - Technical soundness: Cannot be assessed from the abstract alone. Critical validation and methodological details are missing.
  - Readability for nonspecialists: The abstract is dense with technical terms and acronyms, and the logical flow from hypothesis to conclusion is not clearly articulated.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is supportive of further investigation, but the central claim requires substantial additional evidence and validation.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Model validity
- **Claim pointer** The authors claim to have used a "homology-built model of NF-kB" for docking and simulation studies.
- **Evidence pointer** Abstract, location not provided
- **Concern** No information is provided about the template used for homology modeling, sequence identity, or model quality metrics. Without validation of the NF-kB model, all downstream docking and simulation results are built on an unverified foundation.
- **Why it matters** A poorly constructed or inaccurate protein model would invalidate the docking results and the subsequent conformational analysis. The central claim depends entirely on the reliability of this model.
- **Resolution test** Provide template information, sequence identity, and validation scores (e.g., QMEAN, PROCHECK, or MolProbity). Show that the model is structurally reasonable and suitable for docking studies.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative evidence
- **Claim pointer** The authors state that "both the protein and DNA exhibited modest conformational changes with respect to HADDOCK score, energy terms... root mean square deviation, RMSF, radius of gyration, total hydrogen bonds."
- **Evidence pointer** Abstract, location not provided
- **Concern** No numerical values are provided for any of the listed metrics. The term "modest" is subjective and cannot be evaluated without data. It is unclear whether the observed changes are statistically significant or biologically meaningful.
- **Why it matters** The conclusion that ceftriaxone induces conformational changes relies on these metrics. Without quantitative results, the claim is unsupported and cannot be independently verified.
- **Resolution test** Provide a table or figure with numerical values for HADDOCK scores, energy terms, RMSD, RMSF, Rg, and hydrogen bond counts for both pre- and postdocked conditions, including error estimates or replicate information.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal inference
- **Claim pointer** The authors conclude that "conformational changes in the C-terminal domain could be the reason for EAAT-2 expression through ceftriaxone specific binding pocket of -272 of DNA."
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract describes a correlation between ceftriaxone presence and conformational changes in a computational model. It does not establish a causal link between these conformational changes and EAAT-2 expression. The phrase "could be the reason" is speculative and not supported by the presented evidence.
- **Why it matters** The central hypothesis of the study is that ceftriaxone promotes EAAT-2 expression via NF-kB binding. Without experimental validation or a mechanistic link, the conclusion remains a hypothesis, not an established finding.
- **Resolution test** Provide experimental evidence (e.g., reporter assays, gene expression analysis, or mutagenesis studies) linking the predicted conformational changes to functional EAAT-2 expression. Alternatively, clearly frame the conclusion as a hypothesis requiring experimental testing.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Simulation rigor
- **Claim pointer** The authors report "250 ns long all atom explicit solvent molecular dynamics simulations."
- **Evidence pointer** Abstract, location not provided
- **Concern** No details are provided on the force field, water model, ion concentration, temperature/pressure coupling, equilibration protocol, or convergence criteria. The choice of 250 ns may or may not be sufficient for the system, and this cannot be assessed without additional information.
- **Why it matters** MD simulation results are highly dependent on simulation parameters. Without these details, the reliability and reproducibility of the simulations cannot be evaluated.
- **Resolution test** Provide full simulation parameters, including software version, force field, water model, salt concentration, and convergence analysis (e.g., block averaging or RMSD plateau). Justify the 250 ns timescale for the system under study.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract structure
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract is dense and lacks a clear logical progression. The transition from the biological rationale to the computational methods and then to the conclusion is abrupt.
- **Required correction** Restructure the abstract to clearly separate background, objective, methods, key results, and conclusion. Use explicit signposting language.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "gene locus -272"
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "gene locus -272" is ambiguous. It is unclear whether this refers to a specific nucleotide position relative to a transcription start site, a regulatory element, or a genomic coordinate.
- **Required correction** Define the coordinate system and provide the genomic context (e.g., chromosome, gene name, and reference genome version).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Software version
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract mentions "HADDOCK 2.2 web server" but does not specify the version of the underlying software or the docking protocol used.
- **Required correction** Provide the exact software version, docking parameters, and any relevant web server settings to ensure reproducibility.

## Risk / unsupported claims
- The claim that ceftriaxone induces conformational changes in NF-kB leading to EAAT-2 expression is unsupported by the abstract alone. No experimental validation is provided.
- The assertion that "conformational changes in the C-terminal domain could be the reason for EAAT-2 expression" is speculative and not substantiated by the presented data.
- The statement that the study "predicted the in silico model for interaction between NF-kB and EAAT-2 promoter region" is not verifiable without access to the model and its validation.
- All quantitative claims regarding docking scores, energy terms, and MD metrics are unverifiable as no numerical data are presented.
- The biological relevance of the predicted binding at locus -272 cannot be assessed without genomic context and functional studies.