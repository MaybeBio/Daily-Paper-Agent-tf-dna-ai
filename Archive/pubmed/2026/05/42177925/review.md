## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to methods, figures, tables, or supplementary material
- **Shared manuscript claim summary** The authors use molecular dynamics (MD) simulations to characterize how specific post-translational modifications (S305 phosphorylation; K384, K394, K414 acetylation) affect human cGAS catalytic-core complexes, in monomeric and dimeric states, and conclude that PTMs act in a residue-specific manner with K394 acetylation exerting stronger destabilizing effects in the dimeric assembly.
- **Visible evidence base** Abstract text only; no quantitative data, simulation parameters, or structural analyses are provided
- **Missing materials affecting confidence** Full methods, simulation setup and force fields, convergence criteria, structural figures, quantitative metrics (RMSD, contact counts, hydrogen bond occupancies), statistical analyses, and any comparison with experimental data

## Reviewer
- **Overall assessment** The abstract presents a plausible and mechanistically interesting hypothesis, but the evidence base is entirely descriptive. No quantitative results, validation metrics, or methodological details are visible, making it impossible to assess the technical soundness of the simulations or the robustness of the conclusions. The claim that K394 acetylation has a stronger effect in the dimer than in the monomer is a potentially valuable insight, but it is not supported by any numerical comparison in the provided material.
- **Who would be interested in the results, and why** Structural biologists and computational biophysicists studying cGAS regulation and innate immune signaling. Researchers interested in allosteric mechanisms of post-translational modifications in enzyme catalysis would also find the residue-specific framework relevant. The work may appeal to those developing therapeutic strategies targeting cGAS, though the translational relevance is not established from the abstract.
- **Major strengths** The study addresses a clear gap in understanding how PTMs structurally tune cGAS activity. The design comparing monomeric and dimeric states is logical and directly targets the known requirement of DNA-induced dimerization for cGAS function. The focus on site-specific rather than global effects is a nuanced and potentially important framing.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1 (no quantitative evidence), R1-M2 (no methodological validation), R1-M3 (no statistical or convergence support)
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The residue-specific PTM effects on cGAS are not entirely novel, but the monomer-to-dimer comparison for K394 acetylation offers a fresh angle.
  - Scientific importance: Potentially high for the cGAS field, but the abstract does not demonstrate functional consequences beyond structural descriptors.
  - Interdisciplinary readership: Limited from the abstract alone; the work would primarily interest computational and structural biologists, not a broad readership.
  - Technical soundness: Not assessable from the abstract. No simulation details, force field choices, or validation against experimental structures are provided.
  - Readability for nonspecialists: The abstract is reasonably clear but assumes familiarity with cGAS biology and MD simulation terminology.
- **Recommendation posture** Currently not established from the provided evidence. The hypothesis is interesting, but the abstract lacks the quantitative and methodological support needed to evaluate the claims. A supportive posture would require access to the full manuscript.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "K394 acetylation exerting a stronger destabilizing influence in the dimeric assembly than in the monomer"
- **Evidence pointer** Abstract, location not provided
- **Concern** The central comparative claim is presented without any quantitative data. No values for DNA-protein contacts, hydrogen bonding, or ATP-pocket stability are given for either the monomeric or dimeric states, so the reader cannot verify the magnitude or significance of the reported differences.
- **Why it matters** This claim is the main mechanistic takeaway. Without numbers, error bars, or statistical tests, the conclusion is unsupported and could reflect simulation noise or arbitrary thresholds.
- **Resolution test** Provide quantitative metrics (e.g., average contact numbers, hydrogen bond occupancies, RMSD or RMSF values) for each system, with standard deviations and statistical comparisons (e.g., bootstrapping or block averaging) demonstrating that the dimeric K394 acetylation effect is significantly larger than the monomeric effect.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "molecular dynamics simulations" of cGAS complexes with DNA, ATP, Mg(2+), and Zn(2+)
- **Evidence pointer** Abstract, location not provided
- **Concern** No methodological details are given. The force field, water model, ionic conditions, simulation length beyond the stated 1000 ns for dimers, equilibration protocol, and system size are absent. Without this information, the reliability of the simulations cannot be assessed.
- **Why it matters** MD results are highly sensitive to setup choices. Inadequate sampling, incorrect protonation states, or inappropriate force field parameters could invalidate the structural conclusions.
- **Resolution test** Include a methods section or supplementary material specifying all simulation parameters, and demonstrate convergence (e.g., time series of key metrics, block averaging) and, if possible, validation against experimental structures or mutagenesis data.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility and robustness
- **Claim pointer** "PTMs regulate cGAS in a site-specific manner" and "S305 phosphorylation and K414 acetylation weakened ATP engagement"
- **Evidence pointer** Abstract, location not provided
- **Concern** The abstract reports qualitative outcomes ("weakened", "altered", "remodel") without any indication of replicate simulations, statistical significance, or sensitivity analysis. It is unclear whether the observed effects are reproducible across independent runs or robust to minor perturbations in the starting structure.
- **Why it matters** Single-trajectory observations in MD are often unreliable. The field expects multiple replicates or at least a demonstration that the results are consistent across different initial conditions.
- **Resolution test** State the number of independent simulations per system, provide error estimates for all reported metrics, and show that the qualitative conclusions hold across replicates.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract wording
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "catalytic-core complexes" is not defined. It is unclear whether this refers to a specific domain construct or the full-length protein.
- **Required correction** Define the construct used (e.g., residues included, any truncations) in the abstract or methods.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Comparison with experimental data
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract does not mention any comparison with existing experimental studies on cGAS PTMs, which would help contextualize the simulation findings.
- **Required correction** Add a sentence in the discussion or abstract noting whether the simulation results are consistent with known biochemical or structural data on cGAS regulation.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Use of "allosteric"
- **Evidence pointer** Abstract, location not provided
- **Issue** The term "allosteric" is used for K414 acetylation via helix alpha7 rearrangement, but the abstract does not clarify whether this is a local or long-range effect, or how it is distinguished from direct perturbation of the active site.
- **Required correction** Briefly specify the distance or pathway over which the allosteric effect propagates, or justify the use of the term with reference to a defined allosteric network.

## Risk / unsupported claims
- The claim that K394 acetylation has a stronger destabilizing effect in the dimer than in the monomer is unsupported by any quantitative comparison in the abstract.
- The claim that S305 phosphorylation and K414 acetylation weaken ATP engagement is not backed by numerical data or structural evidence.
- The general statement that PTMs "remodel cGAS through residue-specific effects" is plausible but not verifiable from the abstract alone.
- The functional implication for "innate immune signaling" is speculative, as no downstream activity or cellular data are presented.