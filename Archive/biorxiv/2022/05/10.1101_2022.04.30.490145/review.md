## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion) from bioRxiv preprint
- **Assessment boundary** Scientific content, methodological soundness, and claims as presented in the provided text; no supplementary figures or data were available for inspection
- **Shared manuscript claim summary** The authors report that the protonation state of His57, a catalytic residue located >10 Å from the trypsin S1 pocket, critically determines the spontaneous binding pathway of benzamidine. They report that neutral HID57 supports a "His57 pathway" involving a hydrogen bond with benzamidine, while positively charged HIP57 suppresses this pathway and reduces binding frequency. Constant-pH MD simulations at pH 7 and 8 are used to estimate protonation state populations and support the conclusion that accounting for such states is important in spontaneous binding simulations.
- **Visible evidence base** Results section text describing binding frequencies, average binding times, RMSF analysis, free-energy landscapes, and CpH-MD population estimates; references to Figures 1-4 and S1-S5 (not provided)
- **Missing materials affecting confidence** All figures and supplementary materials; simulation input parameters, force field validation details, convergence criteria, error estimates, and trajectory analysis protocols; raw data for binding counts and free-energy differences

## Reviewer
- **Overall assessment** This manuscript addresses a relevant and under-explored question in computational drug binding studies: whether protonation states of residues distal to the binding site can alter the observed binding pathways in spontaneous MD simulations. The system chosen, trypsin-benzamidine, is a well-established benchmark, and the comparison across three fixed protonation states plus CpH-MD is a sensible design. However, the evidence presented in the text is insufficient to fully support the central claims. Key quantitative results are reported without error estimates or statistical tests, the free-energy analysis is described only qualitatively, and the CpH-MD methodology appears inconsistent with the force field used in the conventional simulations. The conclusion that protonation states "can be key" is plausible but not rigorously established from the provided material.
- **Who would be interested in the results, and why** Computational chemists and biophysicists who use MD simulations to study ligand binding, particularly those working on enzyme-inhibitor systems or developing enhanced sampling protocols. The work may also interest experimentalists studying trypsin or serine proteases who care about pH effects on inhibitor binding. The broader message about protonation state assignment in spontaneous binding simulations is relevant to the molecular dynamics community at large.
- **Major strengths** The study addresses a genuinely under-explored aspect of spontaneous binding simulations. The choice of a benchmark system with known experimental and computational data allows for contextual comparison. The design of comparing three fixed protonation states alongside CpH-MD is methodologically sound in principle. The identification of two distinct binding pathways and the mechanistic explanation based on electrostatic repulsion is physically reasonable.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
  - R1-M4
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
  - R1-m4
  - R1-m5
