## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, figure legends not provided)
- **Assessment boundary** Scientific content, methodological validity, claims vs. evidence, and presentation quality as presented in the supplied text
- **Shared manuscript claim summary** The authors use a deep Markov state model (deep MSM) with a multi-input neural network architecture to analyze a 200 μs MD simulation of the intrinsically disordered measles virus N TAIL binding to the X domain (XD). They identify multiple kinetically distinct encounter complexes and bound states, describe a network of folding-upon-binding pathways, and argue that these pathways are inconsistent with a simple induced fit / conformational selection dichotomy. They also propose that their multi-input neural network approach is a generalizable strategy for modeling IDP conformational dynamics.
- **Visible evidence base** Abstract, Introduction, Results (partial), Discussion, Methods, and references to Supplementary Figures 1–19, Supplementary Tables 1–2, and Figure 1–6 (figure content not provided)
- **Missing materials affecting confidence** Figure panels (Figures 1–6), all Supplementary Figures and Tables, the actual MD trajectory data, code repository contents, and any details of the neural network training curves or validation metrics beyond what is described in the Methods

## Reviewer
- **Overall assessment** This manuscript presents a technically sophisticated application of deep learning-based Markov state modeling to a biologically important IDP binding problem. The central claim that the deep MSM resolves states not captured by a conventional tICA-based HMSM is plausible and potentially valuable. However, the evidence as presented is incomplete: the key figures and supplementary materials are not available for inspection, and several methodological details (e.g., hyperparameter selection, model validation, error estimation) are described but not demonstrated. The biological conclusions, while interesting, rest heavily on the interpretation of states that are not directly visualized. The manuscript is likely to be of interest to the computational biophysics and IDP communities, but the current evidence base is insufficient to fully assess the validity of the claims.
- **Who would be interested in the results, and why** Computational biophysicists and chemists working on IDP binding mechanisms, developers of Markov state models and deep learning methods for molecular simulations, and experimentalists studying measles virus N TAIL /XD interactions or fuzzy complexes more broadly. The methodological advance (multi-input VAMPnet) may also appeal to the machine learning for molecular dynamics community.
- **Major strengths** 1) The study addresses a significant and challenging problem: characterizing the atomic-level mechanisms of IDP folding-upon-binding. 2) The use of a long unbiased MD simulation with multiple binding/unbinding events is a strong foundation. 3) The multi-input neural network architecture is a creative and potentially powerful approach to integrate heterogeneous feature types. 4) The comparison between a conventional HMSM and the deep MSM is a useful demonstration of the limitations of linear dimensionality reduction. 5) The connection to experimental data (NMR, stopped-flow, φ-values, mutations) grounds the simulation findings in prior knowledge.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing validation evidence), R1-M2 (incomplete description of neural network training and architecture), R1-M3 (unclear statistical treatment of deep MSM observables), R1-M4 (overinterpretation of pathway dichotomy without direct flux analysis)
- **Assessment against Nature-style criteria**  
  *Originality*: The application of a multi-input VAMPnet to an IDP binding problem is novel, and the finding of multiple distinct encounter complexes is a meaningful advance over prior single-state descriptions. However, the conceptual framework (fuzzy complexes, encounter complexes) is well established.  
  *Scientific importance*: The results have the potential to inform our understanding of IDP binding mechanisms and the nature of fuzzy complexes, which is a topic of broad interest. The methodological advance could also be impactful.  
  *Interdisciplinary readership*: The topic bridges computational chemistry, biophysics, and molecular biology. The writing is generally accessible, but the Methods section is highly technical and may be challenging for non-specialists.  
  *Technical soundness*: The methodological approach is sound in principle, but the evidence provided is insufficient to verify the technical claims. Key validation steps (CK tests, ITS convergence, error estimates) are mentioned but not shown.  
  *Readability for nonspecialists*: The Introduction and Discussion are well written and accessible. The Results section is dense and would benefit from clearer signposting of the main findings. The Methods section is appropriate for specialists but will be opaque to others.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the biological questions are important, but the manuscript as presented does not provide sufficient evidence to fully establish the claims. The authors should provide the missing figures, supplementary materials, and additional validation details.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The authors claim that the deep MSM resolves states not identified by the tICA HMSM, including two distinct encounter complexes and a kinetic trap, and that these states are kinetically and structurally meaningful.  
