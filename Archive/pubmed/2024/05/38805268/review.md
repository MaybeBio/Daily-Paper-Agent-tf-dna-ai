## Review setup
- **Input scope** Full manuscript text (main text, methods summary, data availability statement) as provided by the user. Supplementary Information referenced but not provided.
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and internal consistency based solely on the supplied text. Structural biology and MD simulation details are assessed at the level of description provided.
- **Shared manuscript claim summary** The authors propose that transient, sequence-dependent conformational dynamics of both the RelA NF-κB dimer and its target DNA, rather than direct base-specific contacts to the central base pair, determine the differential binding affinity of RelA for A/T-centric versus G/C-centric κB sites. This is supported by binding assays, crystal structures of free and bound DNA, and microsecond-scale MD simulations.
- **Visible evidence base** Main text descriptions of: luciferase reporter assays (Fig. 1B), EMSA (Fig. 1C, D; SI Appendix Fig. S1D, E), BLI (Fig. 1E; SI Appendix Table S1a, b), crystal structures of four RelA:DNA complexes (Fig. 2; PDB 9BDU-9BDX) and four free DNAs (Fig. 3; PDB 9BDY-9BE1), MD simulations of free and bound DNA (Fig. 4, 6; SI Appendix Fig. S4), inosine substitution experiments (Fig. 5A, B), and mutant binding assays (Fig. 5C). Methods are summarized; full details in SI Appendix.
- **Missing materials affecting confidence** The entire SI Appendix (including all supplementary figures, tables, and detailed methods) is not provided. This includes: SI Appendix Fig. S1-S6, Tables S1a-c, S2a-b, S3, detailed MD simulation protocols, BLI fitting procedures, EMSA quantification methods, and crystallographic data collection/refinement statistics. Without these, quantitative rigor of binding measurements, simulation convergence, and structural validation cannot be independently assessed.

## Reviewer

