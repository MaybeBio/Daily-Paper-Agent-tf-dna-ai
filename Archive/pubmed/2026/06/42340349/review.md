## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results and discussion, conclusions, and supplementary material references.
- **Assessment boundary** Evaluation of methodological soundness, validity of conclusions relative to presented evidence, and clarity of reporting. No assessment of experimental data beyond what is provided in the manuscript.
- **Shared manuscript claim summary** The authors compare GaMD, metadynamics, and weighted ensemble simulations against unbiased MD for sampling the conformational space of the intrinsically disordered β-catenin17–48 peptide in nonphosphorylated and phosphorylated states. They report that the methods explore complementary regions of conformational space, that GaMD largely overlaps with unbiased MD, that metadynamics and WESTPA access novel regions, that intermediate conformations connecting the two phosphorylation states are identified primarily by adaptive methods, and that Ser33/Ser37 ϕ-angle collective variables are more effective than end-to-end distance for capturing phosphorylation-dependent conformational changes. Agreement with NMR observables is reported as broadly similar across methods.
- **Visible evidence base** Abstract, introduction, methods, results and discussion, conclusions, and references to supplementary figures and tables. No supplementary material content was provided for direct inspection.
- **Missing materials affecting confidence** Supplementary figures S1–S9 and tables S1–S2 are referenced but not included. These contain convergence assessments, free-energy surfaces, time series of collective variables, cluster analysis details, and NMR observable comparisons. Without these, quantitative validation of several claims is not possible.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and relevant question in the simulation of intrinsically disordered proteins, namely the comparative performance of enhanced sampling methods. The study design is logical and the choice of a biologically relevant peptide with a known phosphorylation-dependent conformational change provides a useful test case. However, the conclusions are drawn from a limited set of simulations without clear evidence of convergence or statistical robustness. The reliance on unweighted ensembles for comparative analysis, while acknowledged, limits the interpretability of the results. The claim that intermediate conformations are identified is suggestive but not rigorously supported by the presented evidence. The manuscript would benefit from additional analysis and clearer reporting of uncertainties.
- **Who would be interested in the results, and why** Computational biophysicists and chemists working on intrinsically disordered proteins, developers and users of enhanced sampling methods, and researchers studying phosphorylation-dependent conformational changes. The comparative nature of the study provides practical guidance for method selection, which is of broad interest to the molecular simulation community.
- **Major strengths** The study addresses a gap in systematic comparisons of enhanced sampling methods for IDPs. The use of a biologically relevant system with experimental structural data provides a meaningful benchmark. The inclusion of multiple methods and collective variables allows for a nuanced discussion of method-dependent behavior. The analysis of intermediate conformations is an interesting and potentially valuable contribution.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria** Originality: The question of comparative method performance for IDPs is not entirely new, but the specific system and combination of methods provide a useful contribution. Scientific importance: The findings have practical implications for method selection in IDP simulations, which is relevant to a broad community. Interdisciplinary readership: The topic is of interest to computational chemists, biophysicists, and structural biologists, though the technical focus may limit appeal to a wider audience. Technical soundness: The simulation protocols are generally sound, but the lack of convergence analysis and statistical treatment weakens the technical foundation. Readability for nonspecialists: The manuscript is clearly written and accessible, though some technical details may be challenging for non-experts.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding convergence assessment, statistical robustness, and clarification of the intermediate conformation claims.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the enhanced sampling methods explored complementary regions of conformational space rather than converging to a single ensemble, and that this reflects genuine differences in sampling behavior.
- **Evidence pointer** Results and Discussion, Figures 1 and 2, Figures S1–S4
- **Concern** The comparison of conformational ensembles is based on unweighted configurations from each method. The authors acknowledge this, but the interpretation of the results as reflecting method-specific sampling behavior is problematic. Without reweighting, the observed differences could reflect the degree of convergence rather than the equilibrium properties of the system. The convergence assessments referenced in Figures S1–S4 are not provided, so it is impossible to evaluate whether the simulations have reached a stationary distribution.
- **Why it matters** The central conclusion of the paper, that different methods explore different regions of conformational space, depends on the assumption that the simulations are sufficiently converged. If the simulations are not converged, the observed differences may be artifacts of insufficient sampling rather than genuine method-dependent behavior.
- **Resolution test** Provide the convergence data from Figures S1–S4, including free-energy surfaces at different time intervals and collective variable time series. Demonstrate that the qualitative features of the ensembles are stable over the latter half of the simulations. If possible, perform reweighting of the enhanced sampling data and compare the reweighted ensembles with the unweighted ones to assess the impact of the bias.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical robustness
- **Claim pointer** The authors claim that metadynamics and WESTPA more readily accessed conformational regions not observed in unbiased simulations, and that these methods identified intermediate conformations connecting the two phosphorylation states.
- **Evidence pointer** Results and Discussion, Figures 3 and 4, Figure S9
- **Concern** The identification of intermediate conformations is based on cluster analysis of the combined trajectories. The manuscript does not report any statistical measures of uncertainty, such as confidence intervals or bootstrapping, for the cluster assignments or the proportions of each method within each cluster. The claim that certain clusters represent intermediates is based on visual inspection of cluster centers and helicity values, which is subjective. The small number of simulations (one per method per state) provides no basis for assessing run-to-run variability.
- **Why it matters** The claim that adaptive methods can capture biologically relevant intermediate states is a key finding of the paper. If this claim is not statistically robust, it cannot be considered established. The lack of replicate simulations is a significant limitation.
- **Resolution test** Provide replicate simulations for at least one method and state to assess variability. Report the uncertainty in cluster compositions, for example through bootstrapping of the cluster assignments. Clearly define the criteria for classifying a cluster as an intermediate and apply them consistently.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the Ser33/Ser37 ϕ-angle collective variable more effectively captures phosphorylation-dependent conformational shifts than the end-to-end distance.
- **Evidence pointer** Results and Discussion, Figures 3 and 4, Figures S2–S4
- **Concern** The comparison of the two collective variables is based on the observation that the ϕ-angle CV led to cross-sampling between phosphorylation states, while the end-to-end distance did not. However, the two collective variables are fundamentally different in nature, and the choice of CV is known to affect the efficiency of enhanced sampling. The conclusion that ϕ-angles are more effective may be specific to this system and these simulation parameters. The manuscript does not provide a quantitative comparison of the sampling efficiency or the quality of the resulting ensembles for the two CVs.
- **Why it matters** The claim that local dihedral angles are more effective collective variables for capturing phosphorylation-dependent changes is potentially useful for future studies. However, without a more rigorous comparison, this conclusion is not well supported.
- **Resolution test** Provide a quantitative comparison of the two CVs, for example by measuring the overlap of the sampled distributions with the experimental ensembles, or by computing the convergence rate of the free-energy surfaces. Discuss the physical rationale for why ϕ-angles might be more sensitive to phosphorylation in this system.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that all methods produced conformational ensembles that are broadly consistent with available NMR observables, with WESTPA yielding slightly better agreement.
- **Evidence pointer** Results and Discussion, Figure 5, Tables S1 and S2
- **Concern** The comparison to NMR observables is based on ensemble averages over the sampled configurations without reweighting. For the enhanced sampling methods, this is not a valid comparison to equilibrium experimental data, as the sampled distributions are biased. The authors acknowledge this, but the interpretation of the results as indicating accuracy is problematic. The reported differences in RMSE between methods are small, and no uncertainty estimates are provided.
- **Why it matters** The validation against experimental data is an important part of the study. If the comparison is not performed correctly, the conclusions about the accuracy of the methods are not reliable.
- **Resolution test** Perform reweighting of the enhanced sampling ensembles before computing the NMR observables. Report the uncertainty in the calculated observables, for example through block averaging or bootstrapping. Discuss the limitations of comparing biased ensembles to experimental data.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors describe the simulation protocols for each method, but the level of detail is insufficient for reproduction.
- **Evidence pointer** Methods section
- **Concern** The manuscript does not provide specific parameters for the GaMD simulations, such as the threshold energy and the harmonic force constant, nor the well-tempered metadynamics bias factor and deposition interval. The number of WESTPA walkers and the binning scheme are described, but the total simulation time per walker is not clearly stated. The force field parameters for the phosphorylated residues are not described in detail.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without complete parameter details, other researchers cannot replicate the simulations or build upon the findings.
- **Resolution test** Provide a complete description of all simulation parameters, either in the main text or in the supplementary material. Include the specific versions of all software packages used.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that "different enhanced sampling methods explored distinct regions of conformational space rather than converging to a single ensemble," but this is presented without qualification. The abstract would benefit from a brief mention of the limitations of this finding, such as the lack of replicate simulations.
- **Required correction** Add a sentence acknowledging the need for further validation with replicate simulations or longer timescales.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, System Setup
- **Evidence pointer** Methods, System Setup
- **Issue** The description of the Drude-2019 polarizable force field conversion states that "recently developed patches were applied to the relevant residues to create the dianionic form of the phosphorylated amino acids." The specific patches are not referenced or described.
- **Required correction** Provide a reference for the patches or describe them in sufficient detail for reproduction.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results and Discussion, Comparison of Conformational Ensembles
- **Evidence pointer** Results and Discussion, Comparison of Conformational Ensembles
- **Issue** The discussion of why GaMD largely overlaps with unbiased MD is brief. The authors state that GaMD "primarily enhances barrier crossing," but this is not elaborated in the context of IDP energy landscapes.
- **Required correction** Expand the discussion to explain the physical basis for the observed behavior, with reference to the relevant literature.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results and Discussion, Impact of Phosphorylation
- **Evidence pointer** Results and Discussion, Impact of Phosphorylation
- **Issue** The statement that "the two phosphorylation states are completely separated when end-to-end distance is used as the CV" is strong, but the figure is not provided in the main text. The reader must refer to the supplementary material.
- **Required correction** Consider including the relevant figure in the main text or providing a more detailed description of the separation in the text.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Conclusions
- **Evidence pointer** Conclusions
- **Issue** The conclusion states that "the choice of collective variable was found to strongly influence sampling behavior," but this is based on a single system. The generality of this finding is not discussed.
- **Required correction** Add a sentence acknowledging that the findings may be system-specific and that further studies on different IDPs are needed.

## Risk / unsupported claims
- The claim that intermediate conformations connecting the nonphosphorylated and phosphorylated states are identified is not rigorously supported. The identification relies on cluster analysis of unweighted ensembles from single simulations, with no statistical validation.
- The claim that the Ser33/Ser37 ϕ-angle collective variable is more effective than end-to-end distance is based on qualitative observations from a single system and may not be generalizable.
- The comparison of simulated ensembles to NMR observables without reweighting of the enhanced sampling data is not a valid test of equilibrium accuracy, and the reported agreement may be misleading.
- The convergence of the simulations is not demonstrated in the provided material. All claims about the extent of conformational sampling are contingent on the simulations being sufficiently converged, which cannot be assessed from the manuscript alone.