## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) from bioRxiv preprint
- **Assessment boundary** Scientific content, methodological rigor, evidence quality, and claims as presented in the provided text; no external validation or replication attempted
- **Shared manuscript claim summary** The authors propose that the intrinsically disordered C-terminal region (C-IDR) of the pioneer transcription factor Sox2 undergoes conformational changes upon DNA binding, driven by redistribution of weak electrostatic interactions with the folded DNA-binding domain, which alters the accessibility of two activation domains without affecting DNA binding affinity.
- **Visible evidence base** Single-molecule FRET (smFRET) data, NMR spectroscopy (chemical shift assignments, CSPs, relaxation), far-UV CD, coarse-grained molecular dynamics simulations, binding affinity measurements, fluorescence lifetime analysis
- **Missing materials affecting confidence** Figures and supplementary figures referenced but not provided; Supplementary Tables 1-5 not provided; Supplementary Movies 1-2 not provided; detailed simulation parameters and validation metrics only partially described; raw data and statistical analysis details not available

## Reviewer

- **Overall assessment** This manuscript addresses an important and timely question in transcription factor biology: how intrinsically disordered regions behave in the context of full-length proteins and how DNA binding modulates their conformational ensembles. The integration of multiple biophysical techniques is commendable and the central observation that DNA binding redistributes interdomain interactions is potentially significant. However, the evidence as presented has several gaps that prevent full confidence in the conclusions. The smFRET data are described but key quantitative details are missing, the NMR CSP analysis is presented without clear statistical thresholds, and the simulation approach, while reasonable, relies on parameters that are not fully justified. The claim that activation domain accessibility is "redistributed" is supported by indirect evidence (contact lifetimes and ensemble dimensions) rather than direct functional measurements. The manuscript would benefit from clearer presentation of control experiments, more rigorous statistical treatment, and explicit discussion of limitations.

- **Who would be interested in the results, and why** Researchers studying transcription factor structure-function relationships, particularly those focused on intrinsically disordered regions and their role in gene regulation. The work is also relevant to the biophysics community interested in IDP conformational ensembles and to those studying pioneer factors and chromatin biology. The methodological integration of smFRET, NMR, and simulations provides a template that could be applied to other transcription factor systems.

- **Major strengths**
  1. Integration of multiple orthogonal biophysical techniques (smFRET, NMR, CD, simulations) to address a challenging question
  2. Use of full-length protein rather than isolated domains, providing physiologically relevant context
  3. The observation that DNA binding does not affect binding affinity despite large conformational changes is counterintuitive and interesting
  4. The simulation approach with back-calculation of FRET efficiencies provides a testable framework
  5. The potential generality of the findings for other transcription factors is well argued

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence quality
- **Claim pointer** The authors claim that the C-IDR is "highly disordered" and that its conformational dynamics are "guided by weak and dynamic charge interactions with the folded DNA binding domain."
- **Evidence pointer** Figure 1, Figure 2, NMR section, smFRET section
- **Concern** The evidence for the "weak and dynamic" nature of the interdomain interactions is not quantitatively established. The smFRET data show differences in mean transfer efficiency between full-length and isolated C-IDR, but the magnitude of the effect and the statistical significance are not clearly reported. The NMR CSP data are described qualitatively ("considerable CSPs") without a defined threshold for significance. The salt dependence is mentioned as "exquisitely salt-sensitive" but the actual data and fitted parameters are not shown in the text. The claim that interactions are "weak" requires quantitative binding or interaction strength measurements that are not presented.
- **Why it matters** The central mechanistic model depends on the nature and strength of these interactions. If the interactions are not weak and dynamic, the proposed model of "redistributed" accessibility would need revision. The distinction between weak electrostatic interactions and more stable contacts has implications for how the ensemble is conceptualized and for the functional interpretation.
- **Resolution test** Provide quantitative analysis of smFRET data including mean E values with error bars and statistical tests for full-length vs. isolated C-IDR across salt concentrations. Define a CSP significance threshold (e.g., based on spectral noise or a multiple of the average CSP). Show salt titration curves with fitted parameters and confidence intervals.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors state that "DNA binding can lead to complex changes in the IDR ensemble and accessibility" and that this "specifically redistributes the accessibility of two activation domains critical for transcription."
- **Evidence pointer** Figure 3, Figure 4, Figure 5, simulation section
- **Concern** The claim that activation domain accessibility is "redistributed" is inferred from changes in contact lifetimes and ensemble dimensions in simulations, but no direct measurement of accessibility is provided. The simulation analysis shows differential contact lifetimes for AD1 and AD2, but this is a computational inference. The experimental data (smFRET, NMR) show global changes in the C-IDR ensemble but do not specifically resolve AD1 versus AD2 accessibility. The functional significance of the proposed redistribution is not tested experimentally (e.g., through binding assays with coactivators or mutations that disrupt the proposed interactions).
- **Why it matters** The title and abstract emphasize the redistribution of activation domain accessibility as a key finding. If this is only a simulation-based inference without experimental validation, the claim is overstated. The functional implications for transcription regulation are speculative without direct evidence that the proposed accessibility changes affect coactivator binding or transcriptional activity.
- **Resolution test** Provide experimental evidence for differential AD1/AD2 accessibility, such as: (a) NMR or smFRET probes specifically positioned within AD1 and AD2, (b) limited proteolysis or chemical labeling experiments, (c) coactivator binding assays comparing free and DNA-bound Sox2, or (d) mutational analysis that disrupts the proposed interaction redistribution and shows functional consequences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical rigor
- **Claim pointer** The authors claim that the coarse-grained simulations "reconstruct experimentally-derived FRET values" and that the ensemble shows "excellent agreement" with experiments.
- **Evidence pointer** Figure 4, simulation methods
- **Concern** The validation of the simulation approach is described briefly. The concordance correlation coefficients (0.94 and 0.96) are reported, but the number of FRET pairs used for validation, the range of values, and the sensitivity of the results to the single tuning parameter (εpp) are not fully described. The claim that a single parameter can simultaneously match 11 FRET efficiencies for free and 11 for bound Sox2 is remarkable and requires more detailed validation. The choice of εpp = 0.16 kT is stated to be from previous work, but the transferability to this system is not discussed. The simulation length, convergence criteria, and sampling quality are not reported.
- **Why it matters** The simulation provides the structural interpretation of the experimental data. If the model is not adequately validated or if the results are sensitive to parameter choices, the structural conclusions about AD1/AD2 redistribution could be artifacts of the model rather than reflecting the true ensemble.
- **Resolution test** Provide a more detailed validation of the simulation approach: (a) show the full set of experimental vs. simulated FRET efficiencies with uncertainties, (b) demonstrate convergence of the simulations, (c) test sensitivity of the key conclusions to εpp values, (d) provide error estimates on the contact lifetime calculations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Completeness
- **Claim pointer** The authors state that "Both DNA and nucleosome binding induce major rearrangements in the IDR ensemble without affecting DNA binding affinity."
- **Evidence pointer** Figure 3, binding affinity measurements
- **Concern** The binding affinity measurements are described but the actual Kd values, the number of replicates, and the statistical comparison between full-length Sox2 and isolated DBD are not presented in the text. The claim that the C-IDR does not affect DNA binding affinity is based on this comparison, but the precision of the measurement is unclear. Additionally, the nucleosome binding experiments are mentioned but the data are not shown or described in detail.
- **Why it matters** The claim that the C-IDR does not affect DNA binding affinity is important for the model that the C-IDR's role is in regulating cofactor interactions rather than DNA binding. If the affinity measurements are not precise enough to detect modest differences, the conclusion could be premature. The nucleosome data are relevant for the pioneer factor context but are not adequately described.
- **Resolution test** Report Kd values with confidence intervals for at least 3 independent replicates for full-length Sox2 and DBD with both specific and non-specific DNA. Provide the nucleosome binding data with appropriate controls and statistical analysis.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "More than 1600 human transcription factors orchestrate the transcriptional machinery" which is a broad opening that does not clearly connect to the specific findings of the paper. The abstract could more clearly state the specific gap being addressed and the unique contribution of this work.
- **Required correction** Consider revising the opening to more directly frame the specific question about IDR conformational dynamics in transcription factors, and clarify what is novel about the Sox2 system.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, smFRET section
- **Evidence pointer** Methods, Single-molecule spectroscopy
- **Issue** The labeling efficiency and the fraction of doubly-labeled molecules are not reported. The selection of bursts based on stoichiometry ratio (S = 0.3-0.7) is described, but the actual labeling efficiency and how it affects the interpretation of the FRET data is not discussed.
- **Required correction** Report labeling efficiencies for each construct and discuss how the presence of singly-labeled or unlabeled species might affect the measured FRET efficiencies.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion speculates about the generality of the findings to other transcription factors and about links to phase separation, but these speculations are not clearly distinguished from the established findings. The final paragraph introduces several speculative ideas without clear caveats.
- **Required correction** Clearly separate established findings from speculation, and add appropriate caveats when discussing potential generality and functional implications.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, NMR section
- **Evidence pointer** Methods, NMR spectroscopy
- **Issue** The NMR experiments are described but the assignment completeness, the number of spectra used for assignment, and the quality metrics (e.g., chemical shift RMSD between replicates) are not reported. The CSP calculation is described but the threshold for significance is not defined.
- **Required correction** Report assignment statistics, define the CSP significance threshold, and provide information about spectral quality and reproducibility.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results, simulation section
- **Evidence pointer** Figure 5
- **Issue** The contact lifetime analysis is described but the statistical significance of the differences between AD1 and AD2 contact lifetimes is not reported. The figure is referenced but not visible in the provided text.
- **Required correction** Provide statistical analysis of the contact lifetime differences, including error estimates and significance testing.

## Risk / unsupported claims
1. The claim that activation domain accessibility is "redistributed" upon DNA binding is not directly supported by experimental data; it is inferred from simulation contact lifetimes and ensemble dimensions.
2. The claim that the observed conformational changes are "exquisitely salt-sensitive" is not quantitatively supported in the provided text; the actual data and fitted parameters are not shown.
3. The claim that the findings are likely generalizable to other transcription factors is speculative and not directly tested.
4. The statement that the C-IDR ensemble on nucleosomes is "similar, albeit not identical" to that on DNA is not supported by shown data; the nucleosome experiments are described but data are not presented.
5. The claim that the simulation approach "reveals" the structural ensemble is somewhat overstated given that the model is coarse-grained and relies on a single tuning parameter; the interpretation is model-dependent.
6. The functional significance of the proposed accessibility changes for transcriptional regulation is not experimentally tested and remains speculative.