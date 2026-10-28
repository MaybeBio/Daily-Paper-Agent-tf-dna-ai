## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors use extensive molecular dynamics simulations (approximately 13 microseconds total) to investigate how three HPV16 E6 single-site mutants (F47R, R102A, L50E) destabilize the E6/E6AP heterodimer and the E6/E6AP/p53 heterotrimer, proposing distinct atomistic mechanisms for each mutant that explain experimental observations of inhibited complex formation and p53 rescue.
- **Visible evidence base** Abstract text only; no simulation details, force field parameters, convergence metrics, or structural analyses are visible
- **Missing materials affecting confidence** Full methods, simulation setup and validation, force field choice, system construction details, free energy calculations, structural analyses (RMSD, contact maps, interaction energies), comparison with experimental structures, and all figures and tables

## Reviewer
- **Overall assessment** The abstract presents a plausible and mechanistically interesting computational study addressing a relevant biological question in HPV-driven tumorigenesis. The proposed distinct mechanisms for the three mutants are internally coherent and align with the cited experimental observations. However, the abstract alone provides insufficient technical detail to assess the robustness of the simulation results, the statistical significance of the observed differences, or the validity of the mechanistic interpretations. The claims are biologically significant but currently rest on evidence that cannot be evaluated from the supplied material.
- **Who would be interested in the results, and why** Researchers in computational biophysics and molecular dynamics, structural biologists studying protein-protein interactions, and cancer biologists focused on HPV oncogenesis and p53 pathway regulation. The work could inform therapeutic strategies targeting E6/E6AP/p53 complex formation, and the methodological approach may interest those applying long-timescale simulations to mutation-induced destabilization mechanisms.
- **Major strengths** The study addresses a clinically relevant problem with clear experimental motivation. The use of extensive simulations (approximately 13 microseconds) suggests a serious computational effort. The proposal of distinct mechanisms for each mutant is a strength, as it moves beyond a generic destabilization narrative and offers specific, testable hypotheses involving electrostatic repulsion, disrupted hydrophobic and cation-π interactions, and impaired interdomain contacts.
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
  Originality: The mechanistic differentiation among three mutants is a useful contribution, but the overall concept of mutation-induced complex destabilization is not novel. Scientific importance: Moderate to high, given the relevance to HPV oncogenesis and p53 rescue, though the direct translational impact is not established. Interdisciplinary readership: The topic bridges biophysics and cancer biology, but the abstract is written primarily for a computational audience. Technical soundness: Cannot be assessed from the abstract alone; no validation, convergence, or statistical details are provided. Readability for nonspecialists: The abstract is reasonably clear but assumes familiarity with molecular interactions and simulation terminology.
- **Recommendation posture** Currently not established from the provided evidence. The mechanistic claims are interesting and plausible, but the abstract does not provide sufficient technical detail to verify the robustness of the simulations or the validity of the interpretations. A supportive posture would require access to full methods and results.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The simulations reveal that the three E6 mutations destabilize the E6/E6AP/p53 complex through distinct mechanisms, with specific interaction changes attributed to each mutant.  
- **Evidence pointer** Abstract, Results section not provided  
- **Concern** The abstract reports qualitative mechanistic conclusions (electrostatic repulsion, disrupted hydrophobic and cation-π interactions, impaired interdomain contacts) but provides no quantitative data, such as interaction energy values, contact occupancy, or free energy differences, to support these attributions. Without such data, it is impossible to determine whether the observed differences are statistically significant or within simulation noise.  
- **Why it matters** The central claim of distinct mechanisms rests entirely on the ability to distinguish interaction changes among mutants from thermal fluctuations and sampling limitations. Qualitative descriptions without error estimates or replicate analyses do not establish the case.  
- **Resolution test** Provide quantitative interaction energy analyses with standard errors, contact probability distributions, and statistical tests comparing mutant and wild-type systems. Show that the proposed interaction changes are reproducible across independent simulation replicates and are not artifacts of insufficient sampling.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The three E6 mutations reduce the structural stabilities of the heterodimer and heterotrimer, as assessed by approximately 13 microseconds of total simulation time.  
- **Evidence pointer** Abstract, Methods section not provided  
- **Concern** The abstract does not describe the simulation protocol, including force field parameters, water model, temperature and pressure coupling, equilibration procedure, or system size. It also does not report how convergence was assessed or whether the 13 microseconds were distributed across systems and replicates. Without this information, the adequacy of sampling cannot be evaluated.  
- **Why it matters** Molecular dynamics results are highly sensitive to force field choice and simulation setup. The claim of structural destabilization requires evidence that the simulations are converged and that the observed behaviors are not artifacts of the chosen parameters or insufficient equilibration.  
- **Resolution test** Provide full simulation details in the Methods section, including force field version, water model, ion concentration, simulation length per system, number of replicates, and convergence metrics such as RMSD stabilization, block averaging, or principal component overlap.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Scientific importance  
- **Claim pointer** The study identifies intra- and intermolecular interactions crucial for complex stability, which may provide mechanistic insights into the inhibition of complex formation by the three HPV16 E6 mutations.  
- **Evidence pointer** Abstract, Discussion section not provided  
- **Concern** The abstract does not connect the simulation findings to the experimental observations beyond stating that the mutants inhibit heterotrimer formation. There is no mention of whether the simulations reproduce experimental binding affinities, structural data, or functional outcomes. The claim of mechanistic insight would be strengthened by explicit comparison with experimental structures or binding data.  
- **Why it matters** Without validation against experimental evidence, the proposed mechanisms remain speculative. The abstract implies consistency with experiments but does not demonstrate it, leaving the biological relevance of the findings unverified.  
- **Resolution test** Include a comparison of simulation results with available experimental structures of the E6/E6AP/p53 complex or binding affinity measurements for the mutants. Show that the predicted interaction changes correlate with experimentally observed effects on complex formation.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract, first sentence  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The opening sentence is dense and could be clearer for nonspecialist readers. The chain of events (E6 binds E6AP, then recruits p53, then induces degradation) is compressed into a single sentence.  
- **Required correction** Consider splitting the first sentence into two to improve clarity, for example by separating the complex formation steps from the degradation outcome.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Abstract, simulation description  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract states "totally ∼13 μs" but does not specify how this time is distributed across the heterodimer and heterotrimer systems or across the three mutants and wild-type controls.  
- **Required correction** Provide a breakdown of simulation time per system and per replicate, or state that this information is available in the Methods section.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Precision  
- **Affected element** Abstract, mechanistic descriptions  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The phrase "destabilize the structure" is used generically. It is unclear whether this refers to global unfolding, local conformational changes, or reduced binding affinity.  
- **Required correction** Specify the type of destabilization observed, such as increased RMSD, loss of specific contacts, or reduced binding free energy, to avoid ambiguity.

## Risk / unsupported claims
- The claim that the three mutations destabilize the complex through distinct mechanisms is unsupported by quantitative evidence in the abstract.
- The claim that F47R causes electrostatic repulsion between R47 and R290 is plausible but not verifiable without interaction energy data.
- The claim that R102A disrupts hydrophobic and cation-π interactions is not supported by any quantitative analysis in the abstract.
- The claim that L50E impairs interdomain and intermolecular interactions is not supported by data in the abstract.
- The overall assertion that the simulations provide mechanistic insights into inhibition of complex formation cannot be evaluated without comparison to experimental data or validation metrics.