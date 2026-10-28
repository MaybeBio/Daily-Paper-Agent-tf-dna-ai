## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion) without figures, tables, or supplementary information
- **Assessment boundary** Scientific claims, methodological soundness, and force field evaluation as presented in the text; no assessment of figures, tables, or SI content beyond what is described
- **Shared manuscript claim summary** The authors evaluate how well current AMBER force fields (OL15, bsc1, OL15χOL3) describe the continuous B- to A-DNA transition in protein-DNA complexes, focusing on sugar pucker and glycosidic torsion conformations. They report that geometries of A-like intermediate states are modeled reasonably well, but their populations are significantly underestimated, with stability increasing in the order OL15 < bsc1 < OL15χOL3. They also report that force fields predict correct sequence-dependent A-form propensities in naked DNA.
- **Visible evidence base** Text descriptions of MD simulations (8 protein-DNA complexes, 1 μs time scale, AMBER 18, OL15/bsc1/OL15χOL3 force fields), classification of backbone conformations using NtC dinucleotide classes, and comparisons between X-ray and MD populations
- **Missing materials affecting confidence** All figures, tables, and supplementary information referenced in the text (Figures 1-6, Tables 1-5, Tables S2-S3, Figure S1) are not provided; no numerical data, error estimates, or statistical analyses are visible; no simulation convergence or reproducibility metrics are shown

## Reviewer
- **Overall assessment** The manuscript addresses a relevant and timely question in computational biophysics: whether current AMBER force fields can accurately describe the continuous B- to A-DNA transition in protein-DNA complexes. The authors have selected a reasonable set of eight diverse protein-DNA complexes and performed 1 μs MD simulations with three force field variants. The central claim that A-like conformer populations are underestimated is plausible and consistent with prior work from the same group. However, the manuscript as presented cannot be fully evaluated because all quantitative evidence (figures, tables, SI) is missing from the provided material. The text alone supports the qualitative conclusions but does not allow verification of the quantitative claims, statistical significance, or force field comparisons. The writing is generally clear but contains some typographical errors and inconsistencies in the conclusions section that need correction.

- **Who would be interested in the results, and why** Computational biophysicists and force field developers working on nucleic acid simulations would be the primary audience. Researchers studying protein-DNA recognition, particularly those using MD simulations to model transcription factors, chromatin proteins, and DNA-processing enzymes, would also find these results relevant. The finding that A-like states are underestimated across multiple AMBER force fields has practical implications for anyone simulating protein-DNA complexes, as it suggests systematic biases in predicted binding geometries and energetics. The work could also inform future force field parameterization efforts targeting sugar pucker and glycosidic torsion terms.

