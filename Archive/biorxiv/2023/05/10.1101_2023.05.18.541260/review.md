## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure captions
- **Assessment boundary** Scientific validity, methodological soundness, interpretation of results, and alignment with claims made in the abstract and main text
- **Shared manuscript claim summary** The authors use residue-level coarse-grained molecular simulations to show that human Nanog forms micelle-like clusters within phase-separated condensates, driven primarily by hydrophobic interactions between tryptophan repeat regions in the C-terminal domain, with electrostatic interactions between N-terminal and DNA-binding domains bridging clusters; tryptophan mutation dissolves condensates, and DNA fragments bind to cluster surfaces and are brought into closer proximity
- **Visible evidence base** Main text figures 1-6, supplementary figures S1-S10, supplementary movie S1, methods section describing simulation protocols and analysis
- **Missing materials affecting confidence** Simulation parameter files, force field validation data, convergence diagnostics beyond those shown, experimental validation data, and details on the initial configuration generation for the uniformly distributed case

## Reviewer
- **Overall assessment** This manuscript presents a computational study of Nanog condensate structure using coarse-grained molecular dynamics simulations. The central claim that Nanog forms micelle-like clusters with a specific domain organization is novel and potentially important for understanding transcription factor condensate function. The simulation methodology is appropriate for the questions asked, and the authors have performed useful control simulations. However, several technical concerns regarding the interpretation of cluster analysis, the treatment of the DNA-binding domain in the model, and the strength of the conclusions drawn from limited sampling need to be addressed. The connection between the simulated structures and experimental observations is plausible but requires more careful articulation.
- **Who would be interested in the results, and why** Researchers studying biomolecular condensates and liquid-liquid phase separation, particularly those focused on transcription factor behavior and transcriptional regulation. The work is also relevant to the computational biophysics community interested in coarse-grained simulation methods for disordered proteins. The proposed micelle-like structural organization of a transcription factor condensate could inform experimental studies of Nanog and related factors.
- **Major strengths** The study addresses an important and timely question about the internal structure of transcription factor condensates. The use of residue-level coarse-grained simulations is appropriate for the length and time scales involved. The authors have performed multiple control simulations to test the robustness of their findings, including variations in salt concentration, the presence of crowders, and the treatment of the DNA-binding domain. The observation that tryptophan-to-alanine mutations disrupt condensate formation is consistent with experimental data and provides a useful validation of the model.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of cluster analysis
  - **Claim pointer** The authors claim that Nanog forms micelle-like clusters within the condensate, with a specific radial organization of domains (CTD at center, DBD in middle, NTD at surface)
  - **Evidence pointer** Figure 3, section "Micelle-like clusters in the Nanog condensate"
  - **Concern** The cluster analysis is based on contacts between WR regions with a cutoff distance of 6.5 Å. The authors define clusters based on these contacts but do not provide a clear justification for this specific definition. More importantly, the claim of a "micelle-like" structure requires demonstrating that the domain organization is a stable, equilibrium feature rather than a transient artifact of the clustering algorithm. The authors show distributions of domain distances from cluster centers, but do not provide a statistical comparison against a null model (e.g., randomly distributed domains within clusters of the same size and shape). Without such a comparison, it is difficult to assess whether the observed radial organization is statistically significant or could arise from the geometric constraints of the cluster analysis itself.
  - **Why it matters** The central structural claim of the paper rests on this analysis. If the micelle-like organization is not robustly demonstrated, the entire interpretive framework of the study is weakened.
  - **Resolution test** The authors should provide a control analysis where domain positions are randomly permuted within clusters of the same size, and show that the observed radial distributions are significantly different from this null model. Alternatively, they could use an independent clustering method (e.g., based on all residue contacts rather than WR-specific contacts) and show that the same structural organization emerges.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Model completeness and interpretation
  - **Claim pointer** The authors state that the DNA-binding domain is not included in the HPS potential and is treated only with structure-based and excluded volume interactions, and they perform a control simulation applying HPS to all residues including DBD
  - **Evidence pointer** Methods section "Coarse-Grained Model for Nanog and DNA", Figure S7
  - **Concern** The treatment of the DNA-binding domain is a critical modeling choice. The authors state that the HPS potential was not applied to the DBD because it was developed for disordered regions, and they perform a control simulation where HPS is applied to all residues. However, the results of this control are only briefly described as showing "micelle-like structures similar to those of the WT." This is insufficient. The DBD is a folded globular domain, and its interactions with disordered regions are likely to be important for the overall condensate organization. The authors need to provide a more detailed comparison of the two models, including quantitative measures of cluster size, domain organization, and condensate stability. Furthermore, the claim that the micelle-like structure is "not an artifact of the setup" requires a more rigorous demonstration that the two models produce statistically indistinguishable results.
  - **Why it matters** The modeling choice for the DBD could substantially affect the predicted condensate structure. If the conclusions are sensitive to this choice, the robustness of the findings is questionable.
  - **Resolution test** The authors should provide a quantitative comparison of the WT model (HPS on disordered regions only) versus the control model (HPS on all residues), including cluster size distributions, radial density profiles, and contact maps, with appropriate statistical tests to demonstrate equivalence or identify differences.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Interpretation of DNA binding results
  - **Claim pointer** The authors claim that Nanog condensates induce DNA-DNA attraction, bringing DNA fragments closer together
  - **Evidence pointer** Figure 6, section "Condensates induce DNA-DNA attraction"
  - **Concern** The DNA binding simulations use only four or eight 50 bp DNA fragments in a system with 200 Nanog proteins. The authors report that DNA fragments bind to the surface of the condensate and that DNA-DNA distances are shorter in the presence of the condensate compared to a DNA-only system. However, the statistical analysis is limited. The authors do not report how many independent simulations were performed, how the DNA-DNA distance distribution was calculated, or whether the observed differences are statistically significant. Additionally, the biological relevance of bringing DNA fragments to distances of 100-200 Å is not discussed in the context of enhancer-promoter communication, where the relevant length scales may be different.
  - **Why it matters** The claim that Nanog condensates can bring DNA elements closer together is presented as a key functional implication of the study. If this claim is not rigorously supported, the broader significance of the work is diminished.
  - **Resolution test** The authors should provide statistical analysis of the DNA-DNA distance distributions, including error bars and significance testing. They should also discuss the relationship between the simulated DNA-DNA distances and the distances relevant for enhancer-promoter communication in cells.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Sampling and convergence
  - **Claim pointer** The authors claim that the simulations reach near-equilibrium after 2-4 x 10^6 MD steps and that the phase-separated configurations are stable over the simulation time
  - **Evidence pointer** Figure 2, Figure S2, section "Phase separation of simulated human Nanog"
  - **Concern** The convergence analysis shown in Figure S2 is limited to the size of the condensed phase and the number of molecules in the condensed phase. This is insufficient to establish that the internal structure of the condensate (i.e., the micelle-like organization) has converged. The authors should show convergence of the key structural observables, such as the radial distribution of domains within clusters, the cluster size distribution, and the contact maps, as a function of simulation time. Additionally, the authors should report the total simulation lengths and the number of independent trajectories used for each condition.
  - **Why it matters** If the internal structure of the condensate has not converged, the reported micelle-like organization may be a transient, non-equilibrium feature.
  - **Resolution test** The authors should provide time-dependent analysis of the key structural observables, showing that they reach a plateau within the simulation time. They should also report the total simulation length and the number of independent trajectories for each condition.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of presentation
  - **Affected element** Figure 1
  - **Evidence pointer** Figure 1
  - **Issue** The domain boundaries for NTD, DBD, and CTD are not clearly indicated in the figure or its legend. The residue numbers for these domains are mentioned in the text but should be clearly marked in the figure for reader convenience.
  - **Required correction** Add residue number boundaries for NTD, DBD, and CTD to Figure 1A or its legend.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Figure 3B
  - **Evidence pointer** Figure 3B
  - **Issue** The cluster size distribution is shown without error bars or information about the number of independent simulations used to generate it.
  - **Required correction** Add error bars or confidence intervals to the cluster size distribution, and state the number of independent simulations used.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation of experimental comparison
  - **Affected element** Discussion of experimental results
  - **Evidence pointer** Introduction, Discussion
  - **Issue** The authors reference experimental results on Nanog condensate formation but do not provide a detailed quantitative comparison between their simulation predictions and experimental measurements (e.g., critical concentration, cluster size, or domain organization). Such a comparison would strengthen the validation of the model.
  - **Required correction** Add a more detailed comparison with experimental data where available, or explicitly state the limitations of such comparisons given the coarse-grained nature of the model.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Technical detail
  - **Affected element** Methods section
  - **Evidence pointer** Methods section "Molecular Dynamics Simulation"
  - **Issue** The methods state that the box size was gradually decreased along the z-axis to create the phase-separated initial configuration, but the rate of compression and the equilibration protocol after compression are not described in sufficient detail.
  - **Required correction** Provide more detail on the compression protocol, including the compression rate, the equilibration time after compression, and any checks that the resulting configuration is not dependent on the compression protocol.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Presentation of supplementary material
  - **Affected element** Supplementary figures
  - **Evidence pointer** Figure S1, S6
  - **Issue** The supplementary figures showing individual trajectories are useful but would benefit from a summary figure showing the variability across trajectories in a quantitative manner.
  - **Required correction** Consider adding a summary figure showing the mean and standard deviation of key observables across all trajectories.

