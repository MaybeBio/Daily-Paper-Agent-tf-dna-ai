## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results and discussion, conclusions, computational methodology, author contributions, conflicts of interest, acknowledgements, footnotes)
- **Assessment boundary** Scientific content, methodological soundness, claims versus evidence, and presentation quality as presented in the supplied text. No external validation or replication performed.
- **Shared manuscript claim summary** The authors use microsecond-scale all-atom molecular dynamics simulations and protein-DNA docking to propose that SARS-CoV-2 ORF8 binds double-stranded DNA via a histone H3-like ARKS motif, forming stable major- and minor-groove complexes, and that post-translational modifications (acetylation, methylation) of lysine 36 do not destabilize these interactions, supporting a role for ORF8 in perturbing chromatin compaction and epigenetic regulation in infected cells.
- **Visible evidence base** Abstract, full text of Introduction, Results and Discussion, Conclusions, Computational Methodology, Author Contributions, Conflicts of Interest, Acknowledgements, Footnotes. No figures, tables, or Supplementary Information files were provided for inspection.
- **Missing materials affecting confidence** All figures (Figures 1–7), all Supplementary Information (time series, RMSD data, binding free energy tables), and any numerical data tables. Without these, quantitative claims about distances, free energies, and trajectory stability cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and potentially important question, namely the molecular basis of SARS-CoV-2 ORF8-mediated epigenetic perturbation. The hypothesis that ORF8 acts as a histone mimic through its ARKS motif is plausible and consistent with prior experimental observations. However, the evidence presented in the text is largely qualitative, and the absence of the actual figures and numerical data prevents verification of the central claims. The computational methodology is described in reasonable detail, but several choices (e.g., force field corrections, docking protocol, free energy method) require justification and sensitivity analysis. The manuscript would benefit from clearer presentation of quantitative results and a more critical discussion of limitations. As it stands, the case is suggestive but not fully established from the provided material.
- **Who would be interested in the results, and why** Structural biologists, computational biophysicists, virologists studying SARS-CoV-2 host interactions, and researchers interested in epigenetic regulation and histone mimicry. The work offers a first atomistic model of ORF8-DNA interaction, which could inform future experimental studies and antiviral design targeting ORF8.
- **Major strengths** The study addresses a novel and biologically significant question. The use of microsecond-scale all-atom MD simulations is appropriate for studying protein-DNA interactions. The consideration of post-translational modifications adds biological relevance. The authors acknowledge limitations and propose future work, which is commendable.
- **Major Concerns** The central claims rest on data that are not visible in the provided material. The distinction between the two docking poses and their relative stabilities is described but not quantitatively supported. The binding free energy values are stated without error analysis or comparison to experimental benchmarks. The biological interpretation, particularly the claim that PTMs on ORF8 do not lead to chromatin decompaction, is speculative and not directly tested. The authors do not address whether the simulated DNA sequence is representative or whether the observed interactions are sequence-specific.
- **Minor Comments** The abstract contains a typo ("immonuglobulin-like"). The introduction is somewhat lengthy and could be streamlined. The phrase "knocking-off of the interaction" is awkward. The authors should define "μ-sheets" (likely β-sheets). The conclusion that ORF8 "may accumulate PTMs and divert their action" is presented without direct simulation of enzyme interactions, which the authors acknowledge but could be more clearly framed as a hypothesis.
- **Technical failings that need to be addressed before the case is established** The absence of figures and numerical data is a critical failing for assessment. The binding free energy calculations using MM/GBSA are known to be sensitive to setup and should be validated or compared with more rigorous methods. The authors do not report convergence criteria for the MD simulations or block averaging for free energy estimates. The use of CMAP corrections for a disordered region is reasonable but should be justified with reference to validation. The docking protocol with HADDOCK should be described with scoring details.
- **Assessment against Nature-style criteria** Originality: High, as this is the first atomistic model of ORF8-DNA interaction. Scientific importance: Potentially high, given the relevance to COVID-19 pathogenesis and epigenetic regulation. Interdisciplinary readership: Moderate, as the work is primarily computational and would appeal to structural biology and virology communities, but may be less accessible to general readers. Technical soundness: Not fully assessable without the data; the methodology is plausible but lacks validation and sensitivity analysis. Readability for nonspecialists: The text is generally clear but includes technical jargon and would benefit from a schematic figure explaining the proposed mechanism.
- **Recommendation posture** Supportive if technical concerns are resolved and the missing data are provided for verification. Currently not established from the provided evidence.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence availability
- **Claim pointer** The authors claim that ORF8 forms stable complexes with DNA via major- and minor-groove interactions, with specific residue-level contacts and binding free energies of -45.6±8.2 kcal/mol and -28.4±9.6 kcal/mol.
- **Evidence pointer** Figures 3, 4, 5; Supplementary Information (time series, binding free energies); location not provided
- **Concern** The central quantitative claims cannot be verified because the figures and supplementary data are not included in the provided material. The binding free energy values are stated without showing the underlying distributions, error estimates, or convergence analysis. The representative structures and distance distributions are referenced but not visible.
- **Why it matters** Without the actual data, the reader cannot assess whether the simulations are converged, whether the interactions are indeed stable, or whether the free energy differences are meaningful. This is essential for establishing the validity of the proposed model.
- **Resolution test** Provide all figures and supplementary data, including time series for distances, RMSD plots, and free energy values with standard deviations and convergence checks. Show representative structures with clear labeling of the ARKS motif and DNA contacts.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validation
- **Claim pointer** The authors use MM/GBSA to estimate binding free energies and report values that differ by ~17 kcal/mol between the two binding modes.
- **Evidence pointer** Computational Methodology, "To estimate the binding free energies..."; location not provided
- **Concern** MM/GBSA is known to be highly sensitive to the choice of internal dielectric constant, entropy contributions, and the conformational ensemble used. The authors do not report any validation against experimental data or alternative methods (e.g., thermodynamic integration, free energy perturbation). The large difference between the two binding modes is not discussed in terms of statistical significance.
- **Why it matters** The relative stability of the two binding modes is a key claim. If the free energy difference is within the error of the method, the conclusion that the major-groove mode is more favorable is not supported.
- **Resolution test** Provide a sensitivity analysis of the MM/GBSA results to key parameters (e.g., dielectric constant, entropy). Compare with a more rigorous method for at least one system. Report standard errors and discuss whether the difference between binding modes is statistically significant.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Biological interpretation
- **Claim pointer** The authors state that PTMs on ORF8 do not destabilize the DNA interaction and that this "will not result in chromatin decompaction," leading to a hypothesis that ORF8 diverts PTMs from histones.
- **Evidence pointer** Results and Discussion, "Even upon the presence of PTMS..."; location not provided
- **Concern** The simulations only test the effect of PTMs on the ORF8-DNA interaction in isolation. The claim that this will not result in chromatin decompaction is an extrapolation that requires consideration of chromatin structure, competing histone interactions, and the activity of modifying enzymes. The authors acknowledge this but do not frame it as a hypothesis rather than a conclusion.
- **Why it matters** The biological significance of the work depends on this interpretation. Overstating the implications could mislead readers.
- **Resolution test** Clearly label this as a hypothesis and discuss alternative scenarios. If possible, perform additional simulations or cite experimental evidence that supports or refutes the claim.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Sequence specificity
- **Claim pointer** The authors claim that ORF8 binds DNA via the ARKS motif, but they do not test whether this interaction is sequence-specific.
- **Evidence pointer** Results and Discussion, "the ARKS sequence..."; Computational Methodology, "A 21 base pairs model B-DNA duplex..."; location not provided
- **Concern** The simulations use a single DNA sequence. It is unclear whether the observed interactions depend on the specific sequence or are general. The authors do not discuss whether ORF8 shows sequence preference, which would be relevant for its biological function.
- **Why it matters** If ORF8 binds DNA non-specifically, its effect on chromatin compaction would be global. If it binds specific sequences, the effect could be targeted. This distinction is important for understanding the mechanism.
- **Resolution test** Perform simulations with multiple DNA sequences of varying GC content and discuss any sequence-dependent differences. Alternatively, cite experimental data on ORF8 DNA-binding specificity.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, "immonuglobulin-like"
- **Issue** Typographical error.
- **Required correction** Change to "immunoglobulin-like".

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Language
- **Affected element** Results and Discussion
- **Evidence pointer** Results and Discussion, "knocking-off of the interaction"
- **Issue** Awkward phrasing.
- **Required correction** Rephrase to "disruption of the interaction" or "loss of the interaction."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Results and Discussion
- **Evidence pointer** Results and Discussion, "μ-sheets"
- **Issue** The symbol "μ" is likely a typo for "β".
- **Required correction** Change to "β-sheets".

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Conclusions
- **Evidence pointer** Conclusions, "To the best of our knowledge, our study represents the first modelling of the epigenetic effects induced by a viral protein on the host cells."
- **Issue** This claim is strong and may be difficult to verify. It would be safer to say "To the best of our knowledge, this is the first atomistic simulation study of ORF8-DNA interactions."
- **Required correction** Soften the claim to avoid overstatement.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Computational Methodology
- **Evidence pointer** Computational Methodology, "The docking to the dimer gave rise to a rather unstable complex... and is therefore further discarded."
- **Issue** The authors discard the dimer results but do not provide details on the instability. This is relevant because ORF8 is a dimer in solution.
- **Required correction** Provide a brief description of the instability (e.g., RMSD values, dissociation events) or cite a reference for the dimer being inactive.

## Risk / unsupported claims
- The claim that ORF8 forms stable complexes with DNA via major- and minor-groove interactions is unsupported without the figures and time series data.
- The binding free energy values (-45.6±8.2 and -28.4±9.6 kcal/mol) are unverifiable without the underlying data and error analysis.
- The claim that PTMs on ORF8 do not lead to chromatin decompaction is an unsupported extrapolation from the simulation data.
- The claim that this is the "first modelling of the epigenetic effects induced by a viral protein on the host cells" is unverifiable and likely overstated.
- The biological significance of the work, particularly the competition with histone H3 for PTM enzymes, is speculative and not directly tested.