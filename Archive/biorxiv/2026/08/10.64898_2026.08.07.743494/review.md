## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, methods, and supplementary file descriptions
- **Assessment boundary** Scientific claims, methodological soundness, and evidence quality as presented in the manuscript; no assessment of editorial fit or publication venue
- **Shared manuscript claim summary** The authors present a coarse-grained simulation study of HDAC6 condensate formation, proposing a two-layer regulatory mechanism where S22 phosphorylation rewires electrostatic contacts in IDR1 and pocket-binding ligands redirect an FD3-centered folded-domain network in full-length phospho-HDAC6
- **Visible evidence base** Simulation results including single-chain properties, slab coexistence densities, contact maps, ligand engagement metrics, and domain-level interaction analyses; methods descriptions for model construction and simulation protocols
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided; no experimental validation data; no force field validation against experimental observables; no error analysis for slab simulations beyond single production runs

## Reviewer
- **Overall assessment** The manuscript addresses an important question in condensate biology: how phosphorylation and small-molecule ligands acting on folded domains can regulate multidomain protein condensation. The two-layer mechanism proposed is conceptually interesting and the simulation framework is thoughtfully constructed. However, the evidence presented is entirely computational, and several key claims rest on single-replicate simulations without adequate statistical support. The connection between the IDR1-level mechanism and the full-length behavior is not fully resolved, and the absence of experimental validation or comparison to experimental observables limits the strength of the conclusions. The work is potentially significant but requires substantial additional evidence and analysis before the claims can be considered established.

- **Who would be interested in the results, and why** Researchers studying biomolecular condensates, particularly those interested in multidomain proteins and the role of folded domains in phase separation. The work also speaks to the emerging field of condensate pharmacology, where small molecules are being explored as modulators of phase-separated assemblies. The methodological framework for coarse-grained simulation of phosphorylation and ligand effects may interest computational biophysicists working on condensate modeling.

