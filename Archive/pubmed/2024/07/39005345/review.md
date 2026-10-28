## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv)
- **Assessment boundary** Scientific content, methodology, data interpretation, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors propose that the conserved region (CR, residues 319–341) of the TDP-43 C-terminal domain (CTD) forms dynamic, helix-mediated higher-order oligomers (tetramers) that are functionally important for phase separation and nuclear retention, and that these assemblies are stabilized by a methionine-rich core with contributions from W334 and L330.
- **Visible evidence base** NMR spectroscopy (chemical shifts, CSPs, relaxation, NOEs, sPRE), SV-AUC, alanine-scanning mutagenesis with phase separation assays, cellular nuclear-cytoplasmic fractionation, AlphaFold2-Multimer predictions, and all-atom MD simulations
- **Missing materials affecting confidence** Figures and supplementary figures referenced but not provided; detailed experimental parameters for some assays (e.g., exact csat measurement protocols, statistical replicates) not fully described; MD simulation convergence and force field validation details not fully provided

## Reviewer

- **Overall assessment** This manuscript addresses an important and timely question regarding the structural basis of TDP-43 CTD multimerization, a process central to both normal function and disease pathology. The integrative approach combining experimental and computational methods is commendable and appropriate for studying a dynamic, partially disordered system. The authors provide compelling evidence that the CR is α-helical under physiological conditions, that specific residues modulate phase separation and nuclear retention, and that tetrameric assemblies are plausible structural models. However, several concerns regarding the strength of the structural claims, the interpretation of cellular data, and the generalizability of the MD-based models need to be addressed before the case is fully established.

- **Who would be interested in the results, and why** Researchers in the fields of neurodegeneration (ALS, FTD, LATE), phase separation and biomolecular condensates, intrinsically disordered proteins, and structural biology of dynamic protein assemblies. The work provides a structural framework for understanding how disease-associated mutations in TDP-43 might perturb function, which is of broad interest to the neuroscience and protein biophysics communities.