- **Evidence pointer** Figures 1–6, Supplementary Figures 1–19, Supplementary Tables 1–2 (not provided)  
- **Concern** The central claims of the manuscript rest on the visualization and quantitative comparison of Markov states (Figures 1, 3–6) and on validation metrics (Supplementary Figures 2, 11). None of these materials are available in the submitted text. Without seeing the free energy surfaces, structural ensembles, transition matrices, and CK test results, it is impossible to evaluate whether the deep MSM states are genuinely distinct, kinetically separated, or biologically meaningful. The authors state that the tICA HMSM failed CK tests, but no data are shown to support this.  
- **Why it matters** The entire scientific case depends on the quality and interpretation of the MSM states. If the states are not well resolved or the model is not validated, the biological conclusions are unsupported.  
- **Resolution test** Provide all figures and supplementary materials. Show CK test results for both the tICA HMSM and the deep MSM at multiple lag times. Show implied timescale plots. Provide structural ensembles or representative conformations for each state, with clear labels and quantitative descriptors (e.g., helix content, contact maps, RMSD distributions).

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Methodological reproducibility  
- **Claim pointer** The authors claim that their multi-input neural network architecture, combining convolutional layers for contact maps and fully connected layers for helical features, is a key innovation that enables the resolution of subtle conformational states.  
- **Evidence pointer** Methods section, Supplementary Figure 10 (not provided)  
- **Concern** The description of the neural network architecture and training procedure is incomplete. The authors do not specify the number of layers, layer widths, activation functions, regularization methods, or the exact procedure for combining the three feature types. The hyperparameter optimization is described but the search space and final values are not given. The training procedure (e.g., loss function, optimizer details, early stopping criteria) is only partially described. The architecture diagram in Supplementary Figure 10 is not available.  
- **Why it matters** Reproducibility is a core requirement for computational studies. Without a complete description of the model architecture and training procedure, other researchers cannot implement or evaluate the method.  
- **Resolution test** Provide a complete description of the neural network architecture, including layer types, sizes, activation functions, and the merging strategy. Report the final hyperparameter values. Provide the architecture diagram. Consider releasing the training code and a minimal example dataset.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical rigor  
- **Claim pointer** The authors report transition probabilities, mean first passage times, and state populations with error estimates (e.g., "2.53 + 0.4%") and claim that differences between states are statistically significant.  
- **Evidence pointer** Results section, Supplementary Figures 8–9, 16–17 (not provided)  
- **Concern** The error estimation procedure for the deep MSM is unclear. The authors state that they trained 30 independent models and aggregated results, but the details of how the error bars are computed (e.g., bootstrap over trajectories, across models, or both) are not fully specified. The reported errors may be underestimated because the same initial unconstrained VAMPnet was used for all 30 constrained training runs, as the authors acknowledge. This could lead to overconfident claims about the separation of states.  
- **Why it matters** The biological conclusions depend on the statistical distinction between states (e.g., the two encounter complexes, the kinetic trap). If the error bars are underestimated, the claims of distinct states may not be robust.  
- **Resolution test** Provide a detailed description of the error estimation procedure. Show the distribution of observables across the 30 training runs. Discuss the potential bias introduced by using a single unconstrained VAMPnet initialization. Consider retraining the unconstrained VAMPnet multiple times to obtain more realistic error estimates.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Interpretational overreach  
- **Claim pointer** The authors conclude that "folding-upon-binding predominantly occurs via two distinct encounter complexes" and that the pathways are "not consistent with canonical conformational selection or induced fit" mechanisms.  
- **Evidence pointer** Results section, Discussion section  
- **Concern** The claim that the observed pathways are inconsistent with induced fit / conformational selection is strong and may be overinterpreted. The authors show that encounter complexes with different helical content converge to similar downstream pathways, but this does not necessarily rule out a conformational selection component, as some pre-formation of helical structure is observed in one encounter complex. The distinction between "induced fit" and "conformational selection" is also somewhat artificial for a disordered protein that samples a broad ensemble. The authors' own data show that the more helical encounter complex (state 7) does not preferentially proceed to the more helical bound states, which is an interesting finding, but the conclusion that this rules out conformational selection is not fully justified.  
- **Why it matters** The conceptual framing of the paper is built around this dichotomy. If the interpretation is too strong, it may mislead readers and overstate the novelty of the findings.  
- **Resolution test** Soften the language or provide a more nuanced discussion of how the data relate to the induced fit / conformational selection framework. Consider performing a more quantitative analysis of pathway fluxes (e.g., using transition path theory) to support the claim that the two encounter complexes converge to the same downstream pathways.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract  
- **Issue** The abstract states that the deep MSM resolves "two distinct encounter complexes" and "a kinetic trap," but the abstract does not mention the tICA HMSM comparison. This makes the novelty of the deep MSM less clear to a reader who only reads the abstract.  
- **Required correction** Briefly mention that the deep MSM provides higher resolution than a conventional HMSM, or state that the deep MSM resolves states not captured by standard approaches.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Results section  
- **Evidence pointer** Results section, "Markov state model input features"  
- **Issue** The term "binary features based on the DSSP secondary structure assignment" is used, but the exact encoding is not described. It is unclear whether each residue is assigned a single binary value (helix vs. non-helix) or whether multiple binary features are used.  
- **Required correction** Clarify the encoding of the DSSP features.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Methods section  
- **Evidence pointer** Methods section, "Neural network training"  
- **Issue** The authors state that they used a 9:1 train-validation split and early stopping, but they do not report the number of training epochs or the final loss values.  
- **Required correction** Provide the number of training epochs and the final training/validation loss values.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Accessibility  
- **Affected element** Discussion section  
- **Evidence pointer** Discussion section  
- **Issue** The discussion of the Sendai virus N TAIL /XD system is interesting but somewhat tangential. It is not clear how directly the comparison applies, given the sequence differences and different experimental conditions.  
- **Required correction** Briefly clarify the relevance of the Sendai comparison and note the limitations of the comparison.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Data availability  
- **Affected element** Data & Code Availability  
- **Evidence pointer** Data & Code Availability  
- **Issue** The MD trajectory is available only by request from D.E. Shaw Research, which may limit reproducibility for researchers who do not have an established relationship with that group.  
- **Required correction** Consider providing at least a subset of the trajectory data (e.g., state representatives or transition counts) as supplementary material to facilitate independent analysis.

## Risk / unsupported claims
- The claim that the deep MSM resolves states not identified by the tICA HMSM is unsupported without the supplementary figures and tables.
- The claim that the observed pathways are inconsistent with induced fit / conformational selection is partially unsupported and may be overstated.
- The claim that the multi-input neural network approach is "generalizable" is speculative and not demonstrated beyond this single system.
- The claim that the kinetic barrier between state 5 and the native-like states is due to stabilization of helical conformations by non-native contacts is plausible but not directly proven; it is inferred from contact populations and transition probabilities.
- The comparison to experimental data (NMR, stopped-flow, φ-values) is qualitative and does not constitute a quantitative validation of the simulation or the MSM.