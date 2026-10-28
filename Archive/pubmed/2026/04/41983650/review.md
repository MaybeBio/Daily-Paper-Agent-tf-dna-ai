## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusion, supplementary description, data availability statement)
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and internal consistency of the presented findings; no assessment of literature novelty beyond what is stated in the manuscript
- **Shared manuscript claim summary** The authors use extensive MD simulations of BRD3-ET and BRD4-ET to show that paralog-specific peptide recognition arises from subtle differences in the dynamics of the α2–α3 loop, particularly at residues 35 and 36, which modulate formation of flanking helices η1 and η2, control binding-site opening, and determine the number, stability, and geometry of accessible binding modes.
- **Visible evidence base** MD simulation trajectories (7.2 μs per replicate, triplicate per system, 12 systems total), PCA and ELViM analyses, DSSP secondary structure analysis, RMSD distributions, distance analyses, normal-mode analysis, correlation matrices, fpocket pocket prediction, comparison to published NMR structures (PDB IDs cited)
- **Missing materials affecting confidence** The full Supporting Information (figures SI 1–43, tables SI 1–2, supporting methods) is not provided; experimental binding affinity data for the specific peptide–paralog pairs are not included; no experimental validation of the predicted cryptic pocket is presented; details of the MM/PBSA calculations mentioned in the supplementary description are not available

## Reviewer
- **Overall assessment** This manuscript addresses a significant and timely question in the BET protein field: how paralog-specific recognition arises in the highly conserved ET domain. The authors employ extensive MD simulations and a thoughtful comparative framework to propose that sequence differences at positions 35 and 36 in the α2–α3 loop modulate local secondary-structure propensities and loop dynamics, thereby shaping paralog-specific binding modes. The study is well-designed in its use of complementary analysis methods (PCA, ELViM, KL divergence, normal-mode analysis) and the cross-validation of findings across multiple approaches strengthens the central claims. However, several concerns limit the current strength of the conclusions. The reliance on modeled complexes for the cross-paralog comparisons, the absence of quantitative energetic validation, and the lack of direct experimental corroboration for the proposed mechanism mean that the mechanistic claims remain suggestive rather than definitive. The manuscript is clearly written and will interest researchers in epigenetic reader domains, molecular recognition, and drug discovery, but the evidence as presented does not fully establish the mechanistic model proposed.

- **Who would be interested in the results, and why** Researchers studying BET family proteins and epigenetic reader domains will find the paralog-specific recognition mechanism directly relevant to understanding functional divergence among highly conserved domains. Computational biophysicists and MD practitioners will be interested in the methodological framework for comparing conformational ensembles across homologous systems. Drug discovery scientists targeting BET proteins will be interested in the proposed cryptic pocket and the implications for paralog-selective inhibitor design. The broader molecular recognition community will find the discussion of conformational selection versus induced fit in the context of peptide binding informative.

