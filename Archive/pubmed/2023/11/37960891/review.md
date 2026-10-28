## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no figures, tables, methods, or supporting data were provided
- **Shared manuscript claim summary** The authors use all-atom molecular dynamics and umbrella sampling simulations to study the DNA groove preference of a short protamine-like cationic peptide in non-phosphorylated and phosphorylated states. They report that the non-phosphorylated peptide prefers the minor groove, while phosphorylation reduces binding affinity, deforms the minor groove, and eliminates this preference. They extrapolate that phosphorylated protamines would prefer the major groove during spermatogenesis.
- **Visible evidence base** Abstract text only; no quantitative results, simulation details, or structural analyses are visible
- **Missing materials affecting confidence** Full manuscript, methods section, simulation parameters, force field details, free energy profiles, structural analysis figures, and any statistical validation

## Reviewer
- **Overall assessment** The abstract presents a plausible and potentially interesting computational study on the effect of phosphorylation on DNA groove preference of a protamine-like peptide. However, the evidence base is limited to a summary of findings without quantitative support. The central claims, particularly the groove preference shift and the extrapolation to biological context, cannot be rigorously evaluated from the supplied material. The study addresses a relevant question in chromatin biology, but the current presentation does not establish the case with sufficient detail.
- **Who would be interested in the results, and why** Researchers in computational biophysics, DNA-protein interactions, and chromatin biology would be interested. The work could inform understanding of protamine function in sperm chromatin compaction and the role of phosphorylation in modulating DNA binding, which has implications for reproductive biology and potential therapeutic applications.
- **Major strengths** The study addresses a specific and unresolved question regarding DNA groove preference of protamines. The use of all-atom molecular dynamics and umbrella sampling is appropriate for investigating binding free energies and structural changes. The comparison between phosphorylated and non-phosphorylated states provides a clear mechanistic hypothesis.
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
  - Originality: The question of groove preference in protamines is not new, but the specific focus on phosphorylation-induced shifts may offer a novel angle. However, the abstract does not clearly differentiate this work from prior studies.  
  - Scientific importance: The biological implications for spermatogenesis are significant, but the connection is speculative and not directly tested.  
  - Interdisciplinary readership: The topic bridges biophysics and reproductive biology, but the abstract is written in a way that may be accessible to specialists only.  
  - Technical soundness: Cannot be assessed from the abstract alone; simulation methodology and validation are not visible.  
  - Readability for nonspecialists: The abstract is concise but uses jargon without sufficient context, limiting accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially valuable study, but the lack of quantitative data and methodological detail prevents a supportive recommendation.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The claim that the non-phosphorylated peptide prefers the minor groove over the major groove is presented as a definitive finding.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract states a clear preference for the minor groove based on "various thermodynamic and structural analyses," but no quantitative data, such as free energy differences, binding constants, or statistical measures, are provided. Without these, the strength and significance of the preference cannot be evaluated.  
- **Why it matters** The central conclusion of the study rests on this preference. If the evidence is weak or the difference is within error, the entire narrative collapses.  
- **Resolution test** Provide quantitative free energy differences with error estimates and statistical significance tests for the minor versus major groove binding.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Claim extrapolation  
- **Claim pointer** The authors extrapolate that "structurally disordered phosphorylated protamines would prefer major grooves to enter into DNA during spermatogenesis."  
- **Evidence pointer** Abstract, location not provided  
- **Concern** This statement extends the simulation results on a short peptide to full-length protamines in a complex biological process. The abstract does not provide evidence that the peptide model captures the behavior of full-length protamines, nor does it address the physiological relevance of the simulation conditions.  
- **Why it matters** The biological significance of the study hinges on this extrapolation. If the model system is not representative, the conclusion may be misleading.  
- **Resolution test** Discuss the limitations of the peptide model and provide evidence or arguments for its relevance to full-length protamines. If possible, include simulations or experimental data on full-length protamines.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical validation  
- **Claim pointer** The claim that phosphorylation "brings a serious deformation of the minor groove" is presented as a key structural finding.  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract does not describe how deformation is quantified or whether it is statistically significant. No structural metrics, such as groove width, depth, or hydrogen bonding patterns, are provided.  
- **Why it matters** The deformation is used to explain the loss of minor-groove preference. Without proper quantification, this claim is unsupported.  
- **Resolution test** Provide quantitative measures of groove geometry before and after phosphorylation, with appropriate statistical analysis.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract wording  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The phrase "serious deformation" is vague and subjective.  
- **Required correction** Replace with a quantitative description, such as "a significant change in groove width of X angstroms" or similar.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Context  
- **Affected element** Background  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract does not mention prior work on protamine-DNA interactions, making it difficult to assess the novelty of the findings.  
- **Required correction** Add a brief statement on previous studies and how this work advances the field.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Methodology transparency  
- **Affected element** Simulation details  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract does not specify the length of the simulations, the force field used, or the system setup, which are critical for reproducibility.  
- **Required correction** Include key simulation parameters in the abstract or refer to the methods section for details.

## Risk / unsupported claims
- The claim of minor groove preference in the non-phosphorylated state is unsupported without quantitative free energy data.
- The claim of "serious deformation" of the minor groove is unsupported without structural metrics.
- The extrapolation to full-length protamines and spermatogenesis is unsupported and speculative.
- The overall biological relevance is asserted but not demonstrated.