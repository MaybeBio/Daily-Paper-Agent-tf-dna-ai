## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, conclusions, materials and methods) as provided
- **Assessment boundary** Scientific content, methodological soundness, and support of claims based solely on the supplied text; no external data, figures, or supplementary materials were available for inspection
- **Shared manuscript claim summary** The authors use atomistic molecular dynamics simulations to investigate eight cancer-associated missense mutations in human DNA polymerase η (Polη) across pre- and post-translocation states, proposing a unified mechanistic framework in which these mutations converge on reduced DNA binding and impaired translocation through distributed structural perturbations
- **Visible evidence base** Text descriptions of simulation protocols, results summaries, and references to figures and tables (Figures 1–4, S1–S32; Tables S1–S3); no actual data, trajectories, or quantitative results were visible
- **Missing materials affecting confidence** All figures, tables, and supplementary materials; quantitative values beyond a few distances and free energies; simulation convergence metrics; force field validation details; experimental validation data

## Reviewer
- **Overall assessment** The manuscript addresses a clinically relevant and mechanistically important question: how missense mutations in Polη associated with the cancer-prone syndrome xeroderma pigmentosum variant impair enzyme function. The authors employ state-of-the-art equilibrium MD simulations with multiple replicas and microsecond timescales, which is commendable. However, the central claim of a "unified mechanistic framework" rests on qualitative convergence of contact perturbations and semi-quantitative free energy estimates, and the evidence presented in the text does not fully establish this framework. The manuscript would benefit from clearer quantitative support, explicit statistical treatment, and a more critical discussion of limitations. The work is potentially of interest to the DNA repair and computational biophysics communities, but the current evidence base is insufficient to fully support the conclusions as stated.

- **Who would be interested in the results, and why** Researchers in DNA damage tolerance and translesion synthesis, particularly those studying Y-family polymerases and their disease-associated variants; computational biophysicists interested in protein–DNA interactions, allosteric communication, and free energy methods; clinical geneticists studying XP-V genotype–phenotype correlations. The proposed convergence of diverse mutations on common DNA-binding defects could inform future functional studies and potentially therapeutic strategies.

