## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, conclusions, and data availability statements. Figures and tables are referenced but not directly viewable. Supporting material (Figures S1–S16, Table S1) is mentioned but not provided.
- **Assessment boundary** Scientific content, methodological rigor, internal consistency, and support of claims by presented evidence. No assessment of formatting, language style, or journal fit beyond general Nature-style criteria.
- **Shared manuscript claim summary** The authors characterize the conformational ensemble of the p53 proline-rich domain (PRD) using extensive atomistic molecular dynamics simulations, supported by CD and SAXS experiments. They report that the PRD is intrinsically disordered yet contains substantial transient polyproline II (PPII) structure, that consecutive prolines (Pro71–Pro72) impose local steric constraints stabilizing extended conformations, that end-to-end restraints mimicking the full-length protein context improve agreement with SAXS data, and that disease-associated variants P72R and P82L locally perturb these structural features.
- **Visible evidence base** Main text with embedded figure references (Figures 1–8), two tables (Tables 1–2), equations for CD conversion and chi-square metric, and data availability links. Supporting figures and table are referenced but not accessible.
- **Missing materials affecting confidence** Supporting figures S1–S16 and Table S1 are not provided. These include Ramachandran plots (Figure S2), minimum distance maps for variants (Figure S9), NMR comparisons (Figures S13–S15), and additional structural analyses. Without these, several claims cannot be independently verified. Experimental details for CD and SAXS sample preparation, data processing, and error analysis are incomplete. Force field validation and convergence assessments are not fully described.

## Reviewer
- **Overall assessment** This manuscript presents a systematic computational study of the p53 proline-rich domain, combining extensive MD simulations with experimental validation. The work addresses a relevant question about the structural behavior of an important disordered region in a major tumor suppressor. The central finding that PPII helices are robust structural features within a disordered ensemble, and that proline patterning rather than abundance governs local structure, is potentially valuable. The comparison between unrestrained and restrained simulations to model the IDP versus IDR context is thoughtful. However, several technical concerns limit the strength of the conclusions. The absence of cis-proline states in the simulations is acknowledged but its quantitative impact is not fully assessed. The experimental validation is qualitative for CD and the SAXS agreement, while improved with restraints, is based on a non-standard chi-square metric. The variant analysis is limited to two mutations with relatively modest observed effects. The manuscript would benefit from clearer demonstration that the simulation results are converged and robust to force field choice.
- **Who would be interested in the results, and why** Researchers studying intrinsically disordered proteins, particularly those interested in proline-rich regions and their structural propensities. The p53 community will find the variant analysis relevant, especially the mechanistic interpretation of P72R and P82L effects. Computational biophysicists developing or applying MD methods to disordered proteins will be interested in the restrained simulation approach and its comparison to experimental data. The findings on PPII as structural elements within disordered regions may also interest those studying protein-protein interactions involving SH3 domains and similar recognition modules.
- **Major strengths** 1) The study addresses a biologically important yet undercharacterized region of p53 using a combination of computational and experimental approaches. 2) The systematic analysis of secondary structure propensities, including the decomposition by radius of gyration, provides a detailed picture of the conformational ensemble. 3) The comparison between unrestrained and restrained simulations to model the IDP versus IDR context is a thoughtful approach that yields improved agreement with SAXS data. 4) The variant analysis, while limited, connects local structural perturbations to potential functional consequences. 5) The authors are transparent about limitations, particularly the absence of cis-proline states and the qualitative nature of CD validation.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the simulations capture the conformational ensemble of the p53 PRD and that the force field used (AMBER99SB-ILDN with TIP4P-D) generates ensembles with radius of gyration and secondary structure distributions comparable to other IDP-capable force fields.
- **Evidence pointer** Materials and methods, Atomistic molecular dynamics simulations; Results, "The p53 PRD samples a broad CoE with persistent local structure"
- **Concern** The manuscript does not provide sufficient evidence for convergence of the simulations. No block-averaging analysis, autocorrelation times, or other convergence metrics are presented. The claim that five replicates of unspecified length are sufficient to sample the conformational space of a disordered 29-residue peptide is not adequately supported. Additionally, the comparison to other force fields is referenced to a prior study (reference 25) but no direct comparison is shown for this specific system. The choice of AMBER99SB-ILDN with TIP4P-D, while reasonable, may not be optimal for proline-rich sequences, and the authors do not demonstrate that their results are robust to force field choice.
- **Why it matters** For a study whose primary conclusions depend on the conformational ensemble sampled by MD, demonstrating convergence and force field robustness is essential. Without this, the quantitative claims about PPII content, radius of gyration distributions, and the effects of restraints or mutations cannot be considered reliable. The biological interpretations rest on the accuracy of the simulated ensembles.
- **Resolution test** Provide convergence analysis showing that ensemble averages are stable across simulation time and across replicates. Include a comparison of key observables (Rg, Ree, secondary structure propensities) from simulations with at least one alternative IDP-appropriate force field (e.g., CHARMM36m, a99SB-disp) to demonstrate that the qualitative conclusions are not force field dependent. If such simulations are not feasible, clearly state this limitation and temper the strength of the quantitative claims.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that "the absence of cis-proline conformations in the simulations" is a limitation and that "the effective behavior is likely to lie between these extremes" when comparing all-trans and cis-Pro82 simulations.
- **Evidence pointer** Results, "Impact of cis-trans proline isomerization: Limitation and assessment"
- **Concern** The manuscript acknowledges that cis-proline states are not sampled in the standard MD simulations, yet the quantitative claims about PPII content and ensemble properties are based on all-trans simulations. The single cis-Pro82 simulation is presented as a complement, but the authors do not estimate the fraction of cis conformers expected for each proline in the PRD. Given that 5%–10% of prolines in disordered proteins populate cis states, and that the PRD has 10 prolines, the cumulative effect of multiple cis prolines could be substantial. The claim that the "effective behavior is likely to lie between these extremes" is not quantitatively justified. The authors do not attempt to estimate the ensemble-weighted average properties that would result from a mixture of cis and trans states.
- **Why it matters** The central conclusion that PPII helices are robust structural features depends on the all-trans assumption. If a significant fraction of the ensemble contains cis prolines, the PPII content could be substantially lower, and the structural interpretation would change. The authors' own cis-Pro82 simulation shows a dramatic reduction in PPII and increase in beta-bends, suggesting that cis states have a strong local effect. Without a quantitative treatment of cis-trans isomerization, the reported PPII fractions and their functional implications are uncertain.
- **Resolution test** Estimate the cis fraction for each proline in the PRD using available experimental data (e.g., NMR from reference 7) or computational predictions. Perform ensemble-weighted averaging of structural properties using the estimated cis fractions, or perform enhanced sampling simulations (e.g., replica exchange with explicit cis/trans states) to directly sample the isomerization. If this is not feasible, clearly state that the reported PPII fractions represent an upper bound and discuss how the conclusions might change with realistic cis populations.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that "PPII helices emerge as particularly robust features, acting as stiff spacers linking the transactivation domain to downstream regions" and that "proline-mediated rigidity and transient PPII structure are key determinants of the dynamic conformational landscape of the p53 PRD."
- **Evidence pointer** Results, "Functional implications and broader context"; Conclusions
- **Concern** The functional significance of the PPII helices is inferred from structural simulations but is not directly tested. The claim that PPII helices act as "stiff spacers" is based on the observation that extended conformations have higher PPII content, but no quantitative analysis of stiffness or spacer function is presented. The connection to p53 function, such as how PPII structure might affect interactions with binding partners or post-translational modifications, is speculative. The variant analysis shows local perturbations but does not demonstrate functional consequences. The broader claim that these findings "offer insight into the role of internal disordered regions in tumor suppression" is not supported by direct experimental evidence.
- **Why it matters** The manuscript positions itself as providing molecular-level understanding of p53 PRD function. If the functional claims are not directly tested, the significance of the work is reduced to a structural characterization. The authors should either provide experimental or computational evidence linking the observed structural features to function, or clearly frame the work as a structural characterization with hypotheses for future testing.
- **Resolution test** Provide additional analysis or experiments that directly test the functional role of PPII structure. This could include binding simulations or experiments with SH3 domains, analysis of post-translational modification accessibility, or comparison with functional assays from the literature. Alternatively, revise the claims to clearly state that the functional implications are hypotheses based on structural observations, not demonstrated conclusions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "restrained simulations with Ree 40–50 Å show improved agreement with experimental SAXS profiles" and that this "likely reflects the fact that, in vivo and in experimental constructs, the PRD does not behave as a fully isolated chain."
- **Evidence pointer** Results, "Modeling the PRD as an internal disordered region using end-to-end restraints"; Table 2
- **Concern** The chi-square metric used to compare simulated and experimental SAXS profiles is non-standard and the authors note it "does not represent a statistically rigorous goodness of fit." The improvement in chi-square from 0.397 (unrestrained) to 0.133 (Ree = 40.7 Å) or 0.056 (Ree = 51.2 Å) is presented as evidence for improved agreement, but without error bars on the simulated profiles or a proper statistical framework, it is unclear whether these differences are significant. Additionally, the restrained simulations fix the end-to-end distance, which is a strong constraint that may artificially improve agreement by reducing conformational variability. The authors do not discuss whether the improved chi-square could result from overfitting or from the reduced conformational space being closer to the experimental average by chance.
- **Why it matters** The claim that the PRD behaves as an IDR with effective spatial constraints is used to support the biological relevance of the restrained simulations. If the improved SAXS agreement is not statistically robust, this conclusion is weakened. The choice of restraint distances (10–50 Å) and the specific values used are not fully justified.
- **Resolution test** Provide a more rigorous statistical comparison between simulated and experimental SAXS profiles, including error estimates on the simulated profiles and a proper goodness-of-fit test. Discuss the potential for overfitting with restrained simulations. Justify the choice of restraint distances based on the cryo-EM structure and the expected distance between adjacent domains in full-length p53. If possible, validate the restrained ensemble against additional experimental observables beyond SAXS.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "circular dichroism and small-angle X-ray scattering experiments corroborate the largely disordered yet partially structured nature of the PRD" and that temperature-dependent CD at 228 nm is "consistent with PPII structure."
- **Evidence pointer** Results, "Consistency with circular dichroism spectroscopy: Qualitative agreement"; Materials and methods, Circular dichroism
- **Concern** The CD analysis is described as "qualitative" and the authors state that "simulated CD spectra and CD deconvolution results are not used here to quantitatively validate the simulated ensembles." The temperature-dependent CD at 228 nm shows a linear and reversible response, which is interpreted as consistent with PPII, but this is a weak diagnostic. The authors do not provide a quantitative comparison between experimental and simulated CD spectra, nor do they estimate PPII content from the CD data. The SAXS comparison is more quantitative but, as noted above, uses a non-standard metric. The experimental validation is therefore largely qualitative and does not strongly constrain the simulation results.
- **Why it matters** The manuscript claims experimental corroboration of the simulation findings. If the experimental validation is only qualitative, the strength of the corroboration is limited. The authors should either provide more quantitative experimental analysis or clearly state the limitations of the experimental validation.
- **Resolution test** Provide a quantitative analysis of the CD data, such as deconvolution with a PPII basis set or comparison with calculated CD spectra from the simulations. If this is not possible, clearly state that the CD data provide only qualitative support and discuss what additional experiments would be needed for stronger validation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction, first paragraph
- **Evidence pointer** Introduction, paragraph 1
- **Issue** The introduction assumes familiarity with p53 domain architecture and IDP terminology. The significance of the PRD and its role in p53 function could be explained more clearly for a broader audience.
- **Required correction** Briefly explain why the PRD is important for p53 function, such as its role in regulating apoptosis and its interaction with SH3 domains, before diving into the structural questions.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and methods, Atomistic molecular dynamics simulations
- **Evidence pointer** Materials and methods, Atomistic molecular dynamics simulations
- **Issue** The methods section does not specify the total simulation time per replicate, the number of atoms in the system, or the equilibration protocol in sufficient detail. The statement "five replicates with a total simulation run time of 15.6 μs" implies approximately 3 μs per replicate, but this is not explicit.
- **Required correction** Provide the simulation length per replicate, system size, and a more detailed description of the equilibration and production run protocols.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, "Consistency with circular dichroism spectroscopy: Qualitative agreement"
- **Evidence pointer** Results, "Consistency with circular dichroism spectroscopy: Qualitative agreement"
- **Issue** The temperature range for the CD measurements is not stated, and the reversibility of the thermal denaturation is mentioned but not shown. The statement "the cross indicates the Δϵ value after cooling from the highest temperature" suggests reversibility but the data are not presented.
- **Required correction** Specify the temperature range used and show the cooling data or state that the reversibility was verified but not shown.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Results, "Local structural determinants underlying PPII stabilization"
- **Evidence pointer** Results, "Local structural determinants underlying PPII stabilization"
- **Issue** The analysis of structural determinants is largely descriptive. The authors identify that consecutive prolines impose steric constraints, but do not quantify the energetic contributions or compare to other proline-rich sequences.
- **Required correction** Consider adding a quantitative analysis of the energetic contributions to PPII stabilization, or discuss how the findings compare to known PPII propensities in other proline-rich peptides.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Results, "Impact of cis-trans proline isomerization: Limitation and assessment"
- **Evidence pointer** Results, "Impact of cis-trans proline isomerization: Limitation and assessment"
- **Issue** The discussion of cis-trans isomerization is brief and does not fully explain the biological relevance of this phenomenon for readers outside the biophysics community.
- **Required correction** Briefly explain why cis-trans proline isomerization is biologically important, such as its role in regulating protein function and its catalysis by enzymes like PIN1.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, "Local structural determinants underlying PPII stabilization"
- **Evidence pointer** Results, "Local structural determinants underlying PPII stabilization"
- **Issue** The hydrogen bond analysis is mentioned but the results are not shown in the main text. The statement "Hydrogen-bond analysis (Fig. 2, c) reveals a low overall hydrogen-bonding propensity" refers to a figure that is not clearly described.
- **Required correction** Clarify which figure panel shows the hydrogen bond analysis and describe the key findings in the text.

## Risk / unsupported claims
- The claim that PPII helices act as "stiff spacers" with functional significance is not directly tested and should be framed as a hypothesis.
- The quantitative PPII content (31.1% ± 11.9%) is based on all-trans simulations and likely represents an upper bound given the expected 5%–10% cis population.
- The improved agreement of restrained simulations with SAXS data is based on a non-standard chi-square metric without statistical rigor.
- The claim that P82L "provides a mechanistic explanation for impaired PIN1-dependent regulation" is inferred from structural simulations and not directly demonstrated.
- The experimental CD validation is qualitative and does not provide quantitative constraints on the simulation ensemble.
- The NMR comparison is mentioned but the data are not shown in the main text, making the claim of corroboration unverifiable from the provided materials.
- The statement that the PRD "encodes a robust local structural fingerprint" is based on simulations with a single force field and may not be generalizable.