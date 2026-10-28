## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and figure legends as provided.
- **Assessment boundary** Scientific validity, technical soundness, target validation, and support for claims as presented in the provided manuscript. No assessment of editorial fit or journal-specific policy.
- **Shared manuscript claim summary** The authors claim that SaeR, the response regulator of the SaeRS two-component system in Staphylococcus aureus, is a druggable target for antivirulence therapy. They report the discovery of a small-molecule inhibitor, HR3744, identified via high-throughput screening, which directly binds SaeR, inhibits its DNA-binding activity, and reduces virulence factor expression without affecting bacterial growth. A structure-activity relationship study yielded an analogue, SAV13, with improved potency. Both compounds showed efficacy in a mouse bacteraemia model.
- **Visible evidence base** Results sections describing knockdown experiments, high-throughput screening, Western blot, qPCR, haemolysis and leucotoxicity assays, EMSA, waterLOGSY-NMR, virtual docking, mutagenesis, SAR analysis, and mouse infection models. Figure legends for Figures 1, 2, 3, 4, and 5 are provided. Supplementary figure and table titles are referenced but not fully described.
- **Missing materials affecting confidence** Actual figures and raw data are not provided. Supplementary figures and tables are referenced but not included. No structural coordinates, NMR spectra, or docking output files are available. No statistical details beyond p-values in figure legends. No information on compound purity, solubility, or formulation for in vivo studies.