- **Major strengths** The study addresses a clinically important and mechanistically under-characterized set of mutations. The simulation protocol is rigorous, with multiple replicas, microsecond timescales, and modern force fields. The analysis combines structural, energetic, and dynamical perspectives, which is a strength. The comparison across eight mutations in two functional states provides a broad survey. The identification of a potential convergence on DNA-binding defects is an interesting hypothesis.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for central claim
- **Claim pointer** "we could identify a unified mechanistic framework for decoding how XP-V pathogenic mutations compromise Polη function by destabilizing the Polη–DNA complex"
- **Evidence pointer** Results sections; Figures 3–4; Tables S2–S3
- **Concern** The central claim of a "unified mechanistic framework" is not quantitatively established. The evidence presented is largely qualitative: contact frequency changes are described as "decreased" or "increased" without statistical significance testing, and the MM/PBSA free energy differences are reported as mean ± standard deviation without error propagation or significance assessment. The text states that mutations "converge" on reduced DNA binding, but the reported ΔΔG values range from +32 to −53 kcal/mol in state III and +41 to −14 kcal/mol in state IV, which is an enormous spread. It is unclear how such heterogeneous energetic effects support a unified framework. The authors need to provide a quantitative metric of convergence, such as a common set of significantly perturbed residues across all mutants, with appropriate statistical testing.
- **Why it matters** The central claim of the manuscript is the unified mechanism. Without quantitative support, the conclusion is not established, and the manuscript reduces to a descriptive survey of eight mutations.
- **Resolution test** Provide statistical analysis of contact perturbations (e.g., bootstrap or permutation tests) to identify residues significantly affected across mutants. Report MM/PBSA results with standard errors and perform significance testing of ΔΔG values relative to WT. Demonstrate that a common set of residues or interactions is significantly perturbed in at least 7 of 8 mutants in both states.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological validation
- **Claim pointer** "we employed classical molecular dynamics (MD) simulations" and "All simulations reached stable conformational ensembles, as assessed by the root-mean-square deviation (RMSD)"
- **Evidence pointer** Materials and Methods, Molecular Dynamics; Figures S1–S8
- **Concern** The manuscript does not provide sufficient evidence that the simulations are converged and that the observed differences between WT and mutants are not artifacts of insufficient sampling. RMSD stability alone is a necessary but insufficient criterion for convergence of protein–DNA interactions. No block averaging, autocorrelation analysis, or replica convergence metrics are described. The use of three replicas per system is good, but the text does not report whether replicas agree with each other. Additionally, the choice of starting from a single experimental structure for each state may bias the results; no assessment of conformational sampling completeness (e.g., principal component overlap) is provided.
- **Why it matters** Without demonstrated convergence, the observed differences between WT and mutants could reflect incomplete sampling rather than genuine mutational effects. This undermines all downstream analyses.
- **Resolution test** Provide convergence metrics such as block-averaged RMSD with errors, replica-to-replica variability, and overlap of sampled conformational space between replicas. Consider extending simulations or using enhanced sampling if convergence is not achieved.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Free energy methodology
- **Claim pointer** "MM/PBSA calculations in state III revealed that energetic differences were already encoded prior to DNA translocation" and "ΔΔG post–pre" values
- **Evidence pointer** Materials and Methods, MM/PBSA Free Energy Calculations; Tables S2–S3
- **Concern** The MM/PBSA approach is used to estimate binding free energies, but the manuscript acknowledges that entropic contributions are not included. This is a significant limitation, as entropy can be a major contributor to binding free energy differences, especially for mutations that alter flexibility (which the authors themselves report). The text also does not report the number of snapshots used, the convergence of the MM/PBSA estimates, or the dielectric constants and other parameters used. The reported values have very small errors (±1–2 kcal/mol), which seems optimistic for MM/PBSA without entropy. The interpretation of "semi-quantitative" is appropriate, but the conclusions drawn from these values are too strong.
- **Why it matters** The energetic analysis is a key pillar of the proposed framework. If the free energy estimates are unreliable, the conclusions about altered binding energetics are not supported.
- **Resolution test** Report full MM/PBSA parameters, number of snapshots, and convergence of estimates. Consider including entropic contributions or at least discussing their potential impact. Reduce the strength of claims based on MM/PBSA results.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison to experimental data
- **Claim pointer** "we analyzed how a selected set of 8 Polη mutations perturbs its structure, DNA binding, and substrate translocation, thereby altering Polη function"
- **Evidence pointer** Introduction; Discussion
- **Concern** The manuscript does not compare simulation predictions to any experimental data on these specific mutants, beyond noting their clinical pathogenicity. There are published biochemical and structural studies on some Polη mutants that could provide validation or contrast. The authors mention "recent structural and clinical data" but do not specify how their simulations relate to or explain these data. For example, do the predicted changes in DNA binding correlate with experimentally measured polymerase activity or processivity?
- **Why it matters** Without experimental comparison, the biological relevance of the simulation findings remains speculative. The manuscript would be substantially strengthened by explicit discussion of how the simulations explain or predict experimental observations.
- **Resolution test** Add a section comparing simulation predictions to available experimental data on these mutants (e.g., activity assays, binding measurements). If no direct data exist, discuss the relationship to related mutants or experimental systems.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Statistical treatment
- **Claim pointer** "we found that all contributed to reducing DNA anchoring to Polη" and "a striking convergence across XP-V variants"
- **Evidence pointer** Results, Common Features Measurement; Figures 3–4
- **Concern** The contact analysis identifies residues with "decreased" or "increased" contact frequency relative to WT, but no statistical significance is reported. The threshold of 5% change appears arbitrary. The claim that residues are affected in "at least 7 of 8" mutants is descriptive but not statistically evaluated. What is the probability of observing such overlap by chance? A permutation test or similar approach is needed.
- **Why it matters** The convergence claim is the core finding. Without statistical support, the "striking convergence" could be coincidental.
- **Resolution test** Perform permutation testing or bootstrapping to assess the statistical significance of the overlap in affected residues across mutants. Report effect sizes and confidence intervals.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "we found that all contributed to reducing DNA anchoring to Polη" but does not specify the magnitude or significance of this effect. The term "unified mechanistic framework" is used without defining what constitutes a framework.
- **Required correction** Provide a more specific summary of the findings, including quantitative measures where possible, and define what is meant by "unified mechanistic framework."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, State III section
- **Evidence pointer** Results, "Local Mutations Destabilize..."
- **Issue** The text mentions "the catalytic triad in the WT system retained the ability to capture and coordinate sodium ions from the bulk" but does not report the occupancy or residence time of these ions. This is relevant to the claim of impaired ion coordination in mutants.
- **Required correction** Report ion occupancy or coordination numbers for WT and mutants to support the claim of impaired ion coordination.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results, State IV section
- **Evidence pointer** Results, "Mutations Lead to Persistent..."
- **Issue** The text states "most mutants appeared more stable than in state III" but does not define what "stable" means in this context. Is this based on RMSD, radius of gyration, or other metrics?
- **Required correction** Define the stability metric used and report the corresponding values.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion, paragraph on thumb mutations
- **Issue** The discussion of thumb mutations states they "primarily affect the mechanical transmission of conformational changes" but does not explain how this conclusion follows from the contact and fluctuation analyses.
- **Required correction** Provide a more explicit link between the observed data and the proposed mechanical role of the thumb subdomain.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Materials and Methods, MM/PBSA
- **Evidence pointer** Materials and Methods, MM/PBSA Free Energy Calculations
- **Issue** The MM/PBSA section does not report the internal dielectric constant, solute dielectric, or the number of snapshots used. These parameters significantly affect the results.
- **Required correction** Report all MM/PBSA parameters and the number of snapshots used.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion, comparison to Polκ
- **Evidence pointer** Discussion, final paragraph
- **Issue** The comparison to Polκ is brief and does not specify the structural basis for the analogous positions or the significance of the conservation.
- **Required correction** Provide a more detailed comparison, including sequence or structural alignment information.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Throughout
- **Evidence pointer** Various
- **Issue** The manuscript uses terms like "semi-quantitative" and "qualitative correlation" without defining what these mean in the context of the analyses.
- **Required correction** Define these terms and specify the criteria used for qualitative vs. quantitative assessments.

## Risk / unsupported claims
- The "unified mechanistic framework" is not quantitatively established; the reported ΔΔG values span a wide range and no statistical test of convergence is provided
- The claim that all eight mutations "reduce DNA anchoring" is based on qualitative contact analysis without statistical significance testing
- The MM/PBSA free energy differences are presented with very small errors (±1–2 kcal/mol) despite the acknowledged omission of entropic contributions, which is likely an underestimate of uncertainty
- The claim that mutations "differentially reshape the energetic profile" of translocation is based on ΔΔG post–pre values that are not tested for significance
- The comparison to Polκ is presented without sufficient detail to evaluate its validity
- The biological relevance of the findings is not connected to experimental data on these specific mutants
- The convergence of mutational effects across eight mutants is described as "striking" but no statistical measure of this convergence is provided
- The claim that Ala117Pro and Thr122Pro "retained much of the local active-site geometry" is based on distance measurements that are not statistically compared between WT and mutants