- **Major strengths** The manuscript addresses a timely and important question about the integration of IDR and folded-domain contributions to condensate formation. The two-layer mechanism is conceptually clear and provides a useful framework for thinking about multidomain condensate regulation. The simulation methodology is carefully described, including the calibration of phosphoserine parameters and ligand models. The distinction between ligand effects on IDR1 versus full-length assemblies is an important insight that challenges simple extrapolation from isolated domain studies.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical support
  - **Claim pointer** The claim that S22 phosphorylation enhances IDR1 phase separation, supported by slab coexistence simulations showing lower C_sat for phospho-IDR1 at all salt concentrations
  - **Evidence pointer** Figure 2C-E, Results section "S22 phosphorylation promotes IDR1 phase separation by rewiring dense-phase electrostatic contacts"
  - **Concern** The slab coexistence simulations for each condition are described as single production replicates. The C_sat values are presented as single numbers without error estimates or replicate information. Given that the central claim of enhanced phase separation upon phosphorylation rests on these values, the lack of replicate simulations and statistical analysis is a critical gap. The difference between WT and phospho C_sat values at 50 mM NaCl (3.89 vs 1.27 mg/ml) is substantial, but without replicate information, it is impossible to assess whether this difference is robust or within the noise of the simulation method.
  - **Why it matters** The primary conclusion of the IDR1 section depends on the reliability of the C_sat measurements. Single-replicate slab simulations are known to be sensitive to initial conditions and finite-size effects. Without replicates, the claim of phosphorylation-enhanced phase separation is not statistically established.
  - **Resolution test** Provide at least three independent replicate slab simulations per condition, report C_sat as mean ± s.e.m., and demonstrate that the WT vs phospho difference is significant relative to the replicate variability. Alternatively, provide a complementary method such as umbrella sampling or free energy calculations to confirm the phase separation enhancement.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence for full-length mechanism
  - **Claim pointer** The claim that full-length phospho-HDAC6 assembly is organized by FD3-FD3 interactions and that ligands redirect this network toward pocket-FD3 contacts
  - **Evidence pointer** Figure 4B-G, Results section "Pocket-binding ligands redirect an FD3-centered contact network in full-length phospho-HDAC6"
  - **Concern** The full-length simulations use 15-chain systems in 30x30x30 nm boxes, which are relatively small for studying condensate organization. The domain-level contact maps are calculated over the final 3 microseconds of 10 microsecond simulations, but it is unclear whether the systems have reached equilibrium or whether the observed contact patterns are stable. The claim that FD3-FD3 is the dominant organizing feature is based on contact frequency, but no comparison is made to what would be expected from random association or from the IDR contributions. The ligand-induced changes in contact patterns are presented as qualitative differences without statistical assessment.
  - **Why it matters** The full-length mechanism is the central novel claim of the manuscript. If the contact network analysis is not robust or if the systems are not equilibrated, the conclusions about FD3-centered organization and ligand-induced redirection are not reliable.
  - **Resolution test** Demonstrate equilibration of the full-length systems through convergence of contact maps over time. Provide replicate simulations for each condition and assess the statistical significance of the FD3-FD3 vs pocket-FD3 contact differences. Compare observed contact patterns to appropriate null models to establish that FD3-FD3 association is non-random.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Experimental connection
  - **Claim pointer** The claim that the simulation results provide a molecular explanation for experimentally observed condensation behavior of HDAC6
  - **Evidence pointer** Discussion section, Conclusions
  - **Concern** The manuscript references experimental work on HDAC6 phosphorylation and condensation but does not directly compare simulation predictions to any experimental observables. The simulations are not validated against experimental data such as measured saturation concentrations, condensate sizes, or ligand binding affinities. The claim that the mechanism "provides a molecular explanation" for experimental observations is therefore not directly supported by the evidence presented.
  - **Why it matters** Without experimental validation or at least quantitative comparison to experimental observables, the biological relevance of the simulation findings remains uncertain. The manuscript would be substantially strengthened by demonstrating that the simulation predictions are consistent with available experimental data.
  - **Resolution test** Compare simulated C_sat values or contact patterns to available experimental measurements. If direct comparison is not possible, clearly state the limitations and provide testable predictions that could be experimentally verified.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Force field validation
  - **Claim pointer** The claim that the coarse-grained framework captures HDAC6 modularity and ligand pocket recognition, including the calibrated phosphoserine representation
  - **Evidence pointer** Figure 1C, Figure S2B-H, Results section "An atomistic-informed coarse-grained framework captures HDAC6 modularity and ligand pocket recognition"
  - **Concern** The phosphoserine parameters are calibrated against atomistic reference simulations, but the validation is limited to distribution matching for bonded terms. The ligand models are validated only through qualitative pocket engagement in reduced simulations. There is no validation of the overall coarse-grained model against experimental data for HDAC6, such as known secondary structure propensities, domain dynamics, or binding affinities. The IDR-water bias correction is applied uniformly but its effect on the results is not systematically tested.
  - **Why it matters** The reliability of all subsequent conclusions depends on the accuracy of the coarse-grained model. Without validation against experimental observables or at least against higher-resolution simulations for the full system, the quantitative predictions of the model are uncertain.
  - **Resolution test** Provide additional validation of the coarse-grained model, such as comparison of IDR1 conformational ensembles to atomistic simulations or experimental measurements, and sensitivity analysis of the IDR-water bias correction on the main results.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 1A
  - **Evidence pointer** Figure 1A, Results section
  - **Issue** The domain architecture schematic in Figure 1A is described but not shown in the provided text. The assignment of IDR1 as residues 1-85 in the full-length model versus residues 1-66 in the isolated simulations is potentially confusing.
  - **Required correction** Clarify the relationship between the two IDR1 definitions and ensure the figure clearly labels both constructs.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Figure 4K-N
  - **Evidence pointer** Results section "Pocket-binding ligands redirect an FD3-centered contact network in full-length phospho-HDAC6"
  - **Issue** The pocket occupancy and residence time values are reported as mean ± s.e.m., but the number of replicates and the pooling strategy are not clearly described in the main text.
  - **Required correction** Specify the number of replicates and the exact pooling procedure in the figure legends or methods.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Supplementary information
  - **Evidence pointer** Supplementary file description
  - **Issue** The manuscript references multiple supplementary figures and tables that are not provided with the submission. This limits the ability to fully assess the methods and results.
  - **Required correction** Ensure all supplementary materials are available for review, or clearly indicate which materials are not yet available.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion section
  - **Issue** The term "condensate pharmacology" is used without definition or context. This may be unfamiliar to some readers.
  - **Required correction** Define the term or provide context for its use.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods section
  - **Evidence pointer** Methods section "Molecular dynamics simulations"
  - **Issue** The methods describe the simulation protocols but do not provide specific version numbers for GROMACS, Martini, or other software tools beyond GROMACS 2021.7.
  - **Required correction** Provide complete software version information and any relevant parameter files or topology files in the supplementary materials.

- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical support for C_sat differences), R1-M2 (equilibration and statistical support for full-length contact network claims)

## Risk / unsupported claims
- The claim that S22 phosphorylation enhances IDR1 phase separation is supported by single-replicate slab simulations without statistical analysis; the difference in C_sat values cannot be assessed for significance
- The claim that FD3-FD3 is the dominant organizing feature of full-length phospho-HDAC6 assemblies is based on contact frequency analysis without demonstration of equilibration or comparison to null models
- The claim that the simulations provide a molecular explanation for experimental observations is not directly supported, as no quantitative comparison to experimental data is presented
- The claim that Nexturastat A produces stronger remodeling than HPOB relies on qualitative differences in contact maps and competition indices without statistical assessment
- The functional significance of the observed ligand-induced contact network changes for condensate properties (e.g., stability, material properties) is not demonstrated