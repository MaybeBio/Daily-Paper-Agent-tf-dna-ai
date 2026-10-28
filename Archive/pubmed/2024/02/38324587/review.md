## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) without figures, tables, or supporting information files
- **Assessment boundary** Scientific claims, methodological soundness, and internal consistency of the reported computational study; no assessment of figures, tables, or supplementary materials that were not provided
- **Shared manuscript claim summary** The authors use multi-scale molecular dynamics simulations and free energy calculations to propose that ASPP2 and iASPP bind p53 through an ensemble of binding modes, reconciling discrepancies between crystallography and NMR data. They claim that ensemble-average properties better match experimental observations than single crystal structure-based binding modes, and that p53's intrinsically disordered regions modulate these interactions.
- **Visible evidence base** Text descriptions of MD simulation protocols, results narratives referencing Figures 2-6 and Supplementary Figures S1-S6, and statistical comparisons described in the text
- **Missing materials affecting confidence** All figures, tables, supplementary information files, simulation parameter details, and raw numerical data; the manuscript references specific figures and tables that could not be examined

## Reviewer
- **Overall assessment** This manuscript addresses a genuine and important problem in structural biology: reconciling conflicting binding modes for the iASPP-p53 interaction determined by crystallography and NMR. The computational approach is ambitious and the conceptual framework of ensemble binding is timely. However, the evidence presented in the text alone is insufficient to fully support the central claims. Key quantitative results are described but cannot be verified without figures and numerical data. The statistical treatment appears incomplete, and the relationship between simulated encounter complexes and biologically relevant bound states requires more rigorous justification. The manuscript would benefit from clearer articulation of how the ensemble framework specifically resolves the discrepancy rather than merely accommodating both possibilities.

- **Who would be interested in the results, and why** Structural biologists studying protein-protein interactions, particularly those interested in the limitations of crystallography versus solution methods; computational biochemists developing and applying enhanced sampling or coarse-grained simulation approaches to binding free energy calculations; cancer researchers focused on p53 regulation and the ASPP family as therapeutic targets. The methodological framework of reconciling structural discrepancies through ensemble descriptions could have broader appeal to the biophysics community.

