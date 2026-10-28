## Review setup
- **Input scope** Full manuscript text (summary, introduction, results, discussion, limitations, author information)
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and generalizability of the INSRTR platform as presented in the provided text
- **Shared manuscript claim summary** The authors propose a generalizable allosteric regulation platform (INSRTR) based on inserting a short unstructured peptide into solvent-exposed loops of diverse proteins. Binding of a complementary coiled-coil peptide induces a rigid dimer, disrupting local conformation and modulating protein function. The platform is claimed to enable OFF/ON switches, small-molecule regulation, and Boolean logic in mammalian cells, demonstrated on ten diverse proteins.
- **Visible evidence base** Results sections describing principle, ON-switch variants, Boolean logic gates, and application to ten proteins; figures referenced but not provided in detail
- **Missing materials affecting confidence** Figures, supplementary figures, experimental protocols, quantitative data (activity values, replicates, statistical analyses), construct sequences, and detailed methods are not available in the provided text

## Reviewer
- **Overall assessment** The manuscript presents a conceptually appealing and potentially generalizable strategy for allosteric protein regulation. The breadth of demonstrated targets (ten proteins) is impressive and suggests practical utility. However, the provided text lacks the quantitative experimental detail necessary to evaluate the robustness, reproducibility, and mechanistic basis of the claims. Several assertions, particularly regarding mechanism and generalizability, are supported only by qualitative statements or unreferenced figures. The work is likely of interest to the synthetic biology and protein engineering communities, but the current evidence base is insufficient to fully establish the platform's broad applicability and mechanistic underpinnings.

- **Who would be interested in the results, and why** Researchers in synthetic biology, protein engineering, and cell engineering would find this work relevant. The potential to regulate diverse protein classes with a simple insertion strategy, coupled with rapid response and logic gate construction, could enable new approaches in therapeutic cell engineering (e.g., CAR T-cell control), biosensing, and basic studies of protein function. The claim of high success rate across ten proteins is a key attractor for those seeking generalizable regulation tools.

- **Major strengths** 1) The conceptual simplicity of the INSRTR approach, using a single inserted peptide and coiled-coil dimerization, is elegant and potentially transferable. 2) The demonstration across ten proteins spanning enzymes, signaling mediators, DNA binders, fluorescent proteins, and antibodies is a significant breadth claim. 3) The inclusion of ON-switch variants and Boolean logic gates extends the platform's utility beyond simple OFF switches. 4) The use of designed orthogonal coiled-coil pairs with tunable affinities provides a rational basis for response tuning.

- **Major Concerns** 
  - **R1-M1** (Major, Blocking: Yes, Axis: Evidence sufficiency)
  - **R1-M2** (Major, Blocking: Yes, Axis: Mechanistic clarity)
  - **R1-M3** (Major, Blocking: No, Axis: Generalizability)
  - **R1-M4** (Major, Blocking: No, Axis: Reproducibility)

- **Minor Comments** 
  - **R1-m1** (Minor, Axis: Clarity)
  - **R1-m2** (Minor, Axis: Completeness)
  - **R1-m3** (Minor, Axis: Consistency)

- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2

- **Assessment against Nature-style criteria** 
  - **Originality** High. The INSRTR concept, while building on prior domain-insertion approaches, offers a distinct and potentially simpler strategy using short unstructured peptides. The breadth of targets is a novel contribution.
  - **Scientific importance** Potentially high. If the generalizability claim holds, this could become a widely used tool for protein regulation. The logic gate extension adds functional complexity.
  - **Interdisciplinary readership** Moderate to high. The work bridges protein biophysics, synthetic biology, and cell engineering, appealing to a broad audience.
  - **Technical soundness** Currently not fully assessable. The text lacks quantitative data, detailed protocols, and statistical analyses. Mechanistic claims are supported by a single unreferenced simulation and indirect inferences.
  - **Readability for nonspecialists** Good. The text is clearly written and the conceptual framework is accessible. However, the lack of figure details limits comprehension of specific results.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the breadth of demonstration is notable, but the current evidence base is insufficient to establish the platform's generalizability and mechanism. Substantial additional data and methodological detail are required.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that INSRTR is a "generally applicable" regulation platform, demonstrated with "perfect success" on ten proteins, with "up to 90% inhibition" and "up to 30-fold repression."
