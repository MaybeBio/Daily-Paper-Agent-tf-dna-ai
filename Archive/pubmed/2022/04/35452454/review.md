## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results and discussion, conclusions, methods, and supporting information references.
- **Assessment boundary** Scientific claims, methodological soundness, evidence consistency, and alignment with the stated hypothesis. No assessment of editorial fit or publication decision.
- **Shared manuscript claim summary** The authors propose that allostery in the KIX domain arises from changes in the distribution of minor conformational micro-states, with binding partners selecting distinct states and modulating conformational entropy, primarily through the L12-G2 loop. They support this with MD simulations, clustering, methyl order parameters, and DSF experiments.
- **Visible evidence base** Main text figures (Figs 1–5, 7, 8), tables (Table 1), methods descriptions, and references to supporting information (S1–S8 Figs). No raw data, simulation trajectories, or experimental replicates are provided.
- **Missing materials affecting confidence** Raw simulation data, convergence metrics, force field parameters, clustering validation details, DSF raw curves, replicate numbers, and statistical analyses are not provided. The supporting information is referenced but not included in the supplied material.

## Reviewer
- **Overall assessment** The manuscript presents a plausible and mechanistically interesting hypothesis, supported by a combination of computational and experimental approaches. The central claim that allostery in KIX is mediated by reweighting of minor conformational micro-states is consistent with the data shown, but the evidence is largely qualitative and lacks quantitative rigor. The DSF experiments are used to infer entropic changes, but the connection is indirect and not fully validated. The manuscript would benefit from clearer statistical treatment, convergence analysis, and a more direct link between simulation and experiment.
- **Who would be interested in the results, and why** Researchers in the fields of allostery, intrinsically disordered proteins, transcriptional regulation, and molecular recognition. The work is also relevant to those interested in the development of allosteric modulators targeting dynamic protein domains, as it suggests that loop-targeting compounds could be used to tune binding.
- **Major strengths** The study addresses a fundamental question about the microscopic origins of allostery in a dynamic protein. The combination of MD simulations, clustering, order parameters, and DSF provides a multi-pronged approach. The identification of the L12-G2 loop as a key dynamic element is well supported and mechanistically plausible. The use of a small molecule and a mutant to perturb the system adds functional relevance.
- **Major Concerns** The concerns are listed below.
- **Minor Comments** The minor comments are listed below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria** Originality is moderate; the ensemble view of allostery is not new, but the specific application to KIX with a focus on minor micro-states is a useful contribution. Scientific importance is significant for the transcriptional regulation and allostery communities. Interdisciplinary readership is plausible, as the work bridges computational biophysics and experimental biochemistry. Technical soundness is currently insufficient due to missing convergence and statistical analyses. Readability for nonspecialists is acceptable, though some sections assume familiarity with MD and entropy concepts.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding simulation convergence, statistical treatment, and the interpretation of DSF data.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that MD simulations reveal a reduction in the number of KIX micro-states upon binding, and that this reduction is linked to allostery.
- **Evidence pointer** Results section, Figs 2–5; Methods, "Constructing and analyzing the KIX complexes for MD"
- **Concern** The clustering analysis is used to define micro-states and their populations, but no convergence analysis is provided. It is unclear whether the simulations have sampled the conformational space sufficiently to support the claim that the observed distributions are representative. Without convergence metrics (e.g., cluster population stability over time, multiple independent runs), the distributions may be artifacts of insufficient sampling.
- **Why it matters** The central conclusion that binding reduces the number of accessible micro-states depends entirely on the reliability of the clustering. If the simulations are not converged, the observed differences between apo and bound states could be due to sampling noise rather than genuine changes in the conformational ensemble.
- **Resolution test** Provide evidence of convergence, such as time evolution of cluster populations, replicate simulations with consistent results, or comparison to experimental data (e.g., NMR relaxation or residual dipolar couplings) that validate the simulated ensembles.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that methyl order parameters from simulation are used to calculate conformational entropy changes, and that these correlate with clustering-based entropy estimates.
- **Evidence pointer** Results, "Conformational entropy changes can be masked in macroscopic measurements"; Methods, Eq 1; S2 Fig
- **Concern** The relationship between methyl order parameters and conformational entropy is based on an empirical equation (Eq 1) that was derived for a specific set of proteins. The authors do not validate this equation for KIX, nor do they compare their computed order parameters to experimental NMR-derived values. The correlation shown in S2 Fig is mentioned but not quantified or statistically tested.
- **Why it matters** The quantitative entropy values are used to support the mechanistic model. If the empirical relationship is not valid for KIX, the reported entropy changes could be inaccurate, undermining the conclusion that MLL binding "prepays" an entropic cost.
- **Resolution test** Compare simulated methyl order parameters to experimental NMR data for KIX (if available) or provide a validation of Eq 1 for this system. Report the correlation coefficient and statistical significance for the S2 Fig comparison.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors use DSF to infer relative entropic changes across complexes, and compare these to computed entropy changes.
- **Evidence pointer** Results, "Conformational entropy changes can be masked in macroscopic measurements"; Methods, "Differential scanning fluorimetry"; Fig 4B, Fig 5B–5C
- **Concern** DSF measures thermal stability (Tm), which is a global thermodynamic property influenced by enthalpy, entropy, and solvation effects. The authors interpret changes in Tm as reflecting conformational entropy changes in KIX, but this is an indirect inference. No control experiments are shown to isolate the contribution of KIX conformational entropy from other factors, such as peptide folding or solvent effects. Additionally, the DSF data are presented without error bars or replicate information.
- **Why it matters** The comparison between DSF-derived stability changes and simulation-derived entropy changes is a key part of the argument. If the DSF data are not reproducible or if the interpretation is confounded, the link between experiment and simulation is weakened.
- **Resolution test** Provide replicate DSF measurements with standard deviations, and include control experiments (e.g., with a non-binding peptide or a mutant that does not affect the loop) to demonstrate that the Tm changes are specifically due to KIX conformational entropy.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that the L12-G2 loop dynamics dictate KIX conformational entropy changes, and that this could be targeted by small molecules.
- **Evidence pointer** Results, "L12-G2 loop dynamics dictate KIX conformational entropy changes"; Fig 7, Fig 8
- **Concern** The correlation between loop dynamics and entropy is based on RMSF and order parameter analysis, but the causal claim is not directly tested. The authors do not perform mutations or perturbations specifically targeting the loop to demonstrate that altering loop dynamics changes allostery. The I660V mutation is discussed, but its effect on the loop is not quantitatively linked to the observed changes in binding.
- **Why it matters** The claim that the loop is a key allosteric regulator has implications for drug design. Without direct evidence that loop dynamics are causally linked to allostery, the suggestion that loop-targeting compounds could be developed remains speculative.
- **Resolution test** Perform simulations or experiments with loop mutations that alter flexibility and measure the effect on binding cooperativity. Alternatively, use enhanced sampling or perturbation methods to show that loop dynamics directly modulate the binding affinity of the second ligand.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that the I660V mutation "turns on" allostery in the pKID system and that this is due to a reduction in conformational entropy.
- **Evidence pointer** Results, "KIX adopts a diminishing number of micro-states as substrates bind"; Fig 4
- **Concern** The claim that I660V enhances pKID binding is based on DSF data, but the mechanistic link to conformational entropy is not fully established. The clustering analysis for the mutant is mentioned but not shown in detail, and the entropy change for the mutant is not quantified in the same way as for the wild-type systems.
- **Why it matters** The mutant is used as a key piece of evidence for the entropic model. If the mutant's effect is not clearly shown to be due to changes in micro-state distribution, the model is not fully supported.
- **Resolution test** Provide a detailed comparison of the micro-state distributions for KIXI660V versus wild-type, including entropy values and a statistical test of the difference. Also, show that the enhanced pKID binding is specifically due to the reduced conformational entropy, not other effects of the mutation.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, "location not provided"
- **Issue** The abstract states that "allostery is maximized with MLL pre-binding," but the term "maximized" is vague. It is unclear whether this refers to the magnitude of the entropic change, the cooperativity, or the effect on binding affinity.
- **Required correction** Clarify what is meant by "maximized" and provide a quantitative definition or reference to the relevant figure.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "Constructing and analyzing the KIX complexes for MD"
- **Evidence pointer** Methods, "location not provided"
- **Issue** The clustering cutoff is described as 2.5 Å RMSD on Cα atoms, but the number of clusters (W) is not reported for each system. The choice of K in K-means clustering is not justified.
- **Required correction** Report the number of clusters for each system and describe how the optimal K was determined (e.g., elbow method, silhouette score).

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results, "Conformational entropy changes can be masked in macroscopic measurements"
- **Evidence pointer** Fig 6, "location not provided"
- **Issue** The comparison between ITC-derived total entropy and simulation-derived conformational entropy is presented as a trend, but no statistical analysis is shown. It is unclear if the differences are significant.
- **Required correction** Add error bars or confidence intervals to the data points in Fig 6 and perform a statistical test (e.g., t-test or ANOVA) to support the claimed trends.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "KIX adopts a diminishing number of micro-states as substrates bind"
- **Evidence pointer** Fig 3, "location not provided"
- **Issue** The "coral" and "yellow" micro-states are referenced in the text, but the color coding is not described in the figure legend. This makes it difficult for the reader to follow the argument.
- **Required correction** Add a description of the color coding in the figure legend or in the text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Conclusions
- **Evidence pointer** Conclusions, "location not provided"
- **Issue** The conclusion states that "allostery in turn is a manifestation of this reweighting process," but the term "reweighting" is not defined in the context of the micro-state distributions. It is unclear whether this refers to changes in population, changes in state identity, or both.
- **Required correction** Define "reweighting" explicitly and explain how it relates to the observed changes in micro-state distributions.

## Risk / unsupported claims
- The claim that the L12-G2 loop "dictates" conformational entropy changes is not directly tested and is therefore not fully supported by the evidence.
- The interpretation of DSF data as reflecting conformational entropy changes is indirect and not validated with control experiments.
- The quantitative entropy values derived from Eq 1 are not validated for KIX, and the correlation with clustering-based estimates is not statistically assessed.
- The claim that the I660V mutation "turns on" allostery is based on limited data and lacks a detailed mechanistic analysis.
- The statement that "allostery is maximized with MLL pre-binding" is vague and not quantitatively defined.