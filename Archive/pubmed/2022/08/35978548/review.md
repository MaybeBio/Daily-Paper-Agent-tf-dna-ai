## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract, as supplied
- **Shared manuscript claim summary** The authors propose that intrinsic flexibility of DNA flanking sequences, rather than static shape alone, allosterically modulates transcription factor (TF) binding affinity at a core motif, based on molecular dynamics simulations of Hox heterodimers Exd-Ubx and Exd-Scr with DNA.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or simulation details provided
- **Missing materials affecting confidence** Full manuscript, simulation protocols, force field parameters, statistical analyses, sequence constructs, experimental binding data, and any validation against experimental measurements

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially significant hypothesis that DNA flexibility in flanking regions influences TF binding affinity at a core motif. However, the evidence base is limited to a summary of simulation results, with no quantitative data, methodological details, or experimental validation. The claim that flexibility "percolates" and "allosterically modulates" binding is intriguing but not substantiated from the supplied material. The study could be of interest to the biophysics and gene regulation communities, but the current abstract does not establish the case convincingly.
- **Who would be interested in the results, and why** Researchers in DNA-protein recognition, transcription regulation, and computational biophysics would be interested, as the work addresses a fundamental question about how DNA sequence context beyond the core motif affects TF binding. The potential to refine predictive models of TF binding sites could also appeal to genomics and synthetic biology audiences.
- **Major strengths** The hypothesis is clearly articulated and addresses a gap in the field, namely the role of dynamic DNA flexibility versus static shape. The use of closely related Hox heterodimers provides a controlled comparative system. The abstract explicitly distinguishes between localized shape features and nonlocal flexibility effects, which is a conceptually useful framing.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract lacks any quantitative metrics (e.g., binding free energies, flexibility parameters, statistical significance) and does not describe how flexibility was measured or how "percolation" was assessed. Without these, the central claims are not testable from the provided material.
- **Assessment against Nature-style criteria** 
  - Originality: The idea that flanking DNA flexibility modulates TF binding is not entirely new, but the specific focus on allosteric percolation of flexibility is a fresh angle. However, originality cannot be fully assessed without comparison to prior literature.
  - Scientific importance: If substantiated, the findings could have broad implications for understanding TF binding specificity and predicting regulatory elements. The importance is high but conditional on evidence.
  - Interdisciplinary readership: The topic bridges biophysics, molecular biology, and computational biology, which could attract a broad audience. However, the abstract is written in a specialized manner that may limit accessibility.
  - Technical soundness: Not assessable from the abstract alone. No details on simulation convergence, force field accuracy, or statistical treatment are provided.
  - Readability for nonspecialists: The abstract is dense and uses jargon (e.g., "ternary complex," "percolate") without clear definitions, which would hinder nonspecialist comprehension.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is interesting, but the abstract does not provide sufficient data or methodological transparency to support the claims. A revised version with quantitative results and experimental context could change this assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The abstract claims that "flexibility features of the flanking sequences percolate several basepairs and allosterically modulate TF binding at the core."
- **Evidence pointer** Abstract, location not provided
- **Concern** The claim of allosteric modulation via flexibility percolation is presented as a definitive finding, but no quantitative data, such as correlation coefficients, free energy changes, or flexibility profiles, are provided. The abstract does not specify how "percolation" was defined or measured, nor does it show comparative data between the two heterodimers.
- **Why it matters** This is the central novel claim of the study. Without quantitative evidence, the claim remains speculative and cannot be evaluated for robustness or significance.
- **Resolution test** Provide specific numerical results, such as flexibility scores at varying distances from the core, and demonstrate a statistically significant correlation with binding affinity. Include error bars and statistical tests.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological transparency
- **Claim pointer** The study "employed experimentally guided molecular dynamics simulations" to reach its conclusions.
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract does not describe the experimental guidance, simulation length, force field, or system setup. It is unclear whether the simulations were validated against experimental binding data or whether the "experimental guidance" refers to initial structures or restraints.
- **Why it matters** Molecular dynamics results are highly sensitive to simulation parameters and force field choices. Without this information, the technical soundness of the simulations cannot be assessed, and the results may not be reproducible.
- **Resolution test** Include a methods summary in the abstract or main text detailing simulation protocols, force field, equilibration, and any experimental constraints. State how experimental data were used and whether results were compared to measured affinities.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The abstract states that "lack of flexibility in the motif context can render the cognate site resistant to protein-induced shape changes and subsequently lower TF binding affinity."
- **Evidence pointer** Abstract, location not provided
- **Concern** This causal chain is asserted without direct evidence. The abstract does not show data on protein-induced shape changes, nor does it quantify how flexibility differences translate into affinity changes. The link between flexibility, shape change, and affinity is inferred but not demonstrated.
- **Why it matters** This is a key mechanistic conclusion. If unsupported, it weakens the overall argument that flexibility is a determinant of affinity.
- **Resolution test** Provide simulation snapshots or analyses showing that rigid flanking sequences reduce conformational changes at the core, and correlate these with computed or measured binding affinities.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract terminology
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "percolate" is used metaphorically but not defined. It is unclear whether it refers to a physical propagation of flexibility or a statistical correlation.
- **Required correction** Define "percolate" in operational terms, such as "flexibility changes propagate over a distance of X base pairs," or replace with more precise language.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Contextualization
- **Affected element** Abstract background
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not mention prior work on DNA shape or flexibility in TF binding, so the novelty of the claim is not contextualized.
- **Required correction** Add a sentence referencing key prior studies and explicitly state what new insight this work provides.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract structure
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract moves from general background to specific results without a clear logical flow, making it hard for nonspecialists to follow the main argument.
- **Required correction** Restructure the abstract to state the hypothesis, the approach, the key finding, and the implication in a more linear fashion.

## Risk / unsupported claims
- The claim that flanking DNA flexibility "percolates" and allosterically modulates TF binding is unsupported by quantitative data in the abstract.
- The assertion that lack of flexibility causes resistance to protein-induced shape changes and lowers affinity is not evidenced.
- The general conclusion that "flexibility-guided DNA shape" is a key component of the recognition code is an overreach from the abstract alone, as no comparative analysis with static shape models is presented.
- The relevance of the findings to "several million putative sites" in the eukaryotic genome is asserted but not demonstrated, as the study only examines two heterodimers.