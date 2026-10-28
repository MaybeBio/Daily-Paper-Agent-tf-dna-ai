## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full methods, figures, or supplementary data
- **Shared manuscript claim summary** The authors report the computational design and experimental validation of a disulfide-stapled peptide trap derived from the TEAD4 helical hairpin, intended to bind the YAP alpha1-helix and disrupt TEAD4-YAP interaction. They report improved binding affinity (up to 8.5-fold) upon stapling, structural stabilization in free state, and tumor-suppressive activity in a cellular assay when fused to a TAT sequence.
- **Visible evidence base** Abstract text only; no figures, tables, methods, or numerical data beyond the stated fold improvement
- **Missing materials affecting confidence** Full methods, structural models, circular dichroism spectra, affinity assay data, cellular assay details, statistical analyses, and any control experiments

## Reviewer
- **Overall assessment** The abstract presents a conceptually interesting inversion of the usual peptide-inhibitor design strategy, namely deriving a binder from the TEAD4 surface rather than from YAP. However, the evidence provided is insufficient to evaluate the technical soundness of the design, the robustness of the experimental validation, or the specificity of the claimed antitumor effect. The central claims are plausible but not established from the supplied material.
- **Who would be interested in the results, and why** Researchers in peptide drug design, protein-protein interaction inhibition, and Hippo pathway biology would find the concept of a TEAD4-derived YAP trap of interest. The potential therapeutic angle for cancers driven by Hippo dysregulation may also attract translational oncology groups.
- **Major strengths** The design rationale is clear and represents a departure from prior YAP-derived inhibitors. The use of a disulfide staple to pre-organize the helical hairpin is a sensible strategy to reduce entropic penalty. The abstract reports both molecular-level affinity improvement and cellular-level activity, which is a useful progression.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** 
  - Originality: The concept of deriving a trap from the TEAD4 helical hairpin is novel relative to prior YAP-derived inhibitors, but the abstract does not demonstrate how this differs functionally from existing approaches beyond the source of the peptide.
  - Scientific importance: Disrupting TEAD4-YAP interaction is a relevant target in cancer biology, and a selective YAP alpha1-helix trap could be a useful tool. However, the abstract does not provide evidence of selectivity over other YAP regions or other TEAD isoforms.
  - Interdisciplinary readership: The work spans computational design, biophysics, and cell biology, which could appeal to a broad audience. However, the abstract lacks sufficient quantitative detail to engage specialists in any one discipline.
  - Technical soundness: Not assessable from the abstract alone. Key details on simulation methods, affinity assay formats, and cellular endpoints are missing.
  - Readability for nonspecialists: The abstract is generally readable, but terms such as "Omega-loop" and "three-helix bundle" are used without brief explanation, which may hinder nonspecialist comprehension.
- **Recommendation posture** Currently not established from the provided evidence. The concept is promising, but the abstract does not provide enough data to support the central claims of selective binding, stapling benefit, and antitumor activity. A full manuscript with detailed methods and controls would be required for a supportive assessment.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Specificity and selectivity
- **Claim pointer** The trap is claimed to "selectively capture YAP alpha1-helix" and to disrupt TEAD4-YAP interaction.
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract does not provide any data demonstrating selectivity for the YAP alpha1-helix over the Omega-loop region or over other potential binding partners. No competition assays, mutagenesis controls, or off-target binding measurements are described.
- **Why it matters** The stated therapeutic strategy depends on specific disruption of the TEAD4-YAP interaction. Without evidence of selectivity, the observed cellular effects could arise from non-specific peptide activity or off-target binding.
- **Resolution test** Provide binding assays against YAP Omega-loop peptides, unrelated helical peptides, and TEAD family isoforms. Include competition experiments with full-length YAP and a negative control stapled peptide with scrambled sequence.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative evidence and reproducibility
- **Claim pointer** The stapling "considerably improve[s] the trap binding potency to YAP alpha1-helix by up to 8.5-fold" and the trap exhibits "good tumor-suppressing effect at cellular level."
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract reports only a single fold-improvement value and a qualitative cellular outcome. No absolute affinity values, dose-response curves, replicate numbers, error estimates, or statistical significance are provided. The cellular assay endpoint is not specified (e.g., viability, proliferation, apoptosis).
- **Why it matters** Quantitative claims without error bars or statistical tests cannot be evaluated for robustness. The cellular effect is described qualitatively, which is insufficient to judge the magnitude or specificity of the antitumor activity.
- **Resolution test** Report equilibrium dissociation constants (Kd) for stapled and unstapled traps with standard deviations from at least three independent experiments. Provide dose-response curves and statistical analysis for the cellular assay, including a non-functional control peptide.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural and mechanistic validation
- **Claim pointer** The disulfide staple "effectively constrain[s] the trap into a native-like structured conformation in free state" and the trap forms a "three-helix bundle" with YAP alpha1-helix.
- **Evidence pointer** Abstract text; location not provided
- **Concern** Circular dichroism is mentioned as evidence of conformational constraint, but no spectra, secondary structure content estimates, or comparison to the unstapled peptide are shown. The claimed three-helix bundle geometry is not supported by any structural data, such as NMR, X-ray crystallography, or validated computational models.
- **Why it matters** The design rationale rests on the pre-organization of the hairpin and the formation of a specific three-helix complex. Without structural evidence, the mechanism of binding remains speculative, and the observed affinity improvement could arise from other factors.
- **Resolution test** Provide circular dichroism spectra for stapled and unstapled peptides with secondary structure deconvolution. Include a structural model or experimental structure of the trap in complex with YAP alpha1-helix, or at minimum a validated docking simulation with binding free energy calculations.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of terminology
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term "YAP helix(alpha1)-trap" is used without a clear definition of what distinguishes it from a conventional peptide inhibitor. The phrase "native double-stranded helical hairpin" is also ambiguous regarding the peptide length and the exact TEAD4 region used.
- **Required correction** Define the trap construct explicitly, including the TEAD4 residue range, the peptide length, and the position of the disulfide staple. Clarify how this trap differs mechanistically from YAP-derived inhibitors.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of methods description
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract mentions "dynamics simulation and energetics analysis" but does not specify the force field, simulation time, or the energetics method (e.g., MM-PBSA, FEP). This limits reproducibility.
- **Required correction** In the full manuscript, provide detailed computational methods, including software, force field, simulation length, and analysis protocols. In the abstract, a brief mention of the approach is acceptable, but the full methods must be available.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Contextualization of results
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract states that "previous efforts have all been addressed on deriving peptide inhibitors from the YAP to target TEAD4" but does not cite or compare to any specific prior work. This makes it difficult to assess the novelty of the approach.
- **Required correction** Include citations to representative YAP-derived inhibitors and briefly state how the current TEAD4-derived trap offers a distinct advantage, such as improved selectivity or different binding mode.

## Risk / unsupported claims
- The claim of "selectively capture YAP alpha1-helix" is unsupported by any selectivity data in the abstract.
- The claim of "good tumor-suppressing effect" is unsupported by quantitative cellular data or statistical analysis.
- The claim of "native-like structured conformation" is unsupported by shown circular dichroism data or any structural validation.
- The claim of forming a "three-helix bundle" is unsupported by structural evidence.
- The overall therapeutic potential is speculative and not supported by in vivo data, which is not provided.