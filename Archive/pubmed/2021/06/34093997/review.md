## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and figure captions. Supplementary figures referenced but not provided.
- **Assessment boundary** Scientific content, methodological soundness, interpretation of results, and alignment with stated claims. Not assessed: language editing, formatting, or bibliographic completeness beyond what affects reproducibility.
- **Shared manuscript claim summary** The authors use all-atom molecular dynamics (MD) simulations and a machine learning (PCA-based) post-analysis to compare the structural and dynamic behavior of the bacterial DNA glycosylase MutM bound to a 13-bp DNA duplex containing either a single 8-oxoguanine (8-oxoG) lesion or a tandem lesion consisting of 8-oxoG plus an adjacent abasic site (Ap). They report that the tandem lesion perturbs the canonical interaction network around 8-oxoG, particularly the intercalation triad (M77, R112, F114), induces local DNA deformations that bring the lesion site closer to canonical B-DNA, and results in a more rigid MutM:DNA complex, which they propose contributes to reduced repair efficiency.
- **Visible evidence base** Main text figures (Figures 1–5), Table 1, and referenced supplementary figures (S1–S13) which are not included in the provided material. Methods section describes simulation protocols and the machine learning approach.
- **Missing materials affecting confidence** Supplementary figures S1–S13, including distributions of distances, puckering analyses, RMSD plots, and clustering results, are referenced but not provided. The machine learning "importance" score definition and threshold justification are only partially described. No error analysis or convergence assessment beyond RMSD is shown. The exact command lines or input files for reproducibility are not provided.