- **Major strengths** The study addresses a well-defined and biologically important question with a clear hypothesis-driven approach. The computational design is thoughtful, using multiple complementary analysis methods to cross-validate findings. The comparison of both unbound and bound states across two paralogs with two different peptides provides a systematic framework. The authors are appropriately cautious in acknowledging limitations of MD simulations and the absence of kinetic data. The identification of a potential cryptic pocket adds translational relevance. The manuscript is well-structured and clearly written, with appropriate attention to methodological caveats.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that paralog-specific dynamical differences between BRD3-ET and BRD4-ET are intrinsic to each paralog and persist across different peptide ligands, providing a mechanistic basis for selective engagement.
- **Evidence pointer** Results sections "Comparative Conformational Dynamics of BRD3 and BRD4" and "The α2–α3 Loop as a Determinant of Paralog-Specific Peptide Recognition"; Figures 2, 3, 4, 5
- **Concern** The central claim of paralog-specific dynamics is based on comparisons between BRD3-ET and BRD4-ET, but the unbound BRD4-ET state was modeled by removing peptides from BRD4 complex structures, and the BRD3-peptide complexes for LANA and JMJD6 were modeled by mutation from BRD4 structures. This means that for the key cross-paralog comparisons, one of the two systems is always a computational model rather than an experimentally determined structure. The authors state that the simulations "quickly lost memory of the starting conformations," but this assertion requires more rigorous demonstration. The possibility that the modeled starting structures bias the observed dynamical differences cannot be excluded without additional validation, such as comparing simulation outcomes from multiple independent starting structures or demonstrating convergence of key observables from different initial conditions.
- **Why it matters** The central conclusion that paralog-specific dynamics are intrinsic and sequence-encoded depends critically on the reliability of the modeled systems. If the observed differences arise from artifacts of the modeling procedure rather than genuine sequence-dependent properties, the mechanistic model would be substantially weakened.
- **Resolution test** The authors should demonstrate that the key dynamical differences (e.g., η1/η2 helix propensities, loop opening distributions, PCA populations) are robust to the choice of starting structure. This could be achieved by initiating simulations from multiple distinct conformations for each system and showing convergence of the key observables, or by performing additional control simulations where the modeled systems are initiated from the experimentally determined structures of the other paralog.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Quantitative support
- **Claim pointer** The authors propose that differences in binding-site opening and loop dynamics provide a thermodynamic rationale for paralog-specific binding affinities, specifically that BRD3 supports broader ligand-bound geometries while BRD4 enforces a more constrained binding mode.
- **Evidence pointer** Results sections "Peptides That Bind as Hairpins Occupy the Full ET Pocket and Form Stable Complexes" and "Local Helix Formation in the η1/η2 Regions Regulates Binding-Site Opening and Drives Paralog-Specific Recognition"; Figures 5, 6, 7
- **Concern** The manuscript reports qualitative differences in binding modes and dynamics but does not provide quantitative energetic or kinetic validation connecting the observed dynamical differences to the reported affinity differences. The authors mention that TP has Kd = 13 ± 10 nM, BRG1 and CHD4 have Kd = 7 ± 1 μM and 95 ± 10 μM, and LANA, JMJD6, and NSD3 have Kd values around 250 ± 150 μM, but no quantitative analysis links the observed conformational dynamics to these affinity differences. The supplementary description mentions MM/PBSA calculations, but these results are not presented in the main text. Without quantitative energetic analysis or experimental validation, the claim that the observed dynamical differences "provide a structural rationale" for affinity differences remains speculative.
- **Why it matters** The manuscript's central contribution is a mechanistic explanation for paralog-specific recognition. A mechanistic explanation requires demonstrating a quantitative link between the proposed structural/dynamical mechanism and the observed functional outcome (differential affinity or selectivity). Without this link, the study describes interesting dynamical differences but does not establish their functional significance.
- **Resolution test** The authors should present the MM/PBSA calculations (or equivalent free energy analysis) that directly compare binding energetics across paralog–peptide pairs and demonstrate that the observed dynamical differences correlate with computed binding free energies. Alternatively, experimental validation using mutagenesis of residues 35/36 to swap the paralog-specific sequences and measure the effect on binding affinity would directly test the proposed mechanism.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The authors state that a Kolmogorov–Smirnov test comparing RMSD distributions for each peptide bound to BRD3 and BRD4 yielded p-values smaller than 0.05, confirming that observed differences are statistically significant.
- **Evidence pointer** Results section "The α2–α3 Loop as a Determinant of Paralog-Specific Peptide Recognition"; Figure 5
- **Concern** The statistical testing is described only in a single sentence with no details on the specific comparisons performed, the number of tests, or whether multiple testing corrections were applied. Given that the manuscript reports many comparisons across multiple systems and observables, the risk of false positives from multiple testing is substantial. Additionally, the KS test on RMSD distributions may not be the most appropriate test for comparing conformational ensembles, as it does not account for the temporal correlations inherent in MD trajectories.
- **Why it matters** The statistical significance of the observed differences is used to support the central claim of paralog-specific binding modes. Inadequate statistical treatment undermines confidence in the robustness of the findings.
- **Resolution test** The authors should provide full details of the statistical analysis, including the number of comparisons, the specific observables tested, whether corrections for multiple testing were applied, and whether the analysis accounts for the non-independence of MD trajectory frames. If multiple testing is a concern, appropriate corrections should be applied and reported.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Claim scope
- **Claim pointer** The authors propose that the identified mechanism provides "a structural and dynamical framework for the rational design of paralog-selective therapeutics targeting this conserved epigenetic reader family."
- **Evidence pointer** Conclusion section; Results section "Local Helix Formation in the η1/η2 Regions Regulates Binding-Site Opening and Drives Paralog-Specific Recognition" (cryptic pocket discussion)
- **Concern** The claim regarding therapeutic relevance is based on the identification of a transient cryptic pocket in BRD3-ET simulations, supported by fpocket predictions. However, no experimental validation of this pocket is provided, and the functional relevance of this pocket for small-molecule binding is entirely speculative. The leap from computational identification of a transient pocket to a framework for drug design is substantial and not supported by the current evidence.
- **Why it matters** Overstating the translational implications of computational findings without experimental validation can mislead readers and overstate the study's practical significance. The drug design claim extends beyond what the evidence supports.
- **Resolution test** The authors should either temper the drug design claims to reflect the speculative nature of the cryptic pocket identification, or provide additional computational evidence (e.g., small-molecule docking, pocket stability analysis across independent simulations) that strengthens the case for the pocket's potential druggability.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods section, "Systems of Study"
- **Evidence pointer** Methods section, paragraph 1
- **Issue** The description of how the modeled complexes were generated is brief. The statement that structures were "rebuilt based on backbone and Cβ coordinates using tleap" is unclear regarding which residues were mutated and how the peptide coordinates were handled during the mutation process.
- **Required correction** Provide a more detailed description of the modeling procedure, including the specific residues mutated, the treatment of the peptide during mutation, and any minimization or equilibration steps performed before the production simulations.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section, "Molecular Dynamics Protocol"
- **Evidence pointer** Methods section, paragraph 2
- **Issue** The manuscript states that simulations were run "in triplicate for 7.2 μs each" but does not specify how the replicates were initiated (e.g., different random seeds, different initial velocities, or different starting structures). This information is important for assessing the independence of replicates.
- **Required correction** Specify how the three replicates were generated and whether they represent independent sampling or variations of the same trajectory.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Evidence completeness
- **Affected element** Results section, "Peptides That Bind as Hairpins Occupy the Full ET Pocket and Form Stable Complexes"
- **Evidence pointer** Results section, paragraph 2
- **Issue** The authors state that "the frequent dissociation observed on these time scales is surprising" but do not provide quantitative data on the frequency or timing of dissociation events across the different systems. This makes it difficult to assess the reliability of the bound-state analyses.
- **Required correction** Provide quantitative information on the fraction of time each peptide remains bound in each simulation, and specify which analyses were performed on bound versus dissociated portions of the trajectories.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results section, "Local Helix Formation in the η1/η2 Regions Regulates Binding-Site Opening and Drives Paralog-Specific Recognition"
- **Evidence pointer** Results section, paragraph 3; Figure 6
- **Issue** The manuscript describes the η1 region as displaying "persistent bimodal behavior" in BRD3 upon peptide binding, but the functional significance of this bimodality is not fully explained. It is unclear whether the two modes represent distinct functional states or simply thermal fluctuations.
- **Required correction** Clarify the structural and functional interpretation of the bimodal distributions, and specify whether the two modes correspond to distinct binding-site geometries that would be expected to have different ligand-binding properties.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Abstract
- **Evidence pointer** Abstract, final sentence
- **Issue** The abstract states that the findings "provide a structural rationale for paralog-specific targeting of BET proteins," which overstates the strength of the evidence given that no experimental validation is presented and the energetic link between dynamics and affinity is not established.
- **Required correction** Soften the language in the abstract to reflect the computational nature of the study, for example by stating that the findings "suggest a structural basis" or "propose a mechanism" for paralog-specific targeting.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods section, "Analysis"
- **Evidence pointer** Methods section, paragraph 3
- **Issue** The manuscript mentions that "Additional analysis details are provided in the Supporting Methods" but does not describe the normal-mode analysis or correlation matrix calculations in the main text. Given that these analyses are used to support key conclusions, some description in the main text would be helpful.
- **Required correction** Provide a brief description of the normal-mode analysis and correlation matrix methods in the main text, or move the relevant methodological details from the Supporting Information to the main text.

## Risk / unsupported claims
- The claim that the identified mechanism provides a framework for "rational design of paralog-selective therapeutics" is not supported by the evidence presented, as no experimental validation of the cryptic pocket or the proposed mechanism is provided.
- The assertion that the modeled BRD4-ET unbound state and the modeled cross-complexes "quickly lost memory of the starting conformations" is not rigorously demonstrated and requires additional validation.
- The claim that the observed dynamical differences "provide a structural rationale" for differential affinity is not quantitatively supported, as no free energy calculations or experimental binding data are presented in the main text.
- The statistical significance of the KS test results is reported without sufficient methodological detail to assess their validity.
- The functional significance of the proposed cryptic pocket in BRD3-ET is entirely speculative and not supported by experimental evidence.