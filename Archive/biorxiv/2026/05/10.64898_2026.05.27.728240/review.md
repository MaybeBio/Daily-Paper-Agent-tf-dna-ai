## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and supplementary figure/table references
- **Assessment boundary** Structural, biochemical, and cellular characterization of the Zn linchpin motif in human MUTYH, including three crystal structures, metal analysis, in vitro activity assays, cellular repair assays, and computational modeling
- **Shared manuscript claim summary** The authors report three full-length human MUTYH crystal structures bound to DNA across distinct catalytic states, revealing a Zn linchpin motif coordinated by His85, Cys332, Cys339, and Cys342. They propose that Zn coordination organizes a communication network connecting the Zn site, the [4Fe-4S] cluster, and the active site via Arg247/Arg307, and that this network is important for DNA repair in cells, potentially through interactions with downstream BER factors such as APE1.
- **Visible evidence base** Three crystal structures (PDB IDs 11ji, 11jh, 11ip), ICP-MS metal quantification, in vitro glycosylase assays, EMSA and fluorescence polarization binding assays, cellular repair assays in HEK293FT cells, AlphaFold3 Multimer predictions, phylogenetic analysis, circular dichroism, differential scanning fluorimetry
- **Missing materials affecting confidence** Supplementary figures and tables referenced but not provided (Figures S1-S10, Tables S1-S2), PDB validation reports, raw kinetic traces, full statistical details for cellular assays, AlphaFold model confidence metrics, sequence alignment details

## Reviewer
- **Overall assessment** This manuscript presents a substantial structural and functional characterization of the Zn linchpin motif in human MUTYH, providing the first full-length human structures retaining both metal cofactors. The observation of state-dependent Zn coordination chemistry across the reaction coordinate is novel and potentially significant. However, several technical concerns regarding metal quantification, the interpretation of heterogeneous coordination states, and the disconnect between in vitro and cellular phenotypes require careful consideration before the central claims can be fully accepted.
- **Who would be interested in the results, and why** Researchers studying DNA repair mechanisms, particularly base excision repair and the MUTYH family of glycosylases. Structural biologists interested in metalloprotein coordination dynamics and allosteric communication. Cancer geneticists and clinicians studying MUTYH-associated polyposis, as the work provides structural context for understanding pathogenic variants. The broader DNA damage response community interested in how metal cofactors coordinate multi-domain enzyme function.
- **Major strengths** The manuscript provides the first full-length human MUTYH structures with both metal cofactors retained, resolving a significant gap in the field. The observation of state-dependent Zn coordination changes across the catalytic cycle is novel and potentially important. The integration of structural, biochemical, biophysical, and cellular approaches provides a comprehensive view of Zn function. The evolutionary analysis connecting Zn site emergence with Arg247/Arg307 conservation is informative. The work has clear translational relevance given the prevalence of MUTYH variants in cancer predisposition.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (metal quantification interpretation), R1-M2 (heterogeneous coordination states), R1-M3 (in vitro versus cellular disconnect), R1-M4 (AlphaFold3 limitations)
- **Assessment against Nature-style criteria** Originality: The state-dependent Zn coordination chemistry and the proposed allosteric network connecting metal sites to the active site represent a novel contribution. Scientific importance: The work addresses fundamental questions about metalloprotein function in DNA repair and has direct relevance to understanding cancer-associated variants. Interdisciplinary readership: The findings will interest structural biologists, DNA repair specialists, cancer geneticists, and potentially researchers studying metalloprotein evolution. Technical soundness: The structural work appears carefully executed, but several biochemical and computational aspects require additional validation. Readability for nonspecialists: The manuscript is generally well-written and accessible, though some sections assume significant background knowledge in glycosylase enzymology.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding metal quantification rigor, interpretation of heterogeneous coordination states, and the mechanistic basis for the in vitro versus cellular phenotype disconnect.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of metal quantification
- **Claim pointer** The manuscript claims that Zn deficiency leads to reduced Fe-S cluster loading, with MUTYH(Zn-) showing approximately 18% reduced Fe/protein ratio compared to MUTYH(Zn+).
- **Evidence pointer** Table 2, ICP-MS methods section
- **Concern** The ICP-MS data interpretation requires careful scrutiny. The claim that Zn loss causes Fe-S cluster destabilization is significant, but the manuscript does not provide sufficient detail on how the Fe/protein ratios were normalized and whether the observed difference is statistically robust. The authors report values of approximately 3.3 versus 4.0 Fe per protein, but no error bars, replicate numbers, or statistical tests are presented for these measurements. Additionally, the mechanism by which Zn deficiency would lead to partial Fe-S cluster loss is not clearly explained. The authors suggest increased solvent exposure of the cluster in the Zn- state, but the structural data showing this is based on a comparison between a Zn-bound crystal structure and a previously determined Zn-free structure, which may not be directly comparable.
- **Why it matters** The claim that Zn coordination protects the Fe-S cluster is central to the proposed model of inter-cofactor communication. If this claim is not rigorously supported, the model of Zn as a protective organizational element is weakened. Furthermore, the reduced Fe content in Zn- preparations could reflect differences in protein stability during purification rather than a specific functional relationship.
- **Resolution test** Provide replicate ICP-MS measurements with statistical analysis, include a direct comparison of protein stability between Zn+ and Zn- preparations, and demonstrate that the Fe-S cluster loss is specifically due to Zn absence rather than purification artifacts. Consider using UV-visible spectroscopy or EPR to directly assess Fe-S cluster integrity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretation of heterogeneous Zn coordination states
- **Claim pointer** The manuscript claims that Zn coordination is dynamic across the catalytic cycle, with Cys332 coordinating in the early TSAC (one chain), dissociating in the late TSAC (both chains), and re-coordinating in the PAC (both chains).
- **Evidence pointer** Figure 2, Results section "Structural overview of MUTYH Zn holoproteins"
- **Concern** The interpretation of state-dependent Zn coordination relies on comparing coordination states across three different crystal forms, each with different DNA analogs. The observation that one chain in the early TSAC retains Cys332 coordination while the other does not is presented as meaningful, but this could simply reflect crystal packing artifacts or differential radiation damage. The authors do not discuss whether the two chains in the asymmetric unit differ in other ways that might explain the differential coordination. Furthermore, the claim that Cys332 coordination is "restored" in the PAC implies a temporal sequence that cannot be established from static crystal structures of different complexes.
- **Why it matters** The dynamic Zn coordination model is a central novelty of the manuscript. If the observed differences reflect crystallization artifacts rather than biologically relevant conformational changes, the proposed mechanism of coordination sphere remodeling during catalysis is not supported.
- **Resolution test** Provide additional evidence for the functional relevance of Cys332 coordination dynamics, such as solution-based studies (XAS, EXAFS) on MUTYH in different states, or mutagenesis of Cys332 that specifically affects the proposed coordination dynamics without altering overall protein stability. Discuss potential crystal packing effects on the observed coordination heterogeneity.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Disconnect between in vitro and cellular phenotypes
- **Claim pointer** The manuscript claims that Cys332 mutations (C332S, C332R) show wild-type-like in vitro activity but reduced cellular repair, suggesting a role for the Zn linchpin in downstream BER steps beyond glycosylase activity.
- **Evidence pointer** Figure 5, Figure 6, Table 2
- **Concern** The disconnect between in vitro and cellular phenotypes is intriguing but the mechanistic explanation remains speculative. The authors propose that the Zn linchpin mediates interactions with APE1 or other BER factors, but the only evidence for this is an AlphaFold3 prediction. The cellular repair assay measures overall pathway completion, and reduced repair could result from many factors including protein stability, localization, or interactions with other cellular components. The manuscript does not directly test the proposed APE1 interaction hypothesis, nor does it exclude alternative explanations for the cellular phenotype.
- **Why it matters** The claim that the Zn linchpin has functions beyond intrinsic glycosylase activity is important for understanding how MUTYH variants cause disease. However, without direct evidence for the proposed mechanism, this remains speculative. The distinction between effects on glycosylase activity versus downstream BER coordination has implications for understanding the molecular basis of MUTYH-associated pathology.
- **Resolution test** Directly test the proposed MUTYH-APE1 interaction using biochemical methods (pull-downs, co-immunoprecipitation, surface plasmon resonance) with wild-type and mutant proteins. Perform complementation experiments in MUTYH-deficient cells with variants that separate glycosylase activity from proposed scaffolding functions. Consider testing additional BER factors beyond APE1.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Computational modeling limitations
- **Claim pointer** The manuscript uses AlphaFold3 Multimer predictions to propose a MUTYH-APE1-DNA ternary complex interface involving the Zn-linchn motif and the PIP box.
- **Evidence pointer** Figure 8, Methods section "MUTYH–APE1 interaction predictions"
- **Concern** AlphaFold3 is a powerful tool but has known limitations in predicting protein-protein interfaces, particularly for complexes involving DNA and metal cofactors. The authors acknowledge that AlphaFold does not model the Fe-S cluster, but the absence of this cofactor could significantly affect the predicted conformation of the Fe-S cluster domain and its interactions. The manuscript does not provide confidence metrics for the predicted interface, nor does it validate the prediction with any experimental data. The claim that the PIP box mediates APE1 interaction is particularly notable given that this motif is canonically associated with PCNA binding.
- **Why it matters** The proposed APE1 interaction model is used to explain the cellular phenotypes of Zn linchpin variants. If the computational model is inaccurate, the mechanistic interpretation of the cellular data is called into question. The potential dual role of the PIP box in binding both PCNA and APE1 is an interesting but unvalidated hypothesis.
- **Resolution test** Provide AlphaFold confidence metrics (pLDDT, PAE) for the predicted interface. Validate the predicted interaction using site-directed mutagenesis of interface residues followed by biochemical binding assays. Consider whether the PIP box can simultaneously mediate interactions with both PCNA and APE1, or whether these are mutually exclusive.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of structural comparisons
- **Affected element** Figure 2, Results section
- **Evidence pointer** Figure 2
- **Issue** The comparison of Zn coordination states across the three structures is difficult to follow from the text alone. The authors should more clearly describe which residues coordinate Zn in each state and how the coordination geometry changes.
- **Required correction** Provide a clear table or schematic summarizing the Zn coordination sphere in each structure, including bond distances and angles. Consider using a supplementary figure to show the coordination sphere in each state side-by-side.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Table 2, Figures 5 and 6
- **Evidence pointer** Table 2, Figure 5, Figure 6
- **Issue** The manuscript reports kinetic parameters, binding affinities, and cellular repair percentages without clear indication of the number of independent replicates or statistical significance. Error bars are shown in some figures but not described in the legends.
- **Required correction** Clearly state the number of independent experiments for each measurement, report standard deviations or standard errors, and indicate statistical significance where comparisons are made. Add statistical details to figure legends.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Evolutionary analysis depth
- **Affected element** Figure 7, Results section "Arg247/Arg307 bridge evolved in concert with the emergence of the Zn-Linchpin Motif"
- **Evidence pointer** Figure 7
- **Issue** The phylogenetic analysis is presented briefly and the sequence alignment is not shown. The claim that Arg247/Arg307 co-evolved with the Zn site would be strengthened by a more detailed analysis showing the correlation between Zn site presence and Arg247/Arg307 conservation.
- **Required correction** Provide the full sequence alignment as a supplementary file, and consider a more quantitative analysis of the co-evolution of Zn-coordinating residues and the Arg247/Arg307 pair across the sampled species.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of alternative interpretations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion presents the proposed model of Zn function as the primary interpretation without thoroughly considering alternative explanations for the observed phenotypes. For example, the reduced cellular repair of Zn-site mutants could reflect protein misfolding or degradation rather than specific disruption of a communication network.
- **Required correction** Add a paragraph discussing alternative interpretations of the data and how the proposed model could be distinguished from these alternatives experimentally.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Methodological detail for cellular assays
- **Affected element** Methods section "Transfection and flow cytometry"
- **Evidence pointer** Methods section
- **Issue** The cellular repair assay is described briefly. The gating strategy, number of cells analyzed, and how the repair percentage is calculated from flow cytometry data are not fully described.
- **Required correction** Provide additional methodological detail including gating strategy, number of events analyzed, and the exact equation used to calculate repair percentage. Include representative gating plots in supplementary material.

## Risk / unsupported claims
- The claim that Zn coordination protects the Fe-S cluster from degradation is based on ICP-MS data without statistical analysis and a structural comparison between non-isomorphous crystal forms.
- The proposed state-dependent Zn coordination dynamics (Cys332 dissociation and reassociation) cannot be definitively established from static crystal structures of different complexes.
- The claim that the Zn linchpin mediates MUTYH-APE1 interactions is based solely on AlphaFold3 predictions without experimental validation.
- The assertion that reduced cellular repair of Zn-site mutants reflects impaired downstream BER coordination rather than other cellular effects (e.g., protein stability, localization) is not directly supported by the data presented.
- The evolutionary claim that Arg247/Arg307 co-evolved with the Zn site is based on a limited phylogenetic analysis without quantitative co-evolution assessment.
- The statement that the Zn linchpin has "dual roles" in lesion engagement and downstream coordination is a reasonable hypothesis but is not directly tested in this manuscript.