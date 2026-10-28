## Review setup
- **Input scope** Full manuscript text (Introduction, Materials and methods, Results, Discussion, Conclusion) as provided. Supplementary material referenced but not provided.
- **Assessment boundary** Scientific soundness, methodological rigor, internal consistency, and support of claims by presented evidence. No assessment of editorial fit or publication decision.
- **Shared manuscript claim summary** The authors report an in silico pipeline to identify deleterious missense SNPs in the human SOX9 gene. From 5,029 SNPs, 1,158 missense variants were retrieved. After filtering with multiple pathogenicity prediction tools, four SNPs (D85H, A158T, K173E, D441N) were consistently predicted as deleterious. The D85H variant was prioritized as the most damaging based on conservation, stability predictions, and 100-ns molecular dynamics simulations. The authors conclude that D85H destabilizes the SOX9 protein structure, potentially disrupting DNA binding and contributing to cancer pathogenesis.
- **Visible evidence base** Tables 1-4; Figures 1-7; Supplementary Table S1 (referenced, not provided); Methods descriptions for SIFT, PolyPhen-2, SNAP, PhD-SNP, SNPs&GO, I-Mutant2.0, MUpro, ConSurf, MutPred2, Phyre2, VADAR, Desmond, Bio3D, GeneMANIA, STRING.
- **Missing materials affecting confidence** Supplementary Table S1 (quantitative MD data); Supplementary Information file; raw MD trajectory data; multiple sequence alignment details; dbSNP accession list; software version details for several tools; statistical analysis details for MD comparisons.

## Reviewer
- **Overall assessment** The manuscript presents a standard in silico SNP prioritization pipeline applied to SOX9. The workflow is conventional and the tools are appropriate for the stated purpose. However, the manuscript contains several internal inconsistencies, incomplete methodological reporting, and overinterpretation of results relative to the evidence presented. The central claim that D85H is a "highly damaging" variant with likely cancer relevance is not adequately supported by the data shown. The MD simulation analysis is particularly problematic: only one mutant (D85H) was simulated despite four prioritized variants, the reported RMSD values (29-33 Å) are implausibly large for a folded protein domain, and the interpretation of hydrogen bond counts is contradictory. The manuscript requires substantial revision and additional analysis before the conclusions can be considered established.
- **Who would be interested in the results, and why** Researchers in computational genomics and variant annotation may find the pipeline description useful as a methodological reference. Investigators studying SOX9-related disorders, particularly campomelic dysplasia and sex determination, may have interest in the prioritized variant list. However, the lack of experimental validation limits the utility for clinical or translational audiences. The cancer-related claims would interest oncology researchers only if experimentally substantiated, which is not the case here.
- **Major strengths** The authors employ a multi-tool consensus approach for pathogenicity prediction, which is appropriate for reducing false positives in silico. The integration of conservation analysis, stability prediction, and MD simulation represents a comprehensive computational strategy. The use of PCA, DCCM, and FEL analyses to characterize dynamic behavior is methodologically sound. The manuscript is clearly structured and the figures are generally legible.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (MD simulation reporting), R1-M2 (internal inconsistencies in variant counts and simulation numbers), R1-M3 (overinterpretation of functional and disease claims), R1-M4 (missing statistical and methodological details).
- **Assessment against Nature-style criteria** Originality: Low. The pipeline is a standard combination of widely used tools applied to a well-studied gene. No novel methodology or conceptual advance is presented. Scientific importance: Moderate at best. The findings are entirely computational and unvalidated. The clinical or biological significance of the prioritized variants is speculative. Interdisciplinary readership: Limited. The manuscript would primarily appeal to computational biologists and variant annotation specialists. Technical soundness: Weak. The MD simulation analysis contains implausible values and incomplete reporting. Several internal inconsistencies undermine confidence in the results. Readability for nonspecialists: Adequate. The manuscript is generally readable, though some sections (e.g., MD analysis) would benefit from clearer explanation of the significance of the reported metrics.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires major revisions, including correction of internal inconsistencies, complete reporting of MD simulation parameters and results, and tempering of conclusions to match the evidence level. Even after revision, the study would represent a modest contribution to the field.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that MD simulation analysis over 100 ns assessed the structural stability of native SOX9 and the D85H mutant, with reported RMSD values of 29.51 Å and 29.71 Å for wild-type and mutant, respectively.
- **Evidence pointer** Results, Molecular dynamics simulation analysis, RMSD analysis; Figure 5A; Supplementary Table S1
- **Concern** The reported RMSD values of approximately 29-33 Å are physically implausible for a folded protein domain. RMSD values of this magnitude indicate either global unfolding, loss of tertiary structure, or a technical error in trajectory analysis (e.g., incorrect atom selection, misalignment, or simulation box artifacts). The authors do not provide any explanation for these extreme values, nor do they show the RMSD as a function of time to demonstrate equilibration. Additionally, the text states "five mutant proteins" in the RMSD analysis section, but only one mutant (D85H) was simulated. This discrepancy is not addressed.
- **Why it matters** The MD simulation is the primary evidence for the claim that D85H destabilizes SOX9. If the RMSD values are erroneous or reflect technical artifacts, the central conclusion is unsupported. The inconsistency between "five mutant proteins" and the single simulated mutant further undermines confidence in the analysis.
- **Resolution test** The authors must provide: (1) RMSD versus time plots for both systems showing equilibration; (2) clarification of the number of mutants simulated; (3) explanation for the large RMSD values, including whether the protein remained folded throughout the simulation; (4) if the protein unfolded, this must be discussed as a limitation and the interpretation revised accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Internal consistency
- **Claim pointer** The manuscript states that four SNPs (D85H, A158T, K173E, D441N) were consistently identified as deleterious across all tools, and that D85H was the most damaging. However, the text also refers to "five mutant proteins" in the RMSD section and "three mutants" in the DCCM section.
- **Evidence pointer** Results, Molecular dynamics simulation analysis, RMSD analysis; Results, DCCM Analysis; Table 1; Table 4
- **Concern** The number of mutants analyzed is inconsistent across sections. The RMSD section mentions "five mutant proteins," the DCCM section mentions "three mutants," and the overall pipeline prioritized four SNPs. Only D85H is discussed in detail. It is unclear how many mutants were actually simulated and analyzed. This inconsistency suggests either incomplete editing or a lack of clarity in the experimental design.
- **Why it matters** The reader cannot determine the scope of the analysis. If only D85H was simulated, the claims about the other three variants (A158T, K173E, D441N) being destabilizing are based solely on static predictions, not dynamic simulations. The manuscript must clearly state which variants were subjected to which analyses.
- **Resolution test** The authors must provide a clear statement of the number of variants analyzed at each stage of the pipeline, including a flow diagram or table showing the filtering steps and the final set of variants subjected to MD simulation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Overinterpretation
- **Claim pointer** The authors conclude that D85H "may disrupt DNA binding, potentially weakening activation of chondrogenic targets and reducing repression of Wnt/beta-catenin signaling," and suggest implications for cancer pathogenesis and personalized therapy.
- **Evidence pointer** Discussion, paragraphs 3-5; Conclusion
- **Concern** The functional claims extend far beyond what the computational evidence can support. The manuscript provides no experimental data on DNA binding, transcriptional activity, or signaling pathway effects. The MD simulation, even if correctly analyzed, would only provide information about conformational stability of a single mutant. The leap from predicted destabilization to specific molecular mechanisms (e.g., Wnt/beta-catenin dysregulation) and therapeutic implications is speculative and not justified by the data.
- **Why it matters** Overinterpretation of computational predictions as functional evidence can mislead readers and potentially influence future research directions. The manuscript should clearly distinguish between hypothesis-generating predictions and established findings.
- **Resolution test** The authors should revise the Discussion and Conclusion to explicitly state that the functional consequences are hypotheses requiring experimental validation. Speculative statements about cancer mechanisms and therapeutic applications should be removed or clearly framed as untested predictions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The authors state that MD simulation was performed using the Desmond v6.3 program with the OPLS3e force field, TIP3P water model, and 0.15 M NaCl, over 100 ns.
- **Evidence pointer** Materials and methods, Molecular dynamics simulation analysis
- **Concern** Critical methodological details are missing: (1) the initial structure used for simulation (which PDB structure or homology model, and how the mutant was generated); (2) the simulation temperature and pressure coupling methods; (3) the number of replicates; (4) the equilibration protocol; (5) how convergence was assessed; (6) the specific commands or parameters used for PCA, DCCM, and FEL analyses. Without these details, the MD results cannot be reproduced or independently evaluated.
- **Why it matters** Reproducibility is a core requirement for computational studies. The lack of methodological detail prevents assessment of the validity of the MD simulation and the derived conclusions.
- **Resolution test** The authors must provide a complete description of the simulation setup, including structure preparation, system building, equilibration, production run parameters, and analysis protocols. If standard protocols were used, they should be cited explicitly.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** The table footnote states "Here, *more damaging SNPs (SNPs found to have functional significance by the 5 programs)." However, the table lists 9 SNPs, and the asterisk is applied to 5 of them. It is unclear which "5 programs" are being referenced, as the table includes columns for SIFT, PolyPhen-2 (HumDiv and HumVar), SNAP, PhD-SNP, and SNPs&Go, which is 6 prediction columns. The criteria for "functional significance" are not defined.
- **Required correction** Clarify the criteria for the asterisk designation and specify which programs were used for the consensus call. Consider adding a column indicating the number of tools that predicted deleterious/damaging effects for each SNP.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Accuracy
- **Affected element** Results, Hydrogen bonds analysis
- **Evidence pointer** Results, Molecular dynamics simulation analysis, Hydrogen bonds analysis; Figure 5D
- **Issue** The text states "Altered hydrogen bond counts for WT (149-331) and WT (142-318) indicate significant structural deviation from WT." The second "WT" should presumably read "mutant" or "D85H." This appears to be a typographical error.
- **Required correction** Correct the typo to read "Altered hydrogen bond counts for WT (149-331) and D85H (142-318) indicate significant structural deviation from WT."

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, Hydrogen bonds analysis; Discussion
- **Evidence pointer** Results, Molecular dynamics simulation analysis, Hydrogen bonds analysis; Discussion, paragraph 4
- **Issue** The manuscript reports that the mutant has a lower hydrogen bond count range (142-318) compared to WT (149-331), yet the Discussion states that "this mutant higher hydrogen bond count leads to structural instability rather than stabilisation." This is contradictory. The Results section reports fewer hydrogen bonds in the mutant, while the Discussion refers to a "higher hydrogen bond count."
- **Required correction** Reconcile the discrepancy between the Results and Discussion sections. If the mutant has fewer hydrogen bonds, the interpretation should be revised accordingly. If the Discussion refers to a different metric or a different mutant, this must be clarified.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, Protein three-dimensional modelling
- **Evidence pointer** Table 3
- **Issue** Table 3 reports "Confidence (%)" and "Coverage (%)" for the homology models, but the values are not clearly explained. The confidence values appear to be 57% for all models, and coverage values are 100% for WT and 99.8% for mutants. The text states "All mutations and wild-type proteins were shown with 57% confidence," but the table lists different values (e.g., 88, 89, 90 for alpha helix percentages). The relationship between the text and table is unclear.
- **Required correction** Clarify the meaning of the confidence and coverage values in the table and ensure consistency between the text and table. Explain what the 57% confidence value represents in the context of Phyre2 modeling.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, RMSD analysis
- **Evidence pointer** Results, Molecular dynamics simulation analysis, RMSD analysis; Figure 5A
- **Issue** The text states "Analysis revealed deviation patterns in mutants relative to the wild-type, showing highest peak RMSD values of 32.24 Å and 33.54 Å, respectively." It is unclear which protein corresponds to which value. Additionally, the average RMSD values reported in the text (29.51 Å and 29.71 Å) do not match the values in Supplementary Table S1 (29.54 ± 3.07 Å and 29.74 ± 3.53 Å). The source of these discrepancies is not explained.
- **Required correction** Clearly identify which RMSD values correspond to WT and which to the mutant. Reconcile the values reported in the text with those in Supplementary Table S1.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, FEL analysis
- **Evidence pointer** Results, FEL analysis; Figure 6C
- **Issue** The FEL analysis is described qualitatively ("scattered landscape," "stable conformation with reduced flexibility"), but no quantitative metrics are provided to support these interpretations. The free energy values, the number of minima, or the energy barriers between states are not reported.
- **Required correction** Provide quantitative descriptors of the free energy landscapes, such as the range of free energy values, the number and depth of minima, or the energy difference between the most stable and least stable states.

## Risk / unsupported claims
- The claim that D85H "may disrupt DNA binding, potentially weakening activation of chondrogenic targets and reducing repression of Wnt/beta-catenin signaling" is unsupported. No functional assays, binding studies, or pathway analyses were performed.
- The claim that the identified variants could enable "personalized therapeutic strategies like risk stratification, structure-guided inhibitor design, allele-specific RNA or gene-editing therapies" is speculative and not supported by the evidence presented.
- The statement that "the D85H variant within the HMG DNA-binding domain shows structural destabilization... which might reduce DNA-binding affinity, disrupt cofactor interactions, and dysregulate Wnt/beta-catenin signaling" is an overinterpretation of computational predictions.
- The MD simulation results, as reported, are not interpretable due to implausible RMSD values and incomplete methodological reporting. Any conclusions drawn from these simulations are currently unsupported.
- The claim that "all the selected lead mutants exhibited fewer stable results when compared with the native protein" is not supported by the data shown, as only one mutant (D85H) appears to have been simulated.
- The functional significance of the four prioritized SNPs is inferred solely from computational predictions without experimental validation, which is acknowledged by the authors but should be more prominently stated as a limitation throughout.