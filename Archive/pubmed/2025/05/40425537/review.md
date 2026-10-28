## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific content, methodological rigor, data interpretation, and claims as presented in the provided manuscript
- **Shared manuscript claim summary** The authors report that the interaction between FOXO4-DBD and p53-TAD is highly heterogeneous and dynamic, with p53-TAD retaining substantial flexibility in the complex. Using NMR paramagnetic relaxation enhancement (PRE) data combined with HADDOCK molecular docking, they propose multiple binding modes and identify the N-terminal region of FOXO4-DBD as the primary interaction surface. They also report that hydrophobic residues in p53-TAD contribute to complex stability and that phosphorylation-mimicking mutations increase binding affinity.
- **Visible evidence base** NMR chemical shift perturbation data (Fig. 1), fluorescence anisotropy binding assays (Fig. 1e, Fig. 5), PRE-derived distance restraints (Fig. 3), HADDOCK structural models (Fig. 4), 15N relaxation measurements (Fig. 2), and supporting supplementary figures
- **Missing materials affecting confidence** Raw NMR spectra, complete PRE intensity ratio datasets, validation statistics for HADDOCK models, full relaxation dispersion data, and details of the AlphaFold2 model used as starting structure were not fully accessible in the provided text

## Reviewer

- **Overall assessment** This manuscript addresses a biologically relevant question regarding the structural basis of the FOXO4-p53 interaction, which is implicated in cellular senescence. The authors employ a technically appropriate hybrid approach combining PRE NMR with molecular docking to characterize a challenging dynamic system. The data support the conclusion that the interaction is heterogeneous and that p53-TAD remains flexible in the complex. However, several concerns regarding the interpretation of binding affinity data, the robustness of the structural models, and the functional relevance of the phosphorylation experiments need to be addressed before the case is fully established.

- **Who would be interested in the results, and why** Researchers in the fields of structural biology, particularly those studying intrinsically disordered proteins and transient protein-protein interactions, will find the methodological approach of interest. The aging and senescence research community will be interested in the potential therapeutic implications for targeting the FOXO4-p53 interaction. Additionally, those studying transcription factor regulation and p53 biology may find the data relevant to understanding how p53-TAD engages with multiple partners.