- **Major strengths** The study addresses an important and underappreciated problem in nucleic acid simulations: the accurate description of intermediate A/B conformational states, which are over-represented at protein-DNA interfaces. The selection of eight diverse protein-DNA complexes spanning different binding motifs and minor/major groove interactions is thoughtful. The comparison of three force field variants (OL15, bsc1, and the experimental OL15χOL3 combination) is well designed to isolate the contribution of the glycosidic torsion parameterization. The authors appropriately acknowledge the arbitrary nature of the χ division line between anti and high-anti conformations. The connection to prior work on A-DNA stability in solution strengthens the overall argument.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims that "the populations of A-like states seem to be too small in many cases" and provides specific percentages (e.g., "average percentage conservation of for instance the native A/A states in the MD simulations is only 21, 26 and 33% on our 1 μs time scale")
- **Evidence pointer** Tables 3 and 4, location not provided
- **Concern** All quantitative results supporting the central claims are contained in tables and figures that are not included in the provided material. The specific population percentages, force field comparisons, and per-complex data cannot be verified. Without access to Tables 3 and 4, the reader cannot assess whether the reported differences between force fields are meaningful or within statistical noise.
- **Why it matters** The central conclusion that A-like states are underestimated depends entirely on the population data in these tables. The claim that stability increases in the order OL15 < bsc1 < OL15χOL3 requires the actual numbers to be evaluated. The manuscript's scientific contribution rests on these quantitative comparisons.
- **Resolution test** Provide Tables 3 and 4 with population percentages, standard errors or confidence intervals, and per-complex breakdowns. The claims should be verifiable from the data presented.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript states that "different force fields predict different propensities for A-like states growing in the order OL15 < bsc1 < OL15χOL3" and that "the stability of the A-like states is underestimated by the tested force fields"
- **Evidence pointer** Tables 3 and 4, location not provided
- **Concern** No statistical analysis is described or presented. The text reports population differences between force fields and between X-ray and MD structures, but no error bars, standard deviations across replicates, or significance tests are mentioned. The manuscript does not state whether simulations were replicated, how many independent trajectories were run, or how sampling uncertainty was assessed. The observation that "the small differences are likely random and statistically insignificant" for RMSD suggests awareness of statistical issues, but no such analysis is applied to the population data.
- **Why it matters** The claim that one force field performs better than another requires demonstration that the differences are not due to sampling noise. Without statistical treatment, the ordering OL15 < bsc1 < OL15χOL3 could be an artifact of limited sampling or single trajectories.
- **Resolution test** Provide statistical analysis of population differences, including standard errors, confidence intervals, or replicate simulations. State how many independent trajectories were run and how sampling uncertainty was quantified.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Claim overreach
- **Claim pointer** The manuscript concludes that "the instability of the A-like forms in the current AMBER force fields represents a serious problem for accurate modeling of protein-DNA interactions and modification of the description of the sugar puckering may be needed"
- **Evidence pointer** Results section, "Average Stability of A-like Backbones" subsection, location not provided
- **Concern** The manuscript demonstrates that A-like conformer populations are lower in MD than in X-ray structures, but does not establish that this "seriously" affects binding energy or functional predictions. The statement that "the instability of the A-like geometries... can be expected to destabilize the binding motif and significantly reduce the binding energy" is speculative, as no binding free energy calculations or functional assays are presented. The leap from conformational population bias to binding energy consequences is not quantitatively supported.
- **Why it matters** The broader significance of the work depends on the claim that force field inaccuracies materially affect protein-DNA binding predictions. If the population bias does not translate into meaningful energetic or structural errors, the practical importance is reduced.
- **Resolution test** Either temper the conclusion to reflect that binding energy consequences are inferred rather than demonstrated, or provide additional calculations (e.g., binding free energy estimates, end-point methods) that quantify the impact of A-like state destabilization on binding.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Internal consistency
- **Claim pointer** The conclusions section states "This applies not only to the pure A-DNA form (P/χ = A/A), but also to the conformations intermediate between A- and B-DNA, i.e., P/χ = A/A and P/χ = A/A, which are typical for protein-DNA complexes"
- **Evidence pointer** Conclusions section, location not provided
- **Concern** The conclusions section contains an apparent typographical error: "P/χ = A/A and P/χ = A/A" should presumably read "P/χ = A/B and P/χ = B/A" based on the earlier text. This error obscures the intended meaning and suggests the conclusions were not carefully proofread. Additionally, the abstract states "the geometries of the A-like intermediate states in the molecular dynamics (MD) simulations agree well with the native X-ray geometries," but the results section notes that "bsc1 and OL15χOL3 being somewhat more distant" from experimental A/B geometry, which is a more nuanced statement than the abstract conveys.
- **Why it matters** The typographical error in the conclusions directly affects the scientific content, as it misidentifies which conformations are being discussed. The abstract overstates the agreement between MD and X-ray geometries relative to the more qualified statements in the results.
- **Resolution test** Correct the typographical error in the conclusions. Ensure the abstract accurately reflects the nuanced findings in the results section, including force field specific differences.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Methodological transparency
- **Claim pointer** The manuscript states "The analysis of nucleic acid structure parameters was performed using the cpptraj module and nastruct tool of AMBER software package" and describes the classification of sugar pucker and glycosidic torsion
- **Evidence pointer** Methods section, "MD Simulations" and "Classification of Backbone Conformations" subsections, location not provided
- **Concern** The methods section does not describe several critical simulation parameters: the specific AMBER force field versions for the protein and ions, the water model used, the temperature and pressure coupling schemes, the equilibration protocol, the total simulation length per system, the number of replicates, or the criteria for determining when a simulation is converged. The manuscript mentions "1 μs time scale" but does not specify whether this applies to all systems and all force fields. The treatment of Mg2+ ions and the replacement of BrU residues are mentioned but not described in sufficient detail.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without complete simulation parameters, other groups cannot replicate the work or assess whether the results depend on specific methodological choices. The comparison between force fields is only meaningful if all other simulation conditions are held constant and described.
- **Resolution test** Provide a complete description of all simulation parameters, including software versions, water model, ion parameters, equilibration protocol, simulation length per system, number of replicates, and convergence criteria.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states "The combination of A-like P and B-like χ (and vice versa) represents the nature of the intermediate states lying between the pure A- and B-forms." This sentence is grammatically awkward and could be clearer. The phrase "represents the nature of" is vague.
- **Required correction** Rephrase to something like "Intermediate states between the pure A- and B-forms are characterized by combinations of A-like sugar pucker with B-like glycosidic torsion, and vice versa."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Typographical error
- **Affected element** Results section
- **Evidence pointer** Results section, "Average Stability of A-like Backbones" subsection, location not provided
- **Issue** The text reads "the time evolution of P and χ in MD simulationsan can vary significantly" where "simulationsan" appears to be a typographical error for "simulations".
- **Required correction** Correct to "the time evolution of P and χ in MD simulations can vary significantly".

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Typographical error
- **Affected element** Conclusions section
- **Evidence pointer** Conclusions section, location not provided
- **Issue** The text reads "reflects the average X-ray geometries known form the crystal structures" where "form" should be "from".
- **Required correction** Correct to "known from the crystal structures".

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Introduction, location not provided
- **Issue** The sentence "The fact that neither our OL15 nor bsc1 correctly predicts A-DNA stability in solution led us to investigate A/B equilibrium in protein-DNA complexes" is somewhat informal for a scientific manuscript. The phrase "The fact that" can be removed for conciseness.
- **Required correction** Rephrase to "Since neither OL15 nor bsc1 correctly predicts A-DNA stability in solution, we investigated A/B equilibrium in protein-DNA complexes."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Conclusions section
- **Evidence pointer** Conclusions section, location not provided
- **Issue** The conclusions state "the conformations intermediate between A- and B-DNA, i.e., P/χ = A/A and P/χ = A/A" which contains a clear typographical error (should be A/B and B/A). This is noted in Major Concern R1-M4 but is listed here as a minor editorial issue as well.
- **Required correction** Correct to "P/χ = A/B and P/χ = B/A".

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section
- **Evidence pointer** Methods section, "Selection of Protein-DNA Complexes" subsection, location not provided
- **Issue** The methods state that structures were selected based on NtC dinucleotide classification and "confal" scores, but the specific criteria for selection (e.g., minimum confal score, resolution cutoff, sequence constraints) are not provided.
- **Required correction** Provide explicit selection criteria, including numerical thresholds for confal scores and resolution.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section
- **Evidence pointer** Results section, "P/χ = B/A States" subsection, location not provided
- **Issue** The text states "This is very frequent, because of the anti/high-anti overlap, and in fact it is not possible to clearly distinguish the B/A and B/B forms because of a relatively small shift in the χ angle." This statement is somewhat circular and could be clarified by explaining the physical basis for the overlap.
- **Required correction** Clarify why the anti/high-anti overlap occurs and what the implications are for the classification scheme.

## Risk / unsupported claims
- The claim that "the instability of the A-like forms in the current AMBER force fields represents a serious problem for accurate modeling of protein-DNA interactions and modification of the description of the sugar puckering may be needed" is not fully supported by the presented evidence, as no binding energy calculations or functional consequences are demonstrated.
- The claim that "the force fields seem to predict the correct sequence-dependent A-form propensity" is based on a qualitative comparison in Table 5, which is not visible in the provided material; the statistical significance of this correlation is not established.
- The statement that "the instability of the A-like geometries... can be expected to destabilize the binding motif and significantly reduce the binding energy" is speculative and not quantitatively supported.
- The specific population percentages (21%, 26%, 33% for A/A states) cannot be verified without access to Tables 3 and 4.
- The claim that "the geometries of the A/B intermediate states are modeled reasonably well by the OL15 force field" is based on visual comparison in Figure 3, which is not visible; no quantitative geometric comparison metrics are described.
- The manuscript's statement that OL15χOL3 results "suggest that the P/χ = B/A might be on the verge of being overpopulated in naked DNA simulations" is presented without quantitative thresholds for what constitutes "overpopulation."
- The assertion that "the small differences are likely random and statistically insignificant" for RMSD is made without statistical testing.