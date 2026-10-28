## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary information description
- **Assessment boundary** Scientific validity, technical soundness, and support of claims based solely on the provided manuscript content
- **Shared manuscript claim summary** The authors characterize the molecular mechanism of Nurr1 activation by vidofludimus, propose an allosteric binding site between helices 1, 5, 7, and 8, validate this site through mutagenesis and molecular dynamics simulations, and use these insights to design a more potent analog (compound 1) with improved binding affinity and cellular activity.
- **Visible evidence base** Figures 1-4, Supplementary Figures 1-6, Supplementary Tables 1-4, Supplementary Data 1-2, methods sections for mutagenesis, reporter gene assays, protein expression, HTRF, ITC, BLI, docking, and MD simulations
- **Missing materials affecting confidence** Raw data files, uncropped gel/blot images (if applicable), full MD trajectory analysis details, statistical analysis details for HTRF and reporter assays, compound purity data beyond NMR, and complete dose-response curves for all compounds tested

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive and well-executed study addressing a significant gap in the Nurr1 ligand field. The combination of biophysical assays, mutagenesis, and MD simulations provides a multi-layered approach to characterizing the vidofludimus binding site. The structure-guided design of compound 1 with improved potency is a logical and well-supported extension of the mechanistic findings. However, several technical concerns regarding the interpretation of mutagenesis data, the robustness of the MD simulations, and the generalizability of the proposed binding model require clarification before the claims can be fully accepted.
- **Who would be interested in the results, and why** Researchers in nuclear receptor biology, medicinal chemistry, and neurodegenerative disease drug discovery would find this work valuable. The identification of a druggable allosteric pocket on Nurr1 and the demonstration of structure-guided ligand optimization provide a template for future Nurr1 modulator development. The mechanistic insights into ligand-induced dimer dissociation and coregulator release also inform fundamental understanding of NR4A receptor regulation.
- **Major strengths** The study addresses a clear gap in the field, namely the lack of structural understanding of synthetic Nurr1 agonist binding. The use of orthogonal techniques (HTRF, ITC, BLI, mutagenesis, MD) to cross-validate findings is methodologically rigorous. The structure-guided design of compound 1 with 10-fold improved potency is a compelling demonstration of the utility of the proposed model. The manuscript is clearly written and the figures are informative.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4
- **Assessment against Nature-style criteria** Originality: The identification of a specific allosteric binding site for a synthetic Nurr1 agonist is novel and represents a meaningful advance over prior work that only identified covalent ligand binding sites. Scientific importance: The work has clear translational relevance given the therapeutic interest in Nurr1 activation for neurodegenerative diseases. The mechanistic insights are likely to inform future drug design efforts. Interdisciplinary readership: The work bridges structural biology, computational chemistry, and medicinal chemistry, and should appeal to readers across these disciplines. Technical soundness: The experimental design is generally sound, but several concerns (detailed below) regarding data interpretation and simulation robustness need to be addressed. Readability for nonspecialists: The manuscript is well-structured and the key concepts are explained clearly, though some sections assume familiarity with nuclear receptor biology and computational methods.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of mutagenesis interpretation
- **Claim pointer** The authors claim that mutations in site 4 (I500F, I500W, H372F) specifically affect vidofludimus binding and activity, while mutations in other proposed sites do not.
- **Evidence pointer** Figure 2b, Supplementary Figures 3-4
- **Concern** The mutagenesis data are presented as EC50 values for vidofludimus on mutant receptors, but the authors do not report whether these mutations affect the basal constitutive activity of Nurr1. If the mutations alter constitutive activity, the EC50 changes could reflect altered receptor responsiveness rather than specific effects on ligand binding. Additionally, the authors do not report binding affinity data for the mutants that show reduced potency, so it is unclear whether the reduced activity reflects decreased binding or impaired activation. The claim that I500F and H372F mutations "had a more consistent impact" is based on only two mutants, which is a limited basis for localizing a binding site.
- **Why it matters** The identification of the binding site is the central claim of the manuscript. If the mutagenesis data are confounded by effects on constitutive activity or receptor stability, the proposed binding model would be substantially weakened.
- **Resolution test** The authors should report constitutive activity of all mutants in the absence of ligand, and ideally provide binding affinity measurements (e.g., ITC or BLI) for key mutants to demonstrate that reduced potency correlates with reduced binding affinity.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Robustness of MD simulation evidence
- **Claim pointer** The authors claim that MD simulations support stable binding of vidofludimus at site 4 and that the I500W mutation stabilizes the preferred binding mode.
- **Evidence pointer** Figure 3d-i, Supplementary Data 1
- **Concern** The MD simulations are presented as supporting evidence for the binding model, but the analysis appears limited. The authors report RMSD values and ligand binding energies, but do not provide details on the convergence of the simulations, the number of independent binding events observed, or whether the simulations were started from the docked pose only. The claim that the I500W mutation "stabilized the ligand's preferred binding mode" is based on comparing binding energies between two simulations, but the statistical significance of this difference is not assessed. Furthermore, the authors do not report whether the ligand remained bound throughout all four repeats of each simulation, which is critical for assessing binding stability.
- **Why it matters** The MD simulations are used to rationalize the enhanced potency of compound 1 and the effects of the I500W mutation. If the simulations are not robust or statistically well-supported, the mechanistic interpretations drawn from them are questionable.
- **Resolution test** The authors should provide additional analysis including per-residue interaction energies, time series of key contacts, and statistical comparison of binding energies across repeats. Ideally, multiple independent simulations with different initial velocities should be shown to demonstrate reproducibility.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Support for the proposed binding site from docking
- **Claim pointer** The authors propose that vidofludimus binds to a specific allosteric pocket at site 4 based on docking and MD simulations.
- **Evidence pointer** Figure 3a, Methods section "Molecular docking"
- **Concern** The docking calculations were performed using a single crystal structure (PDB ID 1ovl) and a single docking protocol (Glide XP). The authors do not report whether alternative docking poses were obtained or whether the top-scoring pose was consistently reproduced across different docking runs or with different protein conformations. The manuscript does not provide a docking score for vidofludimus or compound 1, nor does it compare the docking scores of these compounds with those of inactive analogs. Without this information, it is difficult to assess whether the proposed binding mode is uniquely supported by the docking data.
- **Why it matters** The docking results form the basis for the MD simulations and the subsequent ligand design. If the docking is not robust or the binding mode is not well-defined, the entire structure-guided design rationale is weakened.
- **Resolution test** The authors should report docking scores for both compounds, ideally with multiple docking runs to assess pose reproducibility. Comparison with known inactive analogs would strengthen the claim that the binding mode is specific.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability of the proposed binding model
- **Claim pointer** The authors claim that the identified binding site and mechanism are relevant for Nurr1 ligand design more broadly.
- **Evidence pointer** Discussion section
- **Concern** The study focuses on a single chemical scaffold (vidofludimus and its analog 1). The authors do not test whether the proposed binding site is relevant for other known Nurr1 agonists, such as amodiaquine or statins, which were mentioned in the introduction. The claim that the model "will aid future ligand discovery" is speculative without evidence that the binding site is conserved across different ligand classes. Additionally, the authors do not discuss whether the proposed allosteric site is conserved in other NR4A receptors, which would be relevant given the high sequence homology.
- **Why it matters** The broader relevance of the findings is a key part of the manuscript's significance. If the binding model is only applicable to this specific scaffold, the impact of the work is more limited.
- **Resolution test** The authors should either test additional known Nurr1 agonists in their assays or provide a clear discussion of the limitations of the proposed model for other ligand classes.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 1c-f
- **Evidence pointer** Figure 1c-f
- **Issue** The HTRF data in Figure 1c-f are presented as fold change vs. DMSO control, but the statistical significance of the observed effects is not indicated. It is unclear whether the differences between vidofludimus-treated and control samples are statistically significant for all tested concentrations.
- **Required correction** Add statistical analysis (e.g., error bars with significance indicators) to the HTRF data, or clearly state in the figure legend which comparisons are statistically significant.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** ITC methods
- **Evidence pointer** Methods section "Isothermal titration calorimetry"
- **Issue** The ITC methods state that experiments were performed at least twice, but the results are presented as single representative experiments. The variability between replicates is not reported, which limits the assessment of data reliability.
- **Required correction** Report the results of all replicates or provide a measure of variability (e.g., mean ± SD) for the ITC-derived thermodynamic parameters.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity of compound characterization
- **Affected element** Compound 1 synthesis
- **Evidence pointer** Methods section "Chemistry"
- **Issue** The purity of compound 1 is reported as 99.1% by qNMR, but the manuscript does not provide HPLC chromatograms or other analytical data to support this claim. Additionally, the yield of the final step is not reported.
- **Required correction** Provide HPLC trace or chromatogram for compound 1 in the supplementary information, and report the yield of the final step.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The authors do not discuss the limitations of their study, such as the lack of a co-crystal structure of vidofludimus bound to Nurr1, which would provide definitive evidence for the proposed binding site.
- **Required correction** Add a paragraph discussing the limitations of the study and the need for future structural studies to confirm the proposed binding model.

## Risk / unsupported claims
- The claim that the identified binding site is "druggable" is not directly supported by experimental evidence, as no in vivo or cellular target engagement studies beyond reporter gene assays are presented.
- The claim that "release of the likely more transcriptionally active Nurr1 monomer contributed to the molecular activation mechanism" is speculative, as the relative transcriptional activity of Nurr1 monomers versus dimers is not directly measured.
- The statement that the proposed binding model "will aid future ligand discovery" is a forward-looking claim that cannot be validated from the current data.
- The claim that compound 1 has "substantially enhanced potency and binding affinity" compared to vidofludimus is supported by the data, but the authors do not report whether compound 1 retains selectivity for Nurr1 over other NR4A receptors or related nuclear receptors.
- The relevance of the proposed binding site for other known Nurr1 agonists (e.g., amodiaquine, statins) is not experimentally addressed and should not be inferred from the current data.