- **Evidence pointer** Results sections "The principle of inserted peptide structure allosteric regulation (INSRTR)" and "INSRTR regulation of diverse protein types and functions in an OFF or ON format"; figures referenced but not provided
- **Concern** The manuscript text provides only qualitative descriptions of results. No quantitative data (e.g., activity values, fold changes, response curves, replicate numbers, error bars, statistical tests) are presented for any of the ten proteins. The claim of "perfect success" is not supported by any visible numerical evidence. The referenced figures (Figure 5, Figure S2-S5) are not available for review, making it impossible to verify the magnitude and consistency of the reported effects.
- **Why it matters** The central claim of generalizability and high success rate rests entirely on the quantitative demonstration across diverse proteins. Without these data, the platform's practical utility cannot be assessed, and the claim of "perfect success" is unverifiable.
- **Resolution test** Provide a comprehensive dataset for all ten proteins, including dose-response curves, activity measurements in the presence and absence of regulatory peptides, replicate numbers, and statistical analyses. Include a summary table of insertion sites, activity retention, and fold regulation for each protein.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic clarity
- **Claim pointer** The authors state that "the formation of a CC dimer in the loop affected the conformation of the loop, while the rest of the host protein, including the geometry and dynamics of the active site residues, remained essentially unperturbed," and that inhibition is "likely a result of a subtle perturbation of the structure or/and dynamics of the active site."
- **Evidence pointer** Results section "The principle of inserted peptide structure allosteric regulation (INSRTR)"; molecular dynamics simulation mentioned but not shown
- **Concern** The proposed mechanism of allosteric inhibition is supported only by a single molecular dynamics simulation that is not shown or described in detail. No experimental validation (e.g., structural studies, mutagenesis, biophysical characterization) is provided to confirm that the coiled-coil formation induces the proposed local conformational change without global perturbation. The distinction between local and global effects is critical for the claimed mechanism.
- **Why it matters** Understanding the mechanism is essential for rational application of the platform to new proteins. If the mechanism is not as proposed, the design rules for selecting insertion sites may be incorrect, limiting the platform's generalizability.
- **Resolution test** Provide the molecular dynamics simulation data and analysis, or experimental structural/biophysical evidence (e.g., HDX-MS, FRET, circular dichroism) demonstrating that coiled-coil formation induces local conformational changes at the insertion site without global unfolding. Include mutagenesis studies to test the role of specific residues in the allosteric relay.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors claim that INSRTR can regulate "a wide range of proteins" and that "insertion positions were selected based on several rational considerations" with a success rate "comfortably above 30%."
- **Evidence pointer** Results section "INSRTR regulation of diverse protein types and functions in an OFF or ON format"; Discussion
- **Concern** While ten proteins are demonstrated, the text does not report the number of failed insertion attempts or the criteria for selecting candidate sites. The claim of a "success rate comfortably above 30%" is not contextualized with the total number of attempts. Without this information, it is unclear whether the success rate is genuinely high or whether the reported proteins represent a selected subset.
- **Why it matters** The generalizability claim depends on the success rate across attempted targets. If many failures occurred, the platform may be less broadly applicable than suggested.
- **Resolution test** Report the total number of proteins and insertion sites tested, including failures, and provide a detailed description of the selection criteria and the relationship between insertion site properties and success.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** The authors describe the construction of ON-switch variants, small-molecule regulation via split protease, and Boolean logic gates.
- **Evidence pointer** Results sections "Designed inverted INSRTR (ON switch) can be regulated by various trigger signals" and "Construction of Boolean protein logic gates based on intramolecular interacting segments"; Figure 4
- **Concern** The text describes these extensions but provides no detailed protocols, construct designs, or quantitative characterization of the logic gate responses (e.g., truth tables, response times, signal-to-noise ratios). The reproducibility of these complex constructs is not assessable from the provided information.
- **Why it matters** The logic gate and small-molecule regulation features are significant extensions of the platform. Without detailed methods and data, other groups cannot reproduce or build upon these results.
- **Resolution test** Provide full construct schematics, sequences, and detailed protocols for the ON-switch and logic gate variants. Include quantitative characterization of all logic gate outputs for all input combinations, with appropriate controls and replicates.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction, paragraph 2
- **Evidence pointer** Location not provided
- **Issue** The sentence "Typically, several permissible insertion sites were identified with a high success rate within each protein, which retained the function but could be controlled in mammalian cells by adding a regulatory peptide provided through different means" is redundant with the preceding sentence and could be streamlined for clarity.
- **Required correction** Revise to avoid repetition and clarify the distinction between "several permissible insertion sites" and "high success rate."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "The principle of inserted peptide structure allosteric regulation (INSRTR)"
- **Evidence pointer** Location not provided
- **Issue** The text mentions "Molecular dynamics simulation of the luciferase model (Figure 1B)" but states "Figure not shown." This is confusing and should be clarified.
- **Required correction** Either include the simulation figure or remove the reference to it and describe the simulation results in the text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Discussion and Limitations
- **Evidence pointer** Location not provided
- **Issue** The Discussion states that "the success rate was comfortably above 30% for most proteins," while the Limitations section notes that "some hub proteins... might be difficult to engineer." These statements are not contradictory but could be better integrated to provide a more nuanced view of the platform's limitations.
- **Required correction** Consider discussing the potential limitations of the approach for specific protein classes in the Discussion to provide a balanced perspective.

## Risk / unsupported claims
- The claim of "perfect success" on ten proteins is unsupported without quantitative data.
- The mechanistic claim that coiled-coil formation induces only local conformational changes is unsupported without the simulation data or experimental validation.
- The claim of "generally applicable" regulation is not fully established given the lack of failure data and the limited number of protein classes tested.
- The "up to 30-fold repression" and "up to 90% inhibition" values are not contextualized with specific proteins or conditions.
- The Boolean logic gate functionality is described but not quantitatively demonstrated in the provided text.
- The claim of "low immunogenicity" is speculative and not supported by any experimental evidence.