- **Technical failings that need to be addressed before the case is established** R1-M1 (statistical rigor), R1-M2 (free-energy methodology), R1-M3 (CpH-MD force field consistency), R1-M4 (convergence and sampling adequacy)
- **Assessment against Nature-style criteria** Originality: moderate. The question is important but the approach is incremental over existing spontaneous binding studies. Scientific importance: potentially high for the MD community, but the current evidence does not yet establish a general principle. Interdisciplinary readership: limited; the work is primarily of interest to computational biophysicists. Technical soundness: not yet established from the provided text; several methodological concerns need resolution. Readability for nonspecialists: the text is generally clear but assumes familiarity with MD terminology and the trypsin-benzamidine system.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is valuable and the system is appropriate, but the current manuscript does not provide sufficient quantitative evidence to support the central claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and quantitative support
- **Claim pointer** The authors claim that binding is "significantly less frequent" for HIP57 (10% vs 48% for HID57) and report average binding times of 88 ns, 80 ns, and 55 ns for HID57, HIE57, and HIP57 respectively.
- **Evidence pointer** Results section, "The effect of His57 protonation states in benzamidine binding"; location not provided
- **Concern** The binding frequencies (48%, 44%, 10%) are presented as point estimates without any measure of uncertainty. With 50 replicas per condition, the 95% confidence interval for a proportion of 0.48 is approximately 0.34-0.62, and for 0.10 it is approximately 0.03-0.22. These intervals do not overlap, which is suggestive, but no statistical test is reported. The average binding times are reported as single values without standard deviations or standard errors, making it impossible to assess whether the differences (88 vs 80 vs 55 ns) are meaningful. The free-energy difference of 2.3 vs 3.8 kcal/mol is stated without error bars or a description of how it was computed.
- **Why it matters** The central claim of the paper is that protonation state alters binding probability and pathway. Without error estimates or statistical testing, the reader cannot distinguish a robust effect from stochastic variation across replicate simulations. This is particularly important given the relatively small number of binding events in the HIP57 condition (5 out of 50).
- **Resolution test** Provide confidence intervals or standard errors for all reported binding frequencies, binding times, and free-energy differences. Apply an appropriate statistical test (e.g., Fisher exact test for proportions, bootstrap for binding times) to demonstrate that the differences between protonation states are significant. Report the number of binding events per condition and the total simulation time per condition.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Free-energy calculation methodology
- **Claim pointer** The authors state that they "calculated the free-energy difference between the unbound conformation and the transition state that leads to productive binding" and report values of 2.3 kcal/mol and 3.8 kcal/mol for HID57 and HIP57.
- **Evidence pointer** Results section, "Characterization of Benzamidine Binding Pathways", reference to Figure S2; location not provided
- **Concern** The method used to compute these free-energy differences is not described. The text mentions a "3D free-energy landscape" but does not specify how it was constructed (e.g., umbrella sampling, metadynamics, histogram binning of unbiased trajectories). The choice of "transition state" is not defined operationally. Without this information, the reported values cannot be evaluated for accuracy or compared meaningfully between conditions. Additionally, the free-energy landscape in Figure 3 is described qualitatively, but no convergence analysis is mentioned.
- **Why it matters** The free-energy difference is a key quantitative result supporting the claim that HIP57 slows binding. If the calculation method is not described or validated, the reader cannot assess whether the 1.5 kcal/mol difference is real or an artifact of the chosen methodology.
- **Resolution test** Describe the exact method used to construct the free-energy landscape and compute the free-energy differences. Provide convergence checks (e.g., block averaging, multiple independent runs). Define the "transition state" criterion explicitly. If possible, compare the computed barrier with known experimental or computational values for this system.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** CpH-MD methodology and force field consistency
- **Claim pointer** The authors state that CpH-MD simulations were performed "using AMBER ff10 force-field" while conventional simulations used "AMBER-ff14SB force field."
- **Evidence pointer** Methods section, "Constant-pH Molecular Dynamics Simulations"; location not provided
- **Concern** The CpH-MD simulations use a different force field (ff10) than the conventional simulations (ff14SB). This inconsistency is not justified. If the goal is to compare binding behavior across protonation states, the protein model should be consistent. Additionally, the CpH-MD method itself (e.g., constant pH replica exchange, stochastic titration) is not described, and the parameters for the Generalized Born calculation are only partially given. The choice of which residues are titratable (His40, His57, His91) is stated, but the pKa values used or calculated are not reported.
- **Why it matters** The CpH-MD results are used to support the claim that "properly accounting for protonation states" gives a more accurate picture. If the force field differs between the fixed-state and CpH-MD simulations, any observed differences could be attributed to the force field change rather than the protonation state treatment. This undermines the internal consistency of the study.
- **Resolution test** Justify the use of ff10 for CpH-MD or repeat the CpH-MD simulations with ff14SB. Describe the CpH-MD algorithm and parameters in sufficient detail. Report the calculated pKa values for the titratable residues and compare with experimental values if available.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Sampling convergence and trajectory analysis
- **Claim pointer** The authors report that binding occurs in 48% of HID57 simulations within 200 ns and that the "His57 pathway" is observed in 79% of productive binding simulations.
- **Evidence pointer** Results section, "The effect of His57 protonation states in benzamidine binding" and "Characterization of Benzamidine Binding Pathways"; location not provided
- **Concern** No information is provided on how binding events were identified, how the pathway classification was performed, or whether the 200 ns simulation length is sufficient for convergence. The authors do not report the distribution of binding times, the number of binding and unbinding events per trajectory, or any metric of sampling convergence (e.g., cumulative binding probability as a function of time). The classification of pathways into "His57 pathway" and "direct pathway" appears to be based on visual inspection of trajectories, but no objective criteria are given.
- **Why it matters** The central conclusion that protonation state alters the binding pathway depends on the reliability of the pathway classification and the representativeness of the sampled trajectories. Without convergence analysis, the reader cannot rule out that longer simulations would reveal additional pathways or different relative frequencies.
- **Resolution test** Provide a clear operational definition of a "binding event" and the criteria for pathway classification. Report the distribution of binding times and the cumulative binding probability as a function of simulation time. Perform a convergence analysis (e.g., split the trajectories into early and late halves and compare pathway frequencies). If possible, extend a subset of simulations to check for additional binding events.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figure references
- **Affected element** Results section, "The effect of His57 protonation states in benzamidine binding"
- **Evidence pointer** Figure 2; location not provided
- **Issue** The text states that "the preferred binding mode obtained from MD simulations in the three protonation states is equivalent to the one observed in the PDB 3PTB" but does not describe how this equivalence was assessed (e.g., RMSD threshold, visual inspection).
- **Required correction** Specify the criterion used to define the binding mode as equivalent to the crystal structure.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Methods section, "System Preparation"
- **Evidence pointer** Location not provided
- **Issue** The number of benzamidine molecules placed in the solvent is stated as four, but the box size and the resulting concentration are not reported. This information is relevant for assessing whether the simulations are comparable to previous studies.
- **Required correction** Report the simulation box dimensions and the resulting benzamidine concentration.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results section, "The effect of His57 protonation states in benzamidine binding"
- **Evidence pointer** Figure 2; location not provided
- **Issue** The average binding times are reported as single values without any measure of spread. Given the small number of binding events in the HIP57 condition (5), the mean is likely to be highly variable.
- **Required correction** Report the standard deviation or interquartile range for binding times, and consider reporting the median as a more robust statistic.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation of CpH-MD results
- **Affected element** Results section, "Spontaneous Benzamidine Binding with Constant-pH Molecular Dynamics Simulations"
- **Evidence pointer** Figure 4; location not provided
- **Issue** The text states that CpH-MD at pH 7.0 produced a FEL that "resembles" the HIP57 FEL but does not quantify the similarity. The claim that CpH-MD offers "a clearer picture" is subjective without a quantitative comparison.
- **Required correction** Provide a quantitative comparison of the FELs (e.g., overlap coefficient, Jensen-Shannon divergence) or describe specific features that distinguish the CpH-MD result from the fixed-state results.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Generalizability of conclusions
- **Affected element** Discussion section
- **Evidence pointer** Location not provided
- **Issue** The authors suggest that protonation states of in-pathway residues should be considered in spontaneous binding simulations, but the study only examines one system (trypsin-benzamidine) and one residue (His57). The generalizability of this recommendation is not demonstrated.
- **Required correction** Acknowledge the limited scope of the study and suggest specific systems or conditions where the effect might be tested further.

## Risk / unsupported claims
- The claim that "binding is significantly less frequent" for HIP57 is not supported by statistical testing.
- The free-energy differences (2.3 vs 3.8 kcal/mol) are reported without methodological detail or error estimates, making them unverifiable.
- The claim that CpH-MD provides "a clearer picture" of binding is subjective and not quantitatively supported.
- The statement that "properly accounting for protonation states of distal residues can be key to obtain reliable pathways" is presented as a general conclusion but is based on a single system and residue.
- The classification of binding pathways into "His57 pathway" and "direct pathway" lacks objective criteria and is not validated.
- The use of different force fields (ff14SB vs ff10) between conventional and CpH-MD simulations is not justified and may confound comparisons.