- **Major strengths** The manuscript tackles a well-defined and significant controversy in the field. The multi-scale approach combining coarse-grained and atomistic simulations is appropriate for the questions asked. The authors explicitly connect their computational findings to experimental observations including NMR chemical shift perturbations, peptide screening assays, and binding affinities. The discussion of crystal packing effects on binding equilibria is thoughtful and provides a plausible physical explanation for the discrepancy. The inclusion of IDR effects on binding kinetics and specificity adds biological relevance.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that "the ensemble-average inter-protein contacting residues and NMR-detected interfacial residues qualitatively overlap on ASPP proteins" and that this validates the ensemble binding framework.
- **Evidence pointer** Results section "Ensemble-average interprotein contacts agree with solution NMR revealed PPI interfaces", Figure 3A and 3B
- **Concern** The manuscript reports RMSE values of 0.291 and 0.248 for iASPP and ASPP2 respectively, described as "moderate deviations." Without seeing the actual comparison between contact frequency profiles and NMR chemical shift data, it is impossible to assess whether this level of agreement is meaningful or merely reflects the fact that most residues show low contact frequency. The qualitative nature of the comparison ("qualitatively overlap") is concerning for a claim that forms the primary validation of the simulation approach. The text does not describe what threshold defines a "contact" or how the comparison was normalized.
- **Why it matters** This comparison is the central validation that the ensemble simulations capture biologically relevant binding interfaces. If the agreement is only qualitative and moderate, it weakens the claim that the ensemble framework reconciles the crystallography-NMR discrepancy. The quantitative basis for this claim must be transparent and convincing.
- **Resolution test** Provide the full contact frequency profiles alongside NMR chemical shift perturbation data, with clear statistical measures of agreement beyond RMSE. Specify the contact definition, normalization procedure, and provide a statistical test for whether the overlap is better than random.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative rigor
- **Claim pointer** The authors claim that "the ensemble-average binding free energies better match experimental KD values compared to single crystallography-determined binding mode" and that for ASPP2 and iASPP, the ensemble-based ΔG values are "not statistically different from experimental values" with p = 0.623 and 0.781.
- **Evidence pointer** Results section "Ensemble-average binding free energy agrees with experimental affinities", Figure 4D
- **Concern** The statistical comparison between calculated and experimental binding free energies is problematic. The p-values reported appear to test whether the mean calculated ΔG differs from the experimental value, but the number of independent samples, the method of error propagation, and the treatment of systematic errors in force field parameters are not described. The text states that crystal structure-based ΔG values are "significantly different from the experimentally-measured binding affinities" but does not report those values or their uncertainties. The comparison between crystal structure-based and ensemble-based ΔG for iASPP shows p = 0.438, which seems to contradict the claim that the ensemble approach is superior.
- **Why it matters** The quantitative agreement with experimental binding affinities is a key pillar of the manuscript's argument. If the statistical treatment is inadequate or the comparisons are not properly controlled, the central conclusion that ensemble binding modes are more physically relevant than single crystal structures is not established.
- **Resolution test** Report all calculated ΔG values with uncertainties, the number of independent simulations used, the method for combining errors, and a clear description of the statistical tests. Show explicitly how the ensemble average is computed and why it differs from the crystal structure-based value. Address whether the p = 0.438 result for iASPP crystal structure versus ensemble undermines the claim.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Conceptual clarity
- **Claim pointer** The authors propose that "crystal packing shifts the equilibrium of binding modes towards the crystallography-determined one" and that the iASPP crystal structure binding mode (PDB 6RZ3) represents a trapped encounter complex.
- **Evidence pointer** Discussion section, Results section "Ensemble-average binding free energy agrees with experimental affinities"
- **Concern** The manuscript reports that the 1YCS binding mode (ASPP2-like) shows stronger affinity for iASPP than both the Martini CG samples and the 6RZ3 mode, with a ΔG difference of 14.6 kcal/mol between the two crystal structure-based poses for iASPP. This is a very large energy difference that requires explanation. The proposal that 6RZ3 represents a trapped encounter complex is speculative and not directly supported by the simulation data presented. The multi-funnel landscape model is invoked but not quantitatively developed or tested.
- **Why it matters** The physical explanation for why crystallography captured a non-native binding mode is central to the manuscript's resolution of the discrepancy. Without direct evidence for the trapping mechanism or quantitative support for the multi-funnel model, this remains an untested hypothesis rather than a conclusion.
- **Resolution test** Provide additional analysis supporting the encounter complex interpretation, such as structural characterization of the 6RZ3 interface in the context of the simulated ensemble, or direct simulation of crystal packing effects. Alternatively, temper the claim to reflect its speculative nature.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological validation
- **Claim pointer** The authors use Martini 3.0 CGMD to simulate protein-protein binding and then backmap selected complexes for atomistic simulations and umbrella sampling PMF calculations.
- **Evidence pointer** Materials and methods section "Martini CGMD to simulate the binding process between p53 and ASPP", "Umbrella samplings to obtain the dissociation potential of mean force (PMF)"
- **Concern** The manuscript does not describe validation of the Martini 3.0 model for this specific protein-protein system. The choice of 50 replicas of 4 μs CGMD is stated but the convergence of binding mode sampling is not demonstrated. The backmapping procedure and subsequent 100 ns atomistic optimization may not be sufficient to relax the system from CG resolution. The selection of representative complexes for umbrella sampling is described as "rigorous" with reference to supplementary figures, but the criteria are not stated in the main text.
- **Why it matters** The reliability of the ensemble binding modes depends entirely on the quality of the CGMD sampling and the backmapping procedure. If the sampling is not converged or the backmapping introduces artifacts, the resulting ensemble and free energy calculations are not trustworthy.
- **Resolution test** Provide convergence analysis for the CGMD sampling, validation of the Martini model against known binding data, and a clear description of the complex selection criteria. Demonstrate that the 100 ns atomistic optimization is sufficient for structural relaxation.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of IDR effects
- **Claim pointer** The authors claim that p53's IDRs "accelerate the binding rates" and that this effect is due to the dynamic nature of the IDRs, as shown by experiments where IDRs were rigidified.
- **Evidence pointer** Results section "p53's IDRs accelerate the binding rates and further differentiate p53's bindings toward ASPP2 and iASPP", Figure 5A
- **Concern** The manuscript reports that adding IDRs reduces the mean first passage time for contact formation from approximately 542 ns to approximately 370 ns. The control experiment with rigidified IDRs is described as showing "much slower binding," but the actual values are not reported. The claim that the effect is due to IDR dynamics rather than simply increased molecular size is only supported by this single control. The biological significance of a change in first contact formation time in CGMD simulations is not clearly established.
- **Why it matters** The IDR effects are presented as biologically meaningful, but the connection between simulated first contact times and actual binding kinetics in cells is tenuous. The differentiation of IDR effects between ASPP2 and iASPP is a key claim that requires robust quantitative support.
- **Resolution test** Report the rigidified IDR control values, provide statistical comparison between conditions, and discuss the limitations of interpreting CGMD first contact times as proxies for binding kinetics.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "the ensemble-average binding free energies better match experimental KD values compared to single crystallgarphy-determined binding mode" with a typo "crystallgarphy." The abstract also uses the phrase "qualitatively overlap" which undersells the quantitative nature of the comparison.
- **Required correction** Fix the typo and consider strengthening the language to reflect the actual statistical results.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods
- **Evidence pointer** Materials and methods section "Conventional molecular dynamics (MD) simulations"
- **Issue** The manuscript states that "the input files for MD were prepared by the tleap program from Amber20 package" but does not specify the version of Amber20, the exact force field parameters for the Zn2+ ion, or the source of the initial structures beyond PDB IDs. The hydrogen mass repartitioning and 4 fs time step are mentioned but the equilibration protocol is not fully described.
- **Required correction** Provide complete simulation parameters including software versions, force field details, equilibration steps, and any modifications to standard protocols.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results
- **Evidence pointer** Results section "Ensemble-average binding free energy agrees with experimental affinities"
- **Issue** The manuscript reports p-values for comparisons between calculated and experimental binding free energies but does not report the actual ΔG values with uncertainties for each condition. The degrees of freedom and type of t-test (paired, unpaired, one-tailed, two-tailed) are not specified.
- **Required correction** Report all ΔG values with standard errors, specify the statistical test used, and provide effect sizes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The term "encounter complex" is used loosely to describe the simulated complexes, but the authors acknowledge that these complexes may not meet the formal definition of encounter complexes. The distinction between "encounter complexes" and "intermediate binding modes" should be clarified.
- **Required correction** Define the term as used in this context and acknowledge the limitations of the analogy.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results
- **Evidence pointer** Results section "MD simulations starting from crystallography binding modes fail to capture the experiment-verified inter-protein interactions"
- **Issue** The manuscript states that "the discrepancies observed between the MD samplings and experimental findings strongly suggest that iASPP and p53 likely engage in alternative binding modes" but does not describe what the MD samplings actually showed. The reader cannot assess the nature of the failure without seeing the data.
- **Required correction** Provide a brief description of the simulation outcomes, such as the distances between the linker and RT loop over time.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction section
- **Issue** The introduction cites references for the crystallography and NMR studies but does not discuss any previous computational attempts to reconcile these discrepancies. The novelty of the ensemble approach would be clearer with explicit comparison to prior modeling efforts.
- **Required correction** Add a brief discussion of prior computational studies on ASPP-p53 interactions and how the current approach differs.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Methods
- **Evidence pointer** Materials and methods section "Sketch-map projections to obtain 2D mode"
- **Issue** The description of the sketch-map method is dense and assumes familiarity with the technique. The choice of the 21 residues used for the distance vector is not justified.
- **Required correction** Provide a brief explanation of why sketch-map was chosen over other dimensionality reduction methods and justify the residue selection.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results
- **Evidence pointer** Results section "Ensemble-average interprotein contacts agree with solution NMR revealed PPI interfaces"
- **Issue** The text refers to "iASSP" in one instance ("iASSP being slightly more severe") which appears to be a typo for "iASPP."
- **Required correction** Fix the typo.

## Risk / unsupported claims
- The claim that "crystal packing shifts the equilibrium of binding modes towards the crystallography-determined one" is presented as a conclusion but is speculative and not directly tested in the simulations
- The claim that ensemble-average binding free energies "better match" experimental values compared to crystal structure-based values is not fully supported given the reported p = 0.438 for the iASPP crystal structure comparison
- The biological significance of the IDR effects on binding kinetics is asserted but not quantitatively connected to functional outcomes
- The statement that "the ensemble of simulated iASPP-p53 complexes facilitates this interaction" (referring to the linker-RT loop interaction) is described but the specific evidence from simulations is not presented in the text
- The claim that the simulated complexes can be "loosely treated as encounter complexes" is an analogy that is not rigorously justified
- The manuscript's statement that "the ensemble binding complexes are sensitive to p53's intrinsically disordered regions" is supported by simulation data but the mechanistic explanation for this sensitivity is not fully developed