## Reviewer
- **Overall assessment** The manuscript addresses an important and timely topic, the development of antivirulence strategies against S. aureus, and identifies a novel class of SaeR inhibitors. The combination of genetic validation, biochemical assays, and in vivo efficacy data is commendable. However, several technical concerns, particularly regarding the interpretation of the knockdown data, the specificity of the compounds, and the in vivo experimental design, need to be resolved before the central claims can be considered fully established.
- **Who would be interested in the results, and why** Researchers in the fields of antimicrobial drug discovery, bacterial pathogenesis, two-component signal transduction systems, and virulence regulation would find these results of interest. The work also has potential translational relevance for clinicians and public health researchers concerned with antibiotic resistance and alternative therapeutic strategies.
- **Major strengths** The study addresses a clinically relevant problem with a rational approach. The use of an inducible knockdown system to validate targetability in vivo is a thoughtful strategy. The identification of a specific binding interaction between HR3744 and SaeR using multiple orthogonal methods (EMSA, waterLOGSY, docking, mutagenesis) strengthens the target validation. The SAR study and identification of a more potent analogue demonstrate a path for compound optimization. The inclusion of in vivo efficacy data in a bacteraemia model is a significant strength.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Target validation
- **Claim pointer** The authors claim that "SaeR is targetable for the discovery of antivirulence agent" based on the in vivo knockdown experiment.
- **Evidence pointer** Figure 1, Results section "SaeR is targetable for antivirulence drug development"
- **Concern** The in vivo knockdown experiment uses an anhydrous tetracycline (aTc)-inducible system. The authors state that aTc was administered orally 6 h post-infection. However, the specificity of the knockdown is not fully demonstrated. It is unclear whether the observed reduction in abscess size and bacterial load is due to SaeR knockdown or to potential off-target effects of the CRISPR-dCas9 system or the inducer itself. The authors do not show that aTc treatment alone (in mice infected with a strain harbouring a non-targeting guide RNA) has no effect. Additionally, the level of SaeR knockdown achieved in vivo is not quantified.
- **Why it matters** The central premise of the manuscript is that SaeR is a valid target for antivirulence therapy. If the knockdown experiment is confounded by off-target effects or the inducer has intrinsic activity, the conclusion that SaeR is targetable is weakened.
- **Resolution test** Provide data showing that aTc treatment of mice infected with a strain expressing a non-targeting sgRNA has no effect on abscess size or bacterial load. Quantify SaeR knockdown efficiency in vivo (e.g., by qPCR or Western blot of bacterial samples recovered from abscesses).

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Compound specificity
- **Claim pointer** The authors claim that "When Glu159 was changed to Asn, the bacteria developed resistance to HR3744," and that this validates target specificity.
- **Evidence pointer** Figure 3E, Results section "Target specificity of HR3744"
- **Concern** The mutagenesis data are presented for a single residue (E159N) and the effect on HR3744 activity is shown. However, it is not clear whether this mutation affects SaeR function globally (e.g., DNA-binding affinity, phosphorylation) or specifically affects HR3744 binding. The authors do not show that the E159N mutant retains normal SaeR function in the absence of the compound. Without this control, the resistance phenotype could be due to a loss of SaeR function rather than a specific loss of HR3744 binding.
- **Why it matters** The claim that HR3744 specifically targets SaeR via E159 is a key part of the target validation. If the mutation compromises SaeR function, the resistance phenotype is not informative about the compound's mechanism of action.
- **Resolution test** Show that the E159N mutant retains wild-type levels of SaeR activity (e.g., hla expression, DNA-binding in EMSA) in the absence of HR3744. Ideally, perform a binding assay (e.g., ITC or NMR) with the mutant protein to demonstrate loss of HR3744 binding.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** In vivo efficacy
- **Claim pointer** The authors claim that "In a mouse bacteraemia model, both HR3744 and SAV13 exhibited in vivo effectiveness."
- **Evidence pointer** Figure 5G, Results section "Effect of SAV13"
- **Concern** The in vivo data show a reduction in bacterial load in the kidneys of treated mice. However, the experimental design has several limitations. First, the timing of treatment (1 h post-infection) is prophylactic rather than therapeutic. Second, the doses used (7.5 and 25 mg/kg for HR3744; 4.9 mg/kg for SAV13) are not justified by pharmacokinetic or dose-response studies. Third, the statistical analysis reports p-values for comparisons between treatment and vehicle groups, but the p-value for the HR3744 25 mg/kg group versus vehicle is 0.066, which is not significant. The authors do not discuss this. Fourth, no survival data or clinical scores are presented.
- **Why it matters** The claim of in vivo efficacy is a major conclusion of the manuscript. The current data are preliminary and do not fully support the conclusion that these compounds are effective in a therapeutic setting.
- **Resolution test** Provide a more clinically relevant treatment regimen (e.g., treatment after infection is established). Include dose-response studies and justify dose selection. Report survival data and clinical scores. Address the non-significant result for the high-dose HR3744 group.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mechanistic understanding
- **Claim pointer** The authors state that "HR3744 inhibited SaeR-DNA probe binding" in EMSA and that "HR3744 directly interacted with SaeR's DNA-binding domain" based on waterLOGSY-NMR.
- **Evidence pointer** Figure 2A, Figure 3B, Results sections "Identification of HR3744" and "Target specificity of HR3744"
- **Concern** The EMSA data show inhibition of SaeR-DNA binding, but the stoichiometry and affinity of the interaction are not quantified. The waterLOGSY data demonstrate binding but do not localize the binding site to the DNA-binding domain. The docking studies suggest a binding site, but this is not experimentally confirmed. The claim that HR3744 binds to the DNA-binding domain is not directly supported by the data presented.
- **Why it matters** Understanding the mechanism of inhibition is important for compound optimization and for assessing potential off-target effects. The current data are suggestive but not conclusive.
- **Resolution test** Perform a quantitative binding assay (e.g., fluorescence polarization or ITC) to determine the Kd of HR3744 for SaeR and SaeRDBD. Use NMR chemical shift perturbation or HDX-MS to map the binding site. Confirm that HR3744 competes with DNA for binding to SaeR.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Selectivity
- **Claim pointer** The authors claim that HR3744 and SAV13 are specific inhibitors of SaeR, but no data on selectivity against other response regulators or two-component systems are presented.
- **Evidence pointer** Not applicable
- **Concern** The manuscript does not address the selectivity of HR3744 and SAV13 for SaeR over other bacterial response regulators or host proteins. Given that response regulators share structural homology, this is a significant gap.
- **Why it matters** Selectivity is critical for the development of a safe and effective antivirulence agent. Off-target effects could lead to toxicity or disruption of beneficial bacterial flora.
- **Resolution test** Screen HR3744 and SAV13 against a panel of related response regulators (e.g., AgrA, WalR, PhoP) in DNA-binding or phosphorylation assays. Assess cytotoxicity against a broader panel of mammalian cell lines.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1
- **Evidence pointer** Figure 1
- **Issue** The figure legend mentions "Protein A and α-toxin production in different saeR knockdown strains with or without inducer aTc (100 ng/mL)" but the Western blot data are not shown in the provided text. It is unclear how the knockdown efficiency was quantified.
- **Required correction** Include the Western blot images and quantification. State the number of biological replicates.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 2
- **Evidence pointer** Figure 2
- **Issue** The figure legend states "A dose-dependent effect of HR3744 reduced major virulence factors production" but the concentrations used for the Western blot are not specified in the legend or text.
- **Required correction** Provide the concentration range used in the Western blot experiments.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 3
- **Evidence pointer** Figure 3
- **Issue** The figure legend mentions "Predicted binding conformations of HR3744 to SaeR" but the docking methodology is only briefly described in the methods. It is unclear whether the docking was performed with the full-length SaeR or the DNA-binding domain, and whether the protein was in the phosphorylated or unphosphorylated state.
- **Required correction** Provide more details on the docking protocol, including the protein structure used, the search space, and the scoring function.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 5
- **Evidence pointer** Figure 5
- **Issue** The figure legend states "Bacterial load of S. aureus USA300 or USA300-ΔsaeR in the kidney of mice after i.v. infection in the presence or absence of HR3744 and SAV13 treatment at different dosages." The dosages are not specified in the legend.
- **Required correction** Specify the dosages used for each treatment group.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Methods
- **Evidence pointer** Methods section "Mice bacteraemia infection models"
- **Issue** The methods state that mice were "randomized into three groups (8–10 mice per group)" but the figure legend for Figure 5G does not specify the number of mice per group.
- **Required correction** State the number of mice per group in the figure legend.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Methods
- **Evidence pointer** Methods section "Statistical analysis"
- **Issue** The methods state that "All experiments were performed in triplicates unless specified otherwise" but it is unclear if this applies to the animal experiments.
- **Required correction** Clarify the number of independent experiments and replicates for each assay.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results
- **Evidence pointer** Results section "Identification of HR3744"
- **Issue** The text states "After screening against 400 compounds with effects on hla expression, 139 compounds exhibited a repression effect on saeP1 promoters." It is unclear how the initial 400 compounds were selected and what the hit rate was.
- **Required correction** Provide more details on the screening cascade and the criteria for compound selection.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Results
- **Evidence pointer** Results section "Target specificity of HR3744"
- **Issue** The text states "In the wildtype USA300 strain, HR3744 inhibited the fluorescence signal with an EC50 of approximately 10 µM, but the EC50 in the saeS and saeR deletion strains were greater than 100 µM." It is unclear how the EC50 was calculated and whether the fluorescence signal is a direct measure of hla promoter activity.
- **Required correction** Provide details on the EC50 calculation and the relationship between fluorescence and hla expression.