- **Overall assessment** This manuscript addresses a fundamental question in gene regulation: how a transcription factor achieves sequence-specific binding affinity differences without direct contact to the discriminating base. The combination of quantitative binding, high-resolution crystallography, and long-timescale MD simulations is ambitious and appropriate. The central hypothesis, that transient interactions and conformational dynamics rather than static contacts govern affinity, is plausible and potentially significant. However, the evidence as presented in the main text is largely qualitative or descriptive. The key claims regarding dynamic differences between A/T- and G/C-κB complexes rest on MD simulations whose validation, convergence, and statistical treatment are not described in the visible text. The inosine and mutant experiments are suggestive but limited in scope. The manuscript would be strengthened by clearer quantitative links between observed dynamic states and measured affinities, and by explicit statistical comparisons across simulation replicates.
- **Who would be interested in the results, and why** Structural biologists studying protein-DNA recognition, computational biochemists interested in allosteric communication and conformational ensembles, and the NF-κB signaling community. The work also speaks to the broader question of how transcription factor families achieve target specificity, which is relevant to gene regulation and disease mechanisms.
- **Major strengths** The study combines multiple orthogonal approaches (biochemistry, structural biology, computation) to address a subtle question. The crystal structures of all four κB sites in both free and bound states are a valuable resource. The use of long (6 µs) MD simulations on a 75 kDa complex is technically demanding and represents a significant computational investment. The identification of specific residues (R187, R124) and their dynamic coupling is mechanistically interesting. The inosine substitution experiments are a clever approach to dissect major versus minor groove contributions.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of MD simulation evidence
- **Claim pointer** The authors claim that MD simulations reveal "transient interactions" and "sequence-dependent shift in distribution of protein side-chain conformers" that explain differential binding affinity (Discussion, Results sections on MD simulations).
- **Evidence pointer** Results section "Microsecond MD Simulations..."; Fig. 4; SI Appendix Fig. S4 (not provided)
- **Concern** The central mechanistic conclusion rests on MD simulations, but the visible text provides no information on simulation convergence, replicate variability, force field validation, or statistical significance of the observed conformational differences. The claim that R187-I "predominantly (60.1%)" flips to bind phosphate in G-κB versus "14.5%" direct base contact in A-κB requires error bars or replicate-level data to establish that these are robust differences rather than sampling artifacts. Similarly, the population differences for R124 states (27.3% vs 6.5%) need statistical support. Without these, the dynamic mechanism is not established.
- **Why it matters** The entire mechanistic narrative depends on the reliability of the MD simulations. If the observed state populations are not statistically distinguishable or are sensitive to force field parameters, the conclusion that dynamics, rather than static structure, dictate affinity is unsupported.
- **Resolution test** Provide per-replicate state populations with standard deviations or confidence intervals, demonstrate convergence (e.g., block averaging, multiple independent seeds), and show that key conclusions are robust to force field choice or at least discuss known limitations. A quantitative comparison of simulated and experimentally measured affinities or kinetics would strengthen the link.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support for affinity differences
- **Claim pointer** The authors state that RelA binds A- and T-centric sites with "~10-fold" higher affinity than G- and C-centric sites, and that inosine substitutions reduce affinity ~5-fold (A to I) or increase ~1.3-fold (G to I).
- **Evidence pointer** Results section "Dimers of RelA Bind..."; Fig. 1B-E; Fig. 5B; SI Appendix Table S1a, b; SI Appendix Fig. S1D, E (not provided)
- **Concern** The main text reports KD values for A/T versus G/C sites (25 nM vs 300 nM) and EMSA-based estimates, but the number of replicates, standard errors, and statistical tests are not reported. The inosine data (5-fold decrease, 1.3-fold increase) are presented without error estimates or significance testing. The claim that a 1.3-fold change is meaningful requires statistical support. Without these, the quantitative basis for the entire study is unclear.
- **Why it matters** The affinity differences are the phenotype that the structural and computational work aims to explain. If the differences are not rigorously quantified, the mechanistic conclusions lack a solid foundation.
- **Resolution test** Report mean ± SD or SEM for all KD values with n ≥ 3 independent experiments, and perform appropriate statistical tests (e.g., t-test or ANOVA) comparing A/T versus G/C and wild-type versus inosine-substituted DNA. Show that the 1.3-fold increase for I:C is statistically significant.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the mechanism
- **Claim pointer** The authors generalize from RelA homodimer to NF-κB family members, suggesting that "a minor difference in interfacial residues... may have provided a significantly enhanced promiscuity to cRel."
- **Evidence pointer** Results section "Differential Selectivity of κB DNAs by RelA and cRel"; Fig. 7
- **Concern** The comparison between RelA and cRel is based on reanalysis of published microarray data (ref 5) and a single chimeric mutant. The text states that the RelA mutant "behaved closer to cRel" but provides no quantitative metric for this claim. The conclusion that cRel's promiscuity arises specifically from the K124 residue is speculative without direct binding measurements on cRel with the same κB site variants used for RelA.
- **Why it matters** The broader significance of the work, particularly its relevance to disease (cancer, autoimmunity), depends on the claim that this mechanism distinguishes NF-κB family members. If the cRel comparison is not rigorously established, the translational implications are weakened.
- **Resolution test** Perform direct binding assays (e.g., BLI or EMSA) comparing cRel and RelA on the same set of A/T- and G/C-centric κB sites, and test the converse mutation (K124R in cRel) to establish causality. Alternatively, temper the claims to be explicitly hypothesis-generating.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Structural interpretation of B-factors
- **Claim pointer** The authors use B-factor analysis to infer "distinctive side chain dynamics" and "increased flexibility around the periphery" of the DNA in the complexes.
- **Evidence pointer** Results section "Crystal Structures Reveal Nearly Identical Binding Modes..."; SI Appendix Table S2b (not provided)
- **Concern** B-factors are influenced by crystal packing, lattice contacts, and refinement procedures, and comparing B-factors between different crystal forms (four different complexes) is fraught. The claim that B-factor differences reflect intrinsic dynamic differences relevant to solution behavior requires validation. The text does not mention whether the four complexes crystallized in the same space group or whether B-factors were normalized or scaled.
- **Why it matters** The B-factor analysis is used to support the dynamic mechanism. If the B-factor differences are artifacts of crystal packing, this line of evidence is invalid.
- **Resolution test** Show that the four complexes are isomorphous or that B-factor differences persist after normalization. Ideally, corroborate with solution techniques (e.g., NMR relaxation, HDX-MS) or with the MD simulations in a quantitative manner.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Functional relevance of weak κB sites
- **Claim pointer** The authors suggest that weak κB sites "may have evolved" to assist recruitment or recruit other TFs, and that this work "set the groundwork" for understanding their role.
- **Evidence pointer** Discussion section "Transcriptional Activity of Diverse Natural κB Sites"
- **Concern** This section is largely speculative. The reporter assay shows that G/C-centric sites drive lower transcription, but no experiments address the proposed functions of weak sites (e.g., cooperative binding, TF tethering). The statement that "a slight increase in their binding affinity did not enhance the reporter activity significantly" is presented without data.
- **Why it matters** The Discussion overreaches beyond the data. While speculation is acceptable in a Discussion, it should be clearly framed as such and not presented as a finding.
- **Resolution test** Either remove or clearly label speculative statements, or add experiments testing the proposed functions (e.g., chromatin context, TF co-binding assays).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure references
- **Affected element** Fig. 1D and SI Appendix Fig. S1D
- **Evidence pointer** Results section "Dimers of RelA Bind..."
- **Issue** The text states "We also qualitatively assessed the binding affinity of purified full-length RelA (RelAFL) homodimer and p50:RelA heterodimer to all four κB DNAs using EMSA (Fig. 1D and SI Appendix, Fig. S1D)." It is unclear whether Fig. 1D shows both proteins or only one, and what "qualitatively" means in terms of data presentation.
- **Required correction** Clarify which protein is shown in which figure panel, and specify whether the EMSA data are quantified or shown as representative gels.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Fig. 1B luciferase assay
- **Evidence pointer** Results section "Dimers of RelA Bind..."
- **Issue** The luciferase assay is described as showing "significantly higher" transcription for A/T sites, but no statistical details are given.
- **Required correction** Add statistical test information and error bars to the figure legend or text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** "A-centric" vs "A-κB" naming
- **Evidence pointer** Throughout
- **Issue** The terms "A-κB", "T-κB", "G-κB", "C-κB" are used to describe DNA sites, but "A-centric" and "G-centric" are also used. This is potentially confusing.
- **Required correction** Define the naming convention early and use it consistently.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Methods detail for MD simulations
- **Affected element** MD simulation methods
- **Evidence pointer** Methods section "MD Simulations"
- **Issue** The methods state that "five independent 2 µs simulations" were performed for free DNAs and "six independent 6 µs simulations" for complexes, but no details on temperature/pressure coupling, equilibration, or analysis tools are given in the main text.
- **Required correction** Either provide these details in the main text or explicitly refer to the SI Appendix for full protocols.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability for MD trajectories
- **Affected element** Data availability statement
- **Evidence pointer** Data, Materials, and Software Availability
- **Issue** The statement covers crystallographic data but does not mention availability of MD trajectories or analysis scripts.
- **Required correction** Consider depositing MD trajectories or providing a statement on availability upon request.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Figure quality for B-factor analysis
- **Affected element** Fig. 2 and SI Appendix Table S2b
- **Evidence pointer** Results section "Crystal Structures Reveal Nearly Identical Binding Modes..."
- **Issue** The B-factor analysis is described in text but no figure showing B-factor mapped onto the structures is referenced in the main text.
- **Required correction** Consider adding a figure panel showing B-factor distribution on the structures, or clarify that this is in the SI.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Reference to "in preparation" work
- **Affected element** Discussion section
- **Evidence pointer** Discussion "Transcriptional Activity of Diverse Natural κB Sites"
- **Issue** The text states "We recently observed an essential role of these weak sites in transcription in vivo (in preparation)." This is not citable evidence.
- **Required correction** Either remove this statement or replace with published or preprint references.

## Risk / unsupported claims
- The claim that MD simulations reveal a causal link between specific conformational states (e.g., R187 phosphate binding) and reduced affinity is not quantitatively supported in the visible text.
- The generalization of the mechanism to cRel and its disease relevance is speculative and not directly tested.
- The statement that "a slight increase in their binding affinity did not enhance the reporter activity significantly" is presented without data.
- The functional role of weak κB sites in vivo is asserted based on unpublished work.
- The B-factor analysis as evidence for differential dynamics is not validated against crystal packing effects.
- The claim that the central base pair "makes no direct contact with the protein" is stated as fact, but the text also describes water-mediated contacts involving K218 and the central base pair, which is a potential inconsistency.