- **Major strengths** The study addresses a technically challenging system using an appropriate combination of solution NMR methods and computational modeling. The use of multiple FOXO family members provides comparative insight. The integration of PRE-derived distance restraints with docking simulations represents a reasonable strategy for studying dynamic complexes. The phosphorylation-mimicking experiments add a functional dimension to the structural work.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data interpretation and claim support
- **Claim pointer** The authors claim that FOXO3-DBD binds p53-TAD with higher affinity (KD 1.2 ± 0.1 µM) than FOXO1-DBD (8.8 ± 0.8 µM) and FOXO4-DBD (42 ± 6 µM), and that this reflects meaningful differences in binding modes.
- **Evidence pointer** Fig. 1e, Results section "FOXO-DBDs differ in their binding affinities to p53-TAD"
- **Concern** The fluorescence anisotropy measurements were performed with a fluorescein-labeled p53-TAD A63C mutant. The authors acknowledge in Supplementary Fig. 8 that the fluorescein moiety slightly increases binding affinity to FOXO4-DBD, yet they use this labeled construct for all comparative KD determinations across the three FOXO proteins. The magnitude of this labeling effect on each FOXO-DBD is not characterized. If the fluorescein contributes differentially to binding across the three proteins, the reported KD differences may not accurately reflect the true relative affinities. Additionally, the KD values differ by approximately 35-fold between FOXO3 and FOXO4, yet the CSP profiles appear qualitatively similar. The authors should provide a more rigorous validation that the labeled construct reports faithfully on relative binding affinities across all three FOXO proteins.
- **Why it matters** The comparative affinity data form a central part of the results and are used to support the claim that FOXO proteins interact with p53 through different mechanisms. If the affinity differences are artifacts of the fluorescent label, this conclusion is weakened.
- **Resolution test** Perform competition binding experiments with unlabeled p53-TAD or use an alternative labeling strategy to confirm the relative affinities. Alternatively, validate that the fluorescein label has a similar effect on binding across all three FOXO-DBDs.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Structural model validation
- **Claim pointer** The authors claim that the HADDOCK model of the FOXO4-DBD:p53-TAD complex, consisting of a set of ten conformers, represents a reliable structural model of the interaction.
- **Evidence pointer** Fig. 4, Results section "PRE NMR measurements", Methods section "High Ambiguity Driven protein-protein DOCKing simulations"
- **Concern** The manuscript reports that 617 PRE-derived distance restraints were used for docking, but the quality of the resulting models is not rigorously assessed. The Q-factor analysis is described, but the final ensemble selection criteria beyond Q-factor optimization are not clearly specified. The authors note that the conformers show high variability in p53-TAD conformation, which is consistent with flexibility, but this also raises the question of whether the models are overfit to the PRE data. The manuscript does not report cross-validation statistics, such as how well the models predict PRE data not used in the docking, or provide a comparison with an independent experimental validation. Additionally, the use of an AlphaFold2 model as the starting structure for FOXO4-DBD, without experimental validation of that model under the conditions used, introduces potential bias.
- **Why it matters** The structural model is a key deliverable of the study. Without adequate validation, the specific binding modes proposed cannot be considered reliable, and the claim that the models provide structural insights into the interaction is not fully supported.
- **Resolution test** Provide cross-validation of the models against a subset of PRE restraints withheld from docking, or validate the models using independent experimental data such as mutagenesis coupled with binding assays targeting predicted interface residues.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Functional relevance of phosphorylation data
- **Claim pointer** The authors claim that phosphorylation-mimicking mutations in p53-TAD increase binding affinity to FOXO4-DBD, implying that phosphorylation modulates the interaction.
- **Evidence pointer** Fig. 5c, Results section "Phosphorylation of p53-TAD affects its affinity for FOXO4-DBD"
- **Concern** The phosphorylation-mimicking mutations (S15E, S20E, S46E, T55E) are used as proxies for actual phosphorylation. While this is a common approach, the authors do not discuss the limitations of glutamate as a phosphomimetic, particularly for serine residues where the charge distribution and hydrogen bonding potential differ from a true phosphate group. The effect sizes are modest (KD values of 14.3 ± 1.6 and 12 ± 3 µM for the double and quadruple mutants, respectively, compared to 42 ± 6 µM for WT), and the authors do not test whether actual phosphorylation by a kinase produces similar effects. The physiological relevance of these findings is therefore uncertain.
- **Why it matters** The phosphorylation data are presented as a significant finding with implications for stress response regulation. If the phosphomimetic approach does not faithfully recapitulate phosphorylation effects, the conclusion that phosphorylation modulates the FOXO4-p53 interaction is not established.
- **Resolution test** Perform in vitro phosphorylation assays with relevant kinases and test the effect on binding, or use unnatural amino acid incorporation to introduce phosphoserine at specific positions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological relevance and context
- **Claim pointer** The authors claim that the FOXO4-DBD:p53-TAD interaction is a promising target for developing senolytic compounds and that their structural insights will facilitate such efforts.
- **Evidence pointer** Discussion section
- **Concern** The study is performed entirely with isolated domains in vitro. While the authors acknowledge this limitation, the leap from the structural characterization of isolated domains to therapeutic targeting is substantial. The authors do not demonstrate that the interaction interface identified in their models is functionally relevant in cells, nor do they show that disrupting this interaction phenocopies the effects of known senolytic agents. The claim that these findings "should prompt further research" is reasonable, but the framing as a promising therapeutic target overstates the current evidence.
- **Why it matters** The translational claims in the discussion may overstate the significance of the findings and could mislead readers about the readiness of this interaction as a drug target.
- **Resolution test** Provide cellular experiments demonstrating that mutations at the identified interface affect FOXO4-p53-dependent transcriptional regulation or senescence phenotypes, or temper the therapeutic claims in the discussion.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness of methods
- **Affected element** Methods section, PRE measurements
- **Evidence pointer** Methods section "PRE measurements"
- **Issue** The methods for PRE data collection and analysis are described briefly. The pulse sequence for measuring 1H transverse relaxation rates is referenced but not described in sufficient detail for reproduction. The conversion of intensity ratios to distances and the treatment of paramagnetic versus diamagnetic states could be clarified.
- **Required correction** Expand the methods to include specific parameters for PRE experiments, such as relaxation delays, number of scans, and the exact procedure for calculating Γ2 rates and converting to distance restraints.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Fig. 1e and Fig. 5
- **Evidence pointer** Figure legends for Fig. 1e and Fig. 5
- **Issue** The binding affinity data are reported as mean of three technical replicates, but error bars and statistical significance between conditions are not described in the figure legends. The authors state that some mutants bind with "significantly lower" affinity, but no statistical tests are reported.
- **Required correction** Include error bars, the number of independent experiments, and appropriate statistical tests in the figure legends and results text.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Figure clarity
- **Affected element** Fig. 4
- **Evidence pointer** Fig. 4 legend
- **Issue** The figure shows the HADDOCK model ensemble, but the representation of the ten conformers is not clear from the legend alone. It is not specified how the conformers are superimposed, which regions are shown, or how the color coding relates to the different p53-TAD regions.
- **Required correction** Clarify the figure legend to describe the superposition method, the representation of the ensemble, and the color coding of the p53-TAD regions.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The authors mention previous studies on FOXO-p53 interactions but do not provide a comprehensive comparison of their findings with those of other groups who have studied this interaction, particularly regarding the proposed binding interface and affinity values.
- **Required correction** Add a more detailed comparison with previous structural and biochemical studies of FOXO-p53 interactions to contextualize the new findings.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data availability statement
- **Evidence pointer** Not explicitly provided in the manuscript text
- **Issue** The manuscript does not include an explicit data availability statement describing where the NMR chemical shift assignments, PRE data, and structural models have been deposited. The authors mention BMRB accession codes for relaxation data but not for other datasets.
- **Required correction** Include a complete data availability statement with accession codes for all deposited data, including chemical shift assignments and structural models.

## Risk / unsupported claims
- The claim that the identified interaction surface can be targeted by small molecules or peptides for senolytic development is not supported by any experimental evidence in this study and should be framed as speculative.
- The claim that phosphorylation of p53-TAD modulates the interaction with FOXO4-DBD is based solely on phosphomimetic mutations and is not directly tested with actual phosphorylation.
- The statement that the HADDOCK model provides "structural insights" into the interaction is only partially supported, as the model validation is incomplete.
- The claim that DNA binding displaces p53-TAD from FOXO4-DBD is based on relaxation measurements but the quantitative details and statistical significance of this effect are not fully reported.
- The assertion that the binding interface identified in the isolated domains is the same in the context of full-length proteins is inferred from CSP similarity but not directly demonstrated.