- **Major strengths** The study directly addresses a controversy regarding the native conformation of the TDP-43 CR under physiological conditions, using rigorous NMR methods. The combination of experimental mutagenesis, biophysical characterization, and computational modeling is well-suited to the dynamic nature of the system. The identification of specific residues (W334, L330, methionines) as key drivers of assembly provides testable hypotheses. The correlation between in vitro phase separation data, NMR-derived contacts, and cellular localization data strengthens the functional relevance of the findings.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural model validity
- **Claim pointer** The manuscript claims to establish "atomic structural models of helical oligomerization of TDP-43 CR" and specifically that "dynamic, oligomeric assemblies of TDP-43 that are stabilized by a methionine-rich core" represent the native state.
- **Evidence pointer** Results section "AAMD simulations reveal the tetrameric helical assembly of TDP-43 CTD"; Figures 5A-E
- **Concern** The structural models are derived from AF2-Multimer predictions that the authors themselves note have "notably low" confidence scores. While the MD simulations show that some of these predicted tetramers are stable, this does not necessarily mean they represent the dominant or functionally relevant species in solution. The authors need to more clearly delineate what is experimentally determined versus computationally inferred. The claim of "atomic structural models" is too strong given the low-confidence starting predictions and the lack of direct experimental validation (e.g., cross-linking mass spectrometry, paramagnetic relaxation enhancement with site-specific labels, or solid-state NMR constraints) of the specific interhelical contacts in the tetramer models.
- **Why it matters** The central claim of the paper is the structural basis of CR multimerization. If the models are not robustly validated, the mechanistic conclusions and the implications for disease mutations are weakened.
- **Resolution test** Provide additional experimental validation of the tetramer models, such as site-directed spin labeling or cross-linking coupled with mass spectrometry, to confirm specific interhelical contacts. Alternatively, clearly reframe the models as "hypothesis-generating" rather than "established" structures.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** No
- **Axis** Functional relevance of oligomerization
- **Claim pointer** The manuscript states that "CR-mediated assembly controls TDP-43 nuclear retention function" and implies that the tetrameric assembly is the functional unit.
- **Evidence pointer** Results section "TDP-43 CR helix-mediated assembly affects TDP-43 nuclear retention"; Figure 2H
- **Concern** The cellular data show a correlation between in vitro phase separation propensity and nuclear-cytoplasmic (N/C) ratio for several mutants, but the mechanistic link is not established. The authors do not directly demonstrate that the tetrameric species observed in vitro is the species that affects nuclear retention in cells. The unexpected result for L340A (increased nuclear retention despite reduced phase separation) is not explained and suggests the relationship is more complex than proposed. The authors should discuss alternative explanations, such as effects on RNA binding, nuclear import/export signals, or interactions with other nuclear factors.
- **Why it matters** The physiological relevance of the proposed structural model depends on demonstrating that the same interactions that drive in vitro oligomerization also govern cellular function.
- **Resolution test** Perform cellular experiments with mutants that specifically disrupt the tetramer interface (e.g., W334A, L330A) and measure not only N/C ratio but also RNA binding, splicing activity, and localization dynamics. Alternatively, use a FRET or BiFC-based approach to detect oligomerization in cells.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Quantitative rigor of phase separation data
- **Claim pointer** The manuscript reports csat values for various alanine mutants and uses these to infer the role of specific residues in phase separation.
- **Evidence pointer** Results section "Alanine-scanning mutagenesis within TDP-43 CR reveal key residues in phase separation"; Figure 2A,B
- **Concern** The csat values are presented as single measurements or with unspecified error bars. The differences between mutants (e.g., ~2-fold changes) may be within experimental variability. The authors should provide replicate measurements, statistical analysis, and a clear description of how csat was determined from the sedimentation assays. Additionally, the relationship between csat and the strength of helix-helix interactions is not quantitatively modeled.
- **Why it matters** The ranking of residue importance and the correlation with computational contact frequencies depend on the reliability of the csat measurements.
- **Resolution test** Provide full dose-response curves with replicates and statistical tests for all mutants. Include a quantitative model linking csat to binding affinity or interaction energy.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** MD simulation methodology
- **Claim pointer** The manuscript uses AAMD simulations to support the stability of tetrameric models and to derive contact frequencies that correlate with experimental data.
- **Evidence pointer** Methods section "All-atom MD simulations"; Figures 5, S8
- **Concern** The simulation time (5 μs for initial screening, 100 ns for stability tests) may be insufficient to sample the conformational space of a dynamic tetramer, especially given the low confidence of the starting structures. The use of a single force field (Amber03ws) without cross-validation is a limitation. The authors should discuss the convergence of their simulations and whether the observed stability is robust to force field choice.
- **Why it matters** The computational models are a key pillar of the structural claims. If the simulations are not converged or are force field-dependent, the conclusions may not be reliable.
- **Resolution test** Provide convergence metrics (e.g., RMSD vs time, contact map stability) and repeat key simulations with an alternative force field (e.g., CHARMM36m or Amber99SB-disp) to demonstrate robustness.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of nomenclature
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The term "multimerization" is used throughout, but the specific oligomeric states (dimer, tetramer, etc.) are not consistently defined. The abstract mentions "higher-order oligomerization" without specifying the size.
- **Required correction** Define the oligomeric states clearly in the abstract and introduction, and use consistent terminology throughout.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2C
- **Evidence pointer** Results section "TDP-43 CR helix-mediated interactions are linked to CTD phase separation"
- **Issue** The correlation between CSPnorm and csat is reported with r = -0.94, but the number of data points and the statistical significance (p-value) are not provided.
- **Required correction** Include the number of mutants used in the correlation and the p-value.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of NOE data
- **Affected element** Results section "NOEs show key contacts for TDP-43 higher order self-assembly"
- **Evidence pointer** Figure 4
- **Issue** The NOE data are qualitative and the authors note that deriving molecular models directly from these constraints is challenging. However, the text implies that the NOEs are consistent with the tetramer models without a quantitative comparison.
- **Required correction** Provide a more explicit comparison between the observed NOEs and the contacts predicted by the tetramer models, or state clearly that the NOEs are only qualitatively consistent.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of disease relevance
- **Affected element** Conclusions
- **Evidence pointer** Conclusions
- **Issue** The discussion of disease relevance is brief and does not fully address how the proposed tetrameric structure explains the effects of specific ALS mutations beyond M337V.
- **Required correction** Expand the discussion to include other disease-associated mutations and how they might perturb the tetramer interface.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** NMR relaxation experiments
- **Evidence pointer** Methods section "NMR spectroscopy"
- **Issue** The exact conditions for the relaxation experiments (e.g., protein concentration, temperature, magnetic field strength) are not fully specified for the data shown in Figure 3F.
- **Required correction** Provide complete experimental parameters for the relaxation measurements.

## Risk / unsupported claims
- The claim that the tetrameric models represent the "native" functional state of TDP-43 CR is not fully supported by the data, as the models are based on low-confidence AF2 predictions and indirect experimental validation.
- The statement that "the entire 21-residue CR is conserved – to mediate assembly" is an overinterpretation, as conservation could also reflect other functions (e.g., RNA binding, interactions with other proteins).
- The mechanistic link between in vitro oligomerization, phase separation, and nuclear retention is correlative and not causally established.
- The claim that "pharmacologically stabilize the helical assembly... may be a therapeutic avenue" is speculative and not supported by any experimental evidence in this manuscript.
- The assertion that the simulations "may serve to improve future predictions" is reasonable but not a finding of this study.