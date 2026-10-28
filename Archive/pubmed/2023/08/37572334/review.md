## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, and interpretation as presented in the provided manuscript text; no external data or supplementary materials were available for verification
- **Shared manuscript claim summary** The authors use extensive allosteric molecular dynamics (MD) simulations of liver receptor homolog-1 (LRH-1) bound to 24 related ligands (12 active, 12 inactive) to propose that active and inactive ligands communicate with the activation function surface (AFS) via distinct allosteric signaling circuits centered on helix 7. Inactive ligands promote strong communication between helix 7 and the AFS, while active ligands disrupt this circuit and instead induce connectivity with a second regulatory surface, AFB. The coactivator Tif2 modulates these circuits, and mismatched ligand-coregulator pairings produce destabilizing fluctuations.
- **Visible evidence base** Main text, figures referenced (Figures 1-8), tables referenced (Tables 1, S1, S2), and methods section
- **Missing materials affecting confidence** Supplementary figures (S1-S3) and tables (S1, S2) were referenced but not provided; specific numerical values for many statistical comparisons are not given in the text; structural coordinates and simulation input files were not available for independent verification

## Reviewer
- **Overall assessment** This manuscript presents a large-scale computational study of LRH-1 allostery, leveraging a chemically related ligand series with well-characterized biological activities. The central hypothesis, that active and inactive ligands engage distinct allosteric circuits through helix 7, is novel and potentially significant for understanding NR pharmacology. The scale of the simulation effort (74 complexes, >100 μs total) is commendable. However, the manuscript has several weaknesses that currently limit the strength of the conclusions. The distinction between "active" and "inactive" circuits relies heavily on correlational analyses whose statistical robustness is not fully demonstrated. The functional validation is indirect, and the mechanistic model, while plausible, is not uniquely supported by the data. The writing is generally clear but some methodological details and statistical treatments require clarification. Overall, the work is of interest to the NR and computational biophysics communities, but the case for the specific allosteric model would be strengthened by additional analyses and clearer presentation of the quantitative evidence.
- **Who would be interested in the results, and why** Researchers studying nuclear receptor structure, dynamics, and pharmacology; computational biophysicists interested in allosteric communication in proteins; medicinal chemists developing NR-targeted therapeutics, particularly for LRH-1 in metabolic and inflammatory diseases. The methodological framework for analyzing large MD datasets could also interest method developers.
- **Major strengths** 1) Large and chemically coherent ligand series with established biological activities, enabling meaningful structure-activity-dynamics correlations. 2) Comprehensive simulation strategy with triplicate runs and multiple analysis techniques (shortest distance, community analysis, suboptimal paths, PCA, RMSF). 3) Identification of helix 7 as a central mediator of ligand-dependent allosteric signaling is a novel and testable hypothesis. 4) The inclusion of coregulator (Tif2) effects adds biological relevance. 5) The proposed model distinguishes between coordinated motions and fluctuations as distinct signaling modes, which is conceptually interesting.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** 
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor and interpretation
- **Claim pointer** The authors claim that active and inactive ligands use "distinct allosteric signaling circuits" based on differences in community membership, suboptimal path counts, and shortest distance values.
- **Evidence pointer** Figures 2-4, Tables S1-S2; specific statistical values for community analysis comparisons are not provided in the text
- **Concern** The central claim of distinct circuits rests on comparisons of network properties (community size, path counts, shortest distances) between active and inactive ligand groups. While some p-values are reported (e.g., Fisher's exact test for community membership, Mann-Whitney for community size, negative binomial regression for path counts), the manuscript does not provide effect sizes, confidence intervals, or a clear demonstration that the observed differences are robust across the triplicate simulations. The clustering in Figure 2a is described as "unbiased" but the stability of the clustering (e.g., via bootstrap) is not assessed. Furthermore, the threshold for "strong" suboptimal paths (cutoff of 75 added to optimal path length) appears arbitrary and its influence on the results is not explored.
- **Why it matters** The entire mechanistic model depends on the statistical distinction between active and inactive ligand behavior. If the differences are marginal or sensitive to analysis parameters, the central conclusion is not supported. The manuscript needs to demonstrate that the observed effects are robust, specific, and not artifacts of the chosen cutoffs or clustering methods.
- **Resolution test** Provide a more detailed statistical analysis, including effect sizes and confidence intervals for the key comparisons. Perform sensitivity analyses for the suboptimal path cutoff and community detection parameters. Assess clustering stability via resampling methods. Show that the differences between active and inactive groups are consistent across individual replicate simulations, not just in the averaged data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Functional validation and causal inference
- **Claim pointer** The authors propose that inactive ligands send a "stop" signal to the AFS to disfavor coactivator binding, and that active ligands suppress this signal. They also claim that Tif2 binding to inactive ligand complexes creates a "frustrated" state.
- **Evidence pointer** Figures 5-7; no direct experimental validation of the proposed mechanism is presented
- **Concern** The manuscript is purely computational. While the authors reference prior experimental data (e.g., luciferase assays, DSF) to classify ligands, there is no new experimental validation of the proposed allosteric mechanism. The claims about "stop signals" and "frustrated states" are interpretations of simulation data (RMSF, PCA) that are not directly linked to functional outcomes. The causal direction (e.g., that helix 7 dynamics cause changes in AFS conformation) is inferred from correlations in the simulations.
- **Why it matters** For a Nature-style journal, the novelty and significance of the findings would be greatly enhanced by experimental validation. Without it, the model remains a hypothesis. The authors should either provide experimental evidence (e.g., mutations that disrupt the proposed circuits and show functional consequences) or temper the strength of their claims to reflect the computational nature of the study.
- **Resolution test** Add experimental validation, such as site-directed mutagenesis of key helix 7 or AFB residues predicted to be critical for circuit selection, followed by functional assays (e.g., transcriptional activity, coregulator recruitment). Alternatively, clearly frame the conclusions as a computational prediction that requires experimental testing.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Model construction and force field validation
- **Claim pointer** The authors constructed 74 models for MD simulations, including 24 ligands, some of which were docked rather than crystallographically determined. They state that ligands were docked such that the 6HP cores were aligned.
- **Evidence pointer** Methods section, Table 1, Figure 1c; docking details and validation are not provided
- **Concern** The manuscript does not provide sufficient detail on the docking protocol for ligands without crystal structures. It is unclear what software was used, how docking poses were scored and selected, and whether the poses were validated (e.g., by comparison to known structure-activity relationships or by assessing pose stability in short MD simulations). The force field parameters for the ligands (GAFF) and the protein (parm99-bsc0) are dated; newer force fields (e.g., ff14SB, ff19SB) are now standard. The choice of parm99-bsc0 may affect the dynamics, particularly for loop regions.
- **Why it matters** The conclusions depend on the accuracy of the initial models. If the docked poses are incorrect or the force field produces artifacts, the observed differences between active and inactive ligands could be spurious. The use of an outdated protein force field is a concern for the quantitative claims made.
- **Resolution test** Provide full details of the docking protocol, including software, scoring function, and validation. Justify the choice of parm99-bsc0 or repeat key simulations with a more modern force field to confirm the results are not force-field dependent. Consider running short simulations of docked poses to ensure stability before production runs.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of RMSF and PCA results
- **Claim pointer** The authors state that Tif2 binding increases fluctuations in AFB for inactive ligand complexes, and interpret this as "disharmony" or a "frustrated" state.
- **Evidence pointer** Figures 6-7; the magnitude of the RMSF differences and their statistical significance are not fully reported
- **Concern** The RMSF differences between active and inactive ligand complexes in the presence of Tif2 are described qualitatively. It is not clear if these differences are statistically significant at the residue level, or if they represent a small but consistent trend. The PCA analysis shows that the overlap matrices do not cluster by ligand class, which seems to contradict the claim of distinct essential motions. The authors explain this by focusing on per-residue contributions, but this needs clearer justification.
- **Why it matters** The interpretation of "frustration" is a strong claim that requires robust quantitative support. If the RMSF differences are small or not significant, the interpretation is overreaching. The PCA result that does not cluster by ligand class needs to be reconciled with the overall model.
- **Resolution test** Provide residue-level statistical analysis of RMSF differences (e.g., with confidence intervals or permutation tests). Quantify the fraction of residues in AFB that show significant differences. Discuss the PCA overlap result more explicitly and explain why the per-residue analysis is more informative than the global overlap.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of the model
- **Claim pointer** The authors suggest that their findings "could inform the design of LRH-1 modulators" and provide a framework for studying allostery in other receptors.
- **Evidence pointer** Discussion section; no data on other receptors or on modulator design are presented
- **Concern** The study is limited to a single receptor (LRH-1) and a single chemical scaffold (6HP). The authors do not test whether the proposed helix 7-mediated circuit switch applies to other LRH-1 ligands (e.g., phospholipids) or to other NRs. The claim of generalizability is speculative.
- **Why it matters** The significance of the work for a broad audience depends on the generalizability of the findings. Without evidence that the model applies beyond the specific ligand series studied, the impact is limited.
- **Resolution test** Acknowledge the limitations more explicitly. If possible, include simulations with a few non-6HP ligands (e.g., a phospholipid agonist) to test whether the model holds. Alternatively, frame the conclusions as specific to the 6HP series and discuss the potential for generalizability as a hypothesis.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness of methods
- **Affected element** Methods section, MD simulation protocol
- **Evidence pointer** Methods section, "MD simulations"
- **Issue** The manuscript states that simulations were performed in triplicate for 500 ns each, but does not specify the total number of simulations (74 complexes × 3 replicates = 222 simulations, totaling >100 μs, which is consistent). However, the temperature coupling algorithm, pressure coupling, and the specific Langevin thermostat parameters are not fully described. The equilibration protocol is described but the duration of each equilibration step is not given.
- **Required correction** Provide complete details of the MD protocol, including the length of each equilibration step, the specific algorithms used for temperature and pressure control, and the random seed for velocity generation. This is essential for reproducibility.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Figures 2-4, statistical tests
- **Evidence pointer** Figure legends and text
- **Issue** The manuscript reports p-values for some comparisons but does not consistently report effect sizes or confidence intervals. For example, the Mann-Whitney test for community size reports p = 0.0015, but the median and interquartile range for each group are not given in the text or figure.
- **Required correction** Add effect sizes and confidence intervals for all key statistical comparisons, or provide the underlying data in a supplementary table.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure quality and accessibility
- **Affected element** Figures 2-4, 6-7
- **Evidence pointer** Figures as described in text
- **Issue** The figures are described as heatmaps and network diagrams, but the text does not always explain how to interpret them. For example, Figure 2a shows a clustering heatmap, but the color scale and the meaning of the dendrogram are not explained in the legend. Figure 3a shows community structures, but the color coding of communities is not described.
- **Required correction** Ensure all figure legends are self-contained and explain the color scales, symbols, and any statistical annotations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Abstract and Discussion
- **Evidence pointer** Abstract, Discussion
- **Issue** The term "signaling circuits" is used throughout, but it is not formally defined. It is used to describe networks of correlated motions, but the relationship between these computational constructs and biological signaling is not explicitly stated.
- **Required correction** Define "signaling circuit" in the context of this work, and clarify that it is a computational construct representing correlated motions, not a direct measure of biochemical signaling.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction, Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript cites prior work on LRH-1 dynamics and NR allostery, but the discussion of how the present findings extend or contradict previous models could be more explicit. For example, the relationship between the proposed helix 7 circuit and the well-studied "mouse trap" model of NR activation is not discussed.
- **Required correction** Add a brief discussion of how the proposed model relates to existing models of NR activation, and what new insights the present work provides.

## Risk / unsupported claims
- The claim that inactive ligands send a "stop" signal to the AFS is an interpretation of computational data without direct experimental evidence; this is a hypothesis, not a demonstrated mechanism.
- The claim that the findings "could inform the design of LRH-1 modulators" is speculative, as no design or testing of modulators is presented.
- The generalizability of the helix 7 circuit model to other NRs is not supported by data presented in this manuscript.
- The statement that the quantitative approach "provides a framework to study allosteric signaling in other receptors" is a reasonable suggestion but is not validated by application to other systems.
- The classification of ligands into "active" and "inactive" groups relies on prior experimental data (luciferase assays) that are summarized in Table 1 but not fully described; the criteria for classification (e.g., threshold for EC50 or Emax) are not explicitly stated in the text.