## Reviewer
- **Overall assessment** This manuscript addresses a relevant and under-explored question: how the presence of a tandem lesion (8-oxoG + Ap) alters the recognition dynamics of MutM compared to a single 8-oxoG lesion. The combination of long-timescale MD simulations (2 × 1 μs) with a PCA-based machine learning analysis is a modern and potentially powerful approach. The authors identify specific structural and dynamic changes, including a shift in the intercalation triad and altered DNA backbone parameters, that are plausible and mechanistically interesting. However, the manuscript has several weaknesses that currently prevent the case from being fully established. The machine learning analysis is presented as a key novelty but its validation, interpretability, and added value over direct geometric analysis are not sufficiently demonstrated. The statistical treatment of the MD data is limited, with no block averaging or convergence assessment for the reported averages. The link between the observed structural changes and the claimed reduction in repair efficiency is inferential and not directly tested. The manuscript is clearly written and the figures are informative, but the evidence base is incomplete without the supplementary material.
- **Who would be interested in the results, and why** Researchers in the fields of DNA repair, specifically base excision repair (BER) and glycosylase mechanism; computational biochemists and biophysicists studying protein-DNA interactions; and method developers interested in applying machine learning to molecular dynamics trajectories. The findings may also be of interest to radiation biologists studying clustered DNA damage, as the tandem lesion modeled here is a relevant radiation-induced lesion.
- **Major strengths**
  1. The biological question is important and timely: understanding why tandem lesions are poorly repaired is clinically relevant.
  2. The use of long (1 μs) MD simulations with two replicas is a significant computational effort and appropriate for the system size.
  3. The combination of MD with a machine learning post-analysis is a modern approach that could provide new insights if properly validated.
  4. The authors identify specific, testable structural changes (e.g., R76 reorientation, altered intercalation triad dynamics, DNA parameter shifts) that provide a mechanistic hypothesis for reduced repair.
  5. The manuscript is generally well-written and the main figures are clear and support the qualitative claims.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that the PCA-based machine learning analysis provides a "footprint" of residues important for MutM:DNA bonding and that this analysis identifies changes in interaction patterns between single and tandem lesion systems.
  - **Evidence pointer** Results section "Systematic assessment of interacting residues through machine-learning protocol"; Figure 4; Methods section "Machine-learning post-analysis"
  - **Concern** The machine learning analysis is a central pillar of the manuscript, but its implementation and validation are insufficiently described. The "importance" score is not formally defined in the main text. The threshold of 0.04 is presented without justification. The authors state that a supervised approach was attempted but was "not discriminative enough," yet no details are given. Most critically, the added value of the PCA-based method over a direct geometric analysis of interatomic distances is not demonstrated. The authors do not show that the method recovers known interactions (beyond a qualitative statement) or that it is sensitive to the perturbations they describe. Without a clear definition, validation, and comparison to simpler metrics, the reader cannot assess whether the "importance" scores are meaningful or an artifact of the method.
  - **Why it matters** The machine learning component is presented as a novel contribution. If the method is not rigorously validated, the central claim of the paper is weakened. The authors need to demonstrate that the method provides reliable and interpretable information that is not readily available from standard distance or contact analysis.
  - **Resolution test** Provide a formal definition of the importance score, including the exact input features and the mathematical transformation used. Justify the threshold choice, possibly with a sensitivity analysis. Validate the method by showing it recovers known MutM-DNA contacts in the singly-damaged system. Compare the importance scores to simple contact frequencies or average distances to show added value. If the supervised approach was attempted, describe it and explain why it failed.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors report quantitative values for structural parameters (e.g., distances, angles, percentages of simulation time) and state that these differ between single and tandem lesion systems.
  - **Evidence pointer** Results sections "Tandem lesions impact the interaction network around 8-oxoG" and "Mechanical and dynamic properties of the DNA strand"; Table 1; Figures 3 and 5
  - **Concern** The manuscript reports averages and standard errors for various structural parameters (e.g., F114-dG20 distance, R76-dC7 distance, bend angles, base-pair parameters) but provides no statistical analysis to support the claim that the observed differences between single and tandem systems are significant. The standard errors reported are extremely small (e.g., 5.35 ± 0.01 Å), which is surprising for a highly flexible protein-DNA interface over 1 μs. No block averaging, bootstrapping, or other convergence assessment is described. The two replicas are mentioned but not analyzed separately or used to assess reproducibility. Without a proper error analysis, the reader cannot determine whether the reported differences are robust or within noise.
  - **Why it matters** The central claim of the paper is that the tandem lesion perturbs the interaction network and DNA structure. If the differences are not statistically significant, the conclusion is not supported. The extremely small standard errors suggest possible underestimation of uncertainty, which could mislead readers.
  - **Resolution test** Perform a block average analysis to estimate the statistical error of the reported quantities. Report the results for each replica separately and assess whether the observed differences are consistent across replicas. Use a statistical test (e.g., a two-sample test on block-averaged data) to assess significance. If the standard errors are indeed as small as reported, explain why the system is so rigid over 1 μs.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors state that the observed structural changes "contribute to ultimately diminish the recognition efficiency" and that the tandem lesion results in a "more rigid complex" that is "counterproductive for repair."
  - **Evidence pointer** Discussion section; Results section "Tandem lesions impact the interaction network around 8-oxoG"
  - **Concern** The link between the observed structural changes and the functional outcome (reduced repair efficiency) is purely inferential. The authors do not measure or compute any free energy barriers for lesion extrusion, nor do they compare their results to experimental data on repair rates for tandem vs. single lesions. The claim that increased rigidity leads to reduced repair is plausible but not directly supported by the data presented. The authors also do not discuss alternative explanations, such as the possibility that the observed changes are functionally neutral or even beneficial in some contexts.
  - **Why it matters** The functional interpretation is the main biological takeaway of the paper. If the link is not established, the significance of the structural findings is diminished.
  - **Resolution test** Either (a) compute a free energy profile for 8-oxoG extrusion in both systems to directly test the effect of the tandem lesion, or (b) clearly frame the results as a structural hypothesis and discuss what experiments would be needed to test it. If experimental data on repair rates exist, cite and compare.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors state that the Ap site was modeled as an alpha anomer and that the Q166C mutation was conserved from the crystal structure.
  - **Evidence pointer** Methods section "All-atom molecular dynamics simulations"
  - **Concern** The choice of the alpha anomer for the Ap site is not justified. Ap sites are known to exist in equilibrium between alpha and beta anomers, and the anomeric form can affect the structural dynamics. The authors do not discuss this choice or its potential impact on their results. Additionally, the Q166C mutation is mentioned but its potential effect on MutM function or dynamics is not discussed. The authors state that the mutation should have a "shy impact" but do not provide evidence for this claim.
  - **Why it matters** The simulation results depend on the accuracy of the model. If the anomeric form is not representative of the biologically relevant state, the conclusions may not be transferable to the in vivo situation. The Q166C mutation could alter protein dynamics in ways that affect the interpretation.
  - **Resolution test** Justify the choice of the alpha anomer with references or a sensitivity analysis. Discuss the potential impact of the Q166C mutation on the results, or use a wild-type structure if available.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods section "All-atom molecular dynamics simulations"
  - **Evidence pointer** Methods section
  - **Issue** The methods section does not specify the number of water molecules, the exact ion placement protocol, or the equilibration criteria. The temperature coupling and pressure coupling algorithms are not described in detail.
  - **Required correction** Provide a more detailed description of the simulation setup, including the number of water molecules, the ion placement method, and the equilibration protocol. Specify the barostat and thermostat settings.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Results section "Tandem lesions impact the interaction network around 8-oxoG"
  - **Evidence pointer** Figure 3
  - **Issue** The figure caption for Figure 3 does not specify which distances are plotted. The text mentions "distances involving the intercalation triad (A) and R76 (B)" but the exact atom pairs are not defined in the caption or the text.
  - **Required correction** Define the specific atom pairs or atom groups used for each distance in the figure caption or in the text.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Results section "Mechanical and dynamic properties of the DNA strand"
  - **Evidence pointer** Table 1
  - **Issue** The authors report that the global bending angle is 51.55 ± 0.34° for the single lesion and 49.12 ± 38° for the tandem lesion. The standard error for the tandem lesion appears to be a typo (38° is implausibly large). This needs correction.
  - **Required correction** Correct the standard error value for the tandem lesion global bending angle.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Results section "Systematic assessment of interacting residues through machine-learning protocol"
  - **Evidence pointer** Figure 4
  - **Issue** The authors state that 47 and 61 residues are above the threshold for single and tandem systems, respectively, but do not provide a list or a detailed comparison of which residues change most significantly. The reader cannot assess which specific residues drive the reported differences.
  - **Required correction** Provide a table or supplementary figure listing the residues above the threshold in each system and highlighting those with the largest changes in importance score.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods section "Machine-learning post-analysis"
  - **Evidence pointer** Methods section
  - **Issue** The description of the PCA-based method is brief. The authors do not specify how the input distance matrix was constructed (e.g., which atom pairs, how many frames, how the matrix was normalized).
  - **Required correction** Provide a more detailed description of the input features, the construction of the covariance matrix, and the interpretation of the importance scores.

## Risk / unsupported claims
- The claim that the tandem lesion "contributes to ultimately diminish the recognition efficiency" is not directly supported by the data; it is an inference from structural observations.
- The claim that the PCA-based machine learning analysis provides a reliable "footprint" of important residues is not validated; the method's definition and added value are not established.
- The claim that the tandem lesion results in a "more rigid complex" is based on limited geometric analysis and lacks statistical support.
- The statement that the Q166C mutation has a "shy impact" is not supported by any data or reference.
- The choice of the alpha anomer for the Ap site is not justified, and its potential impact on the results is not discussed.
- The reported standard error for the tandem lesion global bending angle (49.12 ± 38°) appears erroneous and undermines confidence in the quantitative reporting.