## Technical failings that need to be addressed before the case is established
- R1-M1: Lack of statistical comparison against a null model for the micelle-like domain organization
- R1-M2: Insufficient quantitative comparison between the WT model and the control model with HPS applied to all residues
- R1-M3: Inadequate statistical analysis of DNA-DNA distance distributions
- R1-M4: Incomplete convergence analysis for internal condensate structure

## Risk / unsupported claims
- The claim that the micelle-like structure is a stable, equilibrium feature of Nanog condensates is not fully supported by the convergence analysis provided
- The claim that Nanog condensates can bring DNA elements closer together in a way that is relevant to enhancer-promoter communication is plausible but not rigorously established from the limited DNA simulation data
- The statement that "the current simulation model can reproduce the phase-separated form of Nanog observed in an experimental result" is an overstatement, as the comparison with experiment is only at the level of qualitative phase separation behavior, not quantitative structural agreement
- The speculation about cross-beta structure formation in the discussion is clearly labeled as speculation, which is appropriate, but the connection to the simulation results is tenuous given the limitations of the coarse-grained model
- The biological significance section makes claims about Nanog function in cells that go beyond what can be directly inferred from the simulation data, particularly regarding the relationship between phosphorylation, condensate stability, and transcriptional activity

## Assessment against Nature-style criteria
- **Originality** The concept of micelle-like clusters within transcription factor condensates is novel and represents a potentially important contribution to the field. The application of coarse-grained simulations to dissect the internal architecture of a specific transcription factor condensate is not entirely new, but the specific finding of a micelle-like organization with a defined radial domain arrangement is original.
- **Scientific importance** The work addresses a fundamental question about the structural organization of transcription factor condensates, which is relevant to understanding transcriptional regulation. If the micelle-like organization is confirmed, it could have implications for how condensates recruit DNA and other factors. However, the importance is somewhat limited by the focus on a single protein and the lack of direct experimental validation.
- **Interdisciplinary readership** The work bridges computational biophysics and cell biology, and would be of interest to researchers in both communities. The findings on condensate structure could also be relevant to researchers studying phase separation in other contexts. The manuscript is written in a way that is accessible to a broad audience, though some familiarity with simulation methods is assumed.
- **Technical soundness** The simulation methodology is generally appropriate, but several technical concerns need to be addressed, particularly regarding the statistical rigor of the cluster analysis and the convergence of the internal structure. The control simulations are a positive feature, but the analysis of these controls is insufficient.
- **Readability for nonspecialists** The manuscript is generally well-written and the main findings are clearly presented. The abstract and introduction provide sufficient context for nonspecialists. However, some sections, particularly the methods and the discussion of cluster analysis, may be challenging for readers without a computational background. The figures are informative but could be improved with clearer labeling and more detailed legends.

## Recommendation posture
Supportive if technical concerns are resolved. The central finding of micelle-like clusters in Nanog condensates is potentially important and the simulation approach is appropriate. However, the statistical rigor of the cluster analysis, the convergence of the internal structure, and the quantitative comparison between different model variants need to be strengthened before the case is fully established. The DNA binding results are interesting but require more careful statistical analysis and interpretation.