- **Concern ID** R1-m9
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion states "the data from our chemical genetics, genetics, and mutagenesis studies demonstrated target specificity." However, the chemical genetics data (HR3763 losing activity) are not shown in the main figures.
- **Required correction** Include the HR3763 data in the main figures or clearly reference the supplementary data.

- **Concern ID** R1-m10
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Methods
- **Evidence pointer** Methods section "Molecular modelling"
- **Issue** The methods state that docking was performed using "a grid box covering the entire tetradecamer consisting of HR3744 chains A to B." This is confusing, as HR3744 is a small molecule, not a protein. It is likely meant to be "SaeR chains A to B."
- **Required correction** Correct the typo and clarify the docking setup.

## Risk / unsupported claims
- The claim that SaeR is targetable for antivirulence drug development is supported by the knockdown data, but the specificity of the knockdown is not fully demonstrated.
- The claim that HR3744 directly binds to SaeR's DNA-binding domain is not fully supported by the data. The waterLOGSY experiment shows binding to full-length SaeR, but the localization to the DNA-binding domain is inferred from docking, not experimentally confirmed.
- The claim that E159 is the key residue for HR3744 binding is based on a single mutation and lacks functional characterization of the mutant in the absence of the compound.
- The in vivo efficacy data are preliminary and do not include survival data or a therapeutic treatment regimen.
- The selectivity of HR3744 and SAV13 for SaeR over other response regulators is not addressed.
- The manuscript does not provide quantitative binding data (e.g., Kd) for the HR3744-SaeR interaction.
- The claim that SAV13 is "four times more potent" than HR3744 is based on EC50 values from reporter assays, but the statistical significance of this difference is not reported.