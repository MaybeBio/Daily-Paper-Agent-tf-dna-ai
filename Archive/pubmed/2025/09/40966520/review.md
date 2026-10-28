## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, supplementary materials referenced)
- **Assessment boundary** Scientific content, methodological soundness, interpretation of results, and alignment with stated conclusions. Not assessed: language editing, formatting, or literature completeness beyond what is needed for the claims.
- **Shared manuscript claim summary** The authors propose a three-step kinetic model for the interaction of the SRA domain of UHRF1 with hemi-methylated (HM) and non-methylated (NM) DNA duplexes, using thienoguanosine (thG) fluorescence labelling at four positions. They report that 5mC and C are flipped with similar rate constants, but that only 5mC-containing complexes undergo a slow conformational rearrangement that stabilizes the final complex, which they propose is the basis for methylation-specific discrimination and DNMT1 recruitment.
- **Visible evidence base** Stopped-flow fluorescence kinetics, fluorescence anisotropy binding titrations, UV-Vis absorption and steady-state fluorescence spectra, MD simulations (500 ns, multiple replicas), QM/TD-DFT calculations on representative fragments, and kinetic modelling with Dynafit. Figures 1–10 and Supplementary Figures S1–S20 are referenced.
- **Missing materials affecting confidence** The manuscript text was provided without figures, tables, or the Supplementary Information file. Numerical values for rate constants, amplitudes, and statistical errors are referenced but not visible. The Dynafit fitting residuals are described but not shown. The QM results are summarized in Table 1 and Supplementary Table S1, neither of which was available. This limits the ability to independently verify the quantitative claims.

## Reviewer
- **Overall assessment** This is a technically sophisticated and carefully executed study that addresses a mechanistically important question in epigenetic DNA methylation maintenance. The combination of multiple thG labelling positions, stopped-flow kinetics, MD simulations, and QM calculations is ambitious and largely appropriate. The central claim, that base flipping itself does not discriminate between C and 5mC but that a subsequent conformational rearrangement does, is interesting and potentially significant. However, the evidence as presented in the text alone is not fully sufficient to establish this model. The assignment of the slow kinetic phase to a specific structural rearrangement, the interpretation of the position-dependent rate constants, and the extrapolation to the full-length UHRF1 context all require additional support. The manuscript would be strengthened by clearer presentation of the fitting procedures, error analysis, and the structural basis for the proposed rearrangement.

- **Who would be interested in the results, and why** Researchers studying DNA methylation maintenance, particularly the UHRF1-DNMT1 pathway, will find this directly relevant. The broader community studying base flipping mechanisms in DNA-modifying enzymes (methyltransferases, glycosylases, repair enzymes) will also be interested, as the study provides a rare kinetic dissection of a non-enzymatic base-flipping reader protein. Methodologically, the use of thG as a positional probe for base flipping dynamics will interest biophysicists and chemical biologists working with fluorescent nucleoside analogues. The QM/MD framework for interpreting thG photophysics in DNA contexts is also of general utility.

- **Major strengths**
  1. The multi-position thG labelling strategy is well conceived. Placing the fluorophore at four distinct positions (within and adjacent to the CpG site) allows the authors to monitor different aspects of the interaction and provides internal consistency checks.
  2. The combination of experimental kinetics with MD and QM calculations is exemplary in principle. The QM calculations provide a mechanistic rationale for the fluorescence changes, bridging the gap between structural dynamics and observable signals.
  3. The use of the G448D mutant as a non-flipping control is appropriate and informative. The observation that this mutant produces only a fast, unresolvable signal change strengthens the assignment of the resolvable phases to flipping and rearrangement.
  4. The kinetic modelling is thoughtful. The authors explicitly address the unresolvable fast phase, use the dissociation rate constants as constraints, and acknowledge the possibility of more complex models.
  5. The discussion of the biological implications, particularly the "proofreading" hypothesis for base flipping, is measured and appropriately cautious.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence strength for the central kinetic model
- **Claim pointer** The authors claim a three-step mechanism for HM duplexes: (1) fast non-specific binding/sliding, (2) base flipping of 5mC with rate constant k2, and (3) a slow conformational rearrangement with rate constant k3, which is specific to 5mC and absent for C.
- **Evidence pointer** Results section, Figures 4–6, Scheme 1; location not provided for specific data points
- **Concern** The central claim rests on the assignment of the two resolvable kinetic phases to specific molecular events. The text states that kobs1 is independent of SRA concentration and similar for NM and HM duplexes, and that kobs2 is only observed for HM duplexes. However, the text does not provide the actual fitted values, the amplitudes of the phases, or the statistical quality of the fits. The assignment of step 2 to base flipping is inferential, based on the similarity of k2 values to those of known flipping enzymes. The assignment of step 3 to a conformational rearrangement is even more speculative, as no direct structural or biophysical evidence for such a rearrangement is presented. The position-dependence of kobs2 (14, 24, and 44 s⁻¹ for positions 7, 8′, and 5, respectively) is interpreted as reporting on progressive conformational changes, but the text does not explain why different positions would report different rates if they monitor the same global rearrangement. The absence of a slow phase for the 6′ label is attributed to insensitivity, but this is not independently verified.
- **Why it matters** The entire conclusion of the paper, that 5mC-specific discrimination occurs at the level of a post-flipping conformational rearrangement rather than at the flipping step itself, depends on the correct assignment of these kinetic phases. If the slow phase represents something else, such as a second binding mode or a population shift unrelated to rearrangement, the biological conclusion would be substantially weakened.
- **Resolution test** Provide the full kinetic fitting results, including rate constants, amplitudes, and error estimates for all conditions. Show that the model in Scheme 1 is uniquely identified by the data, or at least that alternative models (e.g., two-step with conformational selection, or a model with parallel pathways) are explicitly ruled out. Provide independent evidence for the proposed conformational rearrangement, such as MD analysis of the SRA-DNA interface over the timescale of the slow phase, or a mutant that specifically abolishes the slow phase without affecting flipping.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support for the QM-based interpretation
- **Claim pointer** The authors claim that QM calculations explain the fluorescence increase upon 5mC flipping by showing that the thG* state is less quenched by CT states when 5mC is absent, and that the G6′ close conformation introduces an additional quenching channel.
- **Evidence pointer** Results section, Table 1, Supplementary Tables S1, Figures 8, S15–S19; location not provided
- **Concern** The QM results are presented in a highly condensed form. The text states that the S1 minimum in the G6′ close conformation has significant CT character and that a pure thG* minimum was also located, but the relative energies, oscillator strengths, and the nature of the electronic transitions are not given in the text. The claim that the G6′ close conformation introduces a new quenching channel is based on the identification of a G6′→thG CT state, but the text does not quantify the degree of quenching or compare it with the quenching in the unflipped duplex. The connection between the computed excited states and the observed fluorescence amplitudes is qualitative at best.
- **Why it matters** The QM calculations are a key pillar of the paper's mechanistic interpretation. Without quantitative data on the energies and characters of the relevant excited states, the reader cannot assess whether the proposed quenching mechanisms are plausible or whether alternative explanations (e.g., changes in the local dielectric environment, or conformational heterogeneity) could equally explain the fluorescence changes.
- **Resolution test** Provide a table or figure with the computed excitation energies, oscillator strengths, and the character (ππ*, CT, etc.) of the lowest excited states for each of the four fragments studied. Show that the relative energies of the thG* and CT states correlate with the observed fluorescence amplitudes across the different conformations. If possible, compute the expected fluorescence quantum yield or radiative/non-radiative rates for each conformation and compare with the experimental amplitudes.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the conclusions to the full-length UHRF1 protein
- **Claim pointer** The authors conclude that "base flipping is used to discriminate 5mC from C residues" and that the slow conformational rearrangement "controls DNMT1 recruitment."
- **Evidence pointer** Discussion section; location not provided
- **Concern** All experiments were performed with the isolated SRA domain and short 12-bp duplexes. The authors acknowledge that the mechanism needs to be confirmed in the full-length UHRF1 context, but the abstract and conclusions are phrased in a way that implies a general mechanism. The SRA domain in full-length UHRF1 is part of a multi-domain protein with additional DNA-binding modules (e.g., the TTD and PHD domains) that may influence the kinetics and thermodynamics of SRA-DNA interactions. The relevance of the proposed proofreading mechanism to the physiological context, where UHRF1 is part of a larger replication-coupled methylation maintenance complex, is not established.
- **Why it matters** The significance of the study for the broader field depends on whether the proposed mechanism operates in the physiological context. If the full-length protein or other interacting partners alter the kinetic parameters or the conformational landscape, the conclusions may not translate.
- **Resolution test** Perform at least one experiment with a longer DNA substrate or a construct that includes additional UHRF1 domains, to test whether the three-step mechanism and the 5mC-specific slow phase are preserved. Alternatively, clearly limit the conclusions to the isolated SRA domain and discuss the implications for the full-length protein as speculative.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of the G488D mutant data
- **Claim pointer** The text states that "G488D" is used as a control, but the mutant is referred to as "G448D" throughout the methods and results. The authors state that this mutant is "incapable of base-flipping" and that it induces only minimal fluorescence changes.
- **Evidence pointer** Abstract, Methods, Results, Figures 2–3, S7–S9; location not provided
- **Concern** There is an inconsistency in the residue numbering: the abstract and most of the text refer to G448D, but the Results section mentions "G488D" in one instance. This is likely a typographical error, but it creates confusion. More importantly, the text does not provide a structural or functional rationale for why G448D is incapable of flipping. The mutant is used as a negative control, but the possibility that the mutation affects DNA binding affinity or the conformational dynamics of the SRA domain in ways other than abolishing flipping is not discussed. The binding constant for G448D is reported to be ~10-fold lower than for SRA, which could complicate the interpretation of the fluorescence changes.
- **Why it matters** The G448D mutant is a critical control. If the mutation has pleiotropic effects beyond abolishing flipping, the interpretation of the fast phase as non-specific binding and the assignment of the fluorescence changes to flipping may be compromised.
- **Resolution test** Clarify the residue numbering. Provide a structural rationale for the G448D mutation, ideally with reference to the known SRA-DNA crystal structure. Discuss whether the reduced binding affinity of G448D could affect the interpretation of the kinetic data, and whether any control experiments (e.g., with a different flipping-deficient mutant) were performed.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of kinetic model presentation
- **Affected element** Scheme 1 and associated text
- **Evidence pointer** Results section, Scheme 1; location not provided
- **Issue** The scheme is described in the text but not shown. The relationship between the rate constants k1, k-1, k2, k-2, k3, k-3 and the observed kobs1 and kobs2 is stated to follow reference [78], but the derivation is not given. The assumptions underlying the separation of timescales (fast equilibration of the first step) are stated but not justified quantitatively.
- **Required correction** Show Scheme 1 explicitly. Provide the equations relating kobs1 and kobs2 to the microscopic rate constants, and state the assumptions (e.g., steady-state, rapid equilibrium) with justification. If possible, provide a sensitivity analysis showing that the fitted rate constants are robust to the assumed value of k1.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical treatment of binding constants
- **Affected element** Figure 2 and associated text
- **Evidence pointer** Results section, Figure 2; location not provided
- **Issue** The binding constants are reported as mean values with standard deviations, but the number of independent replicates is not stated. The text mentions that "the prepared SRA is validated when its binding constant is within 20% of its target value," but the criteria for this validation are not described.
- **Required correction** State the number of replicates for each binding constant measurement. Describe the fitting procedure used to extract Ka from the anisotropy titrations, including how the stoichiometry (n=1) was verified.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Description of MD simulation analysis
- **Affected element** Methods section, MD simulations
- **Evidence pointer** Methods, Results, Figures 7, S14, S20; location not provided
- **Issue** The text states that "up to three replicas" of MD simulations were run, but the number of replicas for each system is not specified. The clustering algorithm is described as "hierarchic agglomerative," but the cutoff criteria for defining clusters are not given. The representative frames at 250 and 400 ns are described as "G6′ close" and "G6′ far," but the structural criteria for these designations are not quantified.
- **Required correction** Specify the number of replicas for each system. Describe the clustering procedure in sufficient detail to be reproducible. Provide the distance criteria used to classify the G6′ conformations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of alternative models
- **Affected element** Discussion section
- **Evidence pointer** Discussion; location not provided
- **Issue** The authors state that the three-step model is "currently the simplest one that integrates and matches all our data," but they do not systematically compare it to plausible alternatives, such as a model where the slow phase represents a conformational change in the protein rather than the DNA, or a model where the slow phase represents a second, higher-affinity binding mode.
- **Required correction** Add a brief paragraph explicitly considering alternative interpretations of the slow phase and explaining why they are less consistent with the data.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Abstract, Results, Discussion
- **Evidence pointer** Throughout; location not provided
- **Issue** The terms "base flipping," "base extrusion," and "nucleotide flipping" are used interchangeably. The term "proofreading" is introduced in the Discussion without a precise definition in this context.
- **Required correction** Use a single term for the process of rotating the base out of the helix. Define "proofreading" explicitly in the context of SRA function.

## Risk / unsupported claims
- The claim that the slow conformational rearrangement is "crucial for DNMT1 recruitment" is not directly supported by any experiment in this study. No DNMT1 recruitment or activity assays were performed. This is an extrapolation from the kinetic model to the biological function.
- The claim that "base flipping is used to discriminate 5mC from C residues" is supported by the kinetic data, but the mechanism of discrimination (the slow rearrangement) is not directly observed. The structural basis for this discrimination is inferred from the QM calculations and the known crystal structure.
- The statement that the G448D mutant is "incapable of base-flipping" is taken from prior work [18] and is not directly demonstrated in this study.
- The interpretation of the position-dependent kobs2 values as reporting on "progressive conformational changes" is speculative. The text does not provide a structural model that explains why the rate would differ by position.
- The claim that the initial fast phase represents "non-specific binding and sliding" is plausible but not directly tested. The authors do not provide independent evidence (e.g., from single-molecule experiments or binding assays with non-specific DNA) that this phase corresponds to sliding rather than a simple bimolecular association.