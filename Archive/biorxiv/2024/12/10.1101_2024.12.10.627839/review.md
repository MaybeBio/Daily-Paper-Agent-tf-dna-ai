## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, supplementary figure legends referenced but not provided)
- **Assessment boundary** Scientific content, technical soundness, and claims as presented in the provided text; no assessment of supplementary figures, tables, or deposited data beyond what is described
- **Shared manuscript claim summary** The manuscript reports the NMR solution structure of the Z0 domain (residues 46-72) of BCL11A, a CCHC-type zinc-finger, and characterizes its Zn2+-binding properties, thermostability, and sequence features distinguishing DNA-binding from non-DNA-binding zinc-fingers
- **Visible evidence base** Abstract; Introduction; Results sections 2.1-2.3; Materials and Methods sections 3.1-3.5; references to Figures 1-3, Supplementary Figures 1-4, Tables S1-S4; deposition numbers for BMRB (52414) and PDB (9BV0)
- **Missing materials affecting confidence** Supplementary figures (S1-S4), supplementary tables (S1-S4), NMR restraint statistics, structural quality metrics, sequence alignments for the four datasets, and the full list of 18 literature references for deletion analyses were not provided

## Reviewer

- **Overall assessment** This manuscript presents a solid biophysical characterization of the Z0 domain of BCL11A, including NMR structure determination, Zn2+ binding affinity measurements, and a bioinformatic analysis of sequence features distinguishing DNA-binding from non-DNA-binding zinc-fingers. The structural work appears technically sound, though the limited number of NOE restraints and lack of isotopic labeling raise questions about the precision of the structure. The sequence analysis is interesting but preliminary, with several methodological concerns that need addressing. The manuscript is clearly written and the topic is of interest to the structural biology and gene regulation communities, though the broader significance is somewhat limited by the narrow scope of the conclusions.

- **Who would be interested in the results, and why** Structural biologists studying zinc-finger domains and their metal-binding properties; researchers working on BCL11A as a therapeutic target for hemoglobinopathies, particularly given the recent FDA approval of Cas9-based therapy targeting BCL11A; computational biologists interested in sequence-function relationships in zinc-finger proteins; and investigators studying transcription factor oligomerization and protein-protein interactions mediated by zinc-finger domains.

- **Major strengths** The manuscript addresses a biologically relevant target (BCL11A) with therapeutic importance. The combination of CD, UV-vis, and NMR spectroscopy provides complementary evidence for Zn2+-induced folding and CCHC coordination geometry. The determination of a picomolar Kd for Zn2+ binding is noteworthy. The comparison of the NMR structure with ColabFold predictions provides validation. The sequence analysis addresses an important open question in the field regarding distinguishing DNA-binding from non-DNA-binding zinc-fingers.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of structure determination
- **Claim pointer** The manuscript claims to present an NMR solution structure of the Z0 domain with a prototypical beta-beta-alpha fold, with the structure converging to a unique solution with no irreconcilable restraint violations.
- **Evidence pointer** Section 2.2; Figure 2C; Table S1 (not provided)
- **Concern** The structure determination relied on only 26 long-range and 22 medium-range NOEs from D2O experiments, plus 5 long-range and 10 medium-range NOEs from H2O experiments. This is a very small number of restraints for a 27-residue peptide. The manuscript does not report the total number of NOE restraints used in the final structure calculation, the number of dihedral angle restraints, or the resulting structural statistics (RMSD values for the ensemble, Ramachandran plot statistics, restraint violations). Without these metrics, the quality and precision of the structure cannot be assessed. Additionally, the lack of isotopic enrichment means no 15N-based experiments were possible, limiting the ability to obtain backbone dynamics or additional structural restraints.
- **Why it matters** The central claim of the manuscript is the NMR structure of Z0. If the structure is poorly defined due to insufficient restraints, the conclusions drawn from it, including the identification of the hydrophobic knob and comparisons with other structures, may not be reliable.
- **Resolution test** Provide the complete restraint list, structural statistics table (including backbone and heavy atom RMSD to the mean structure, percentage of residues in favored/allowed/disallowed Ramachandran regions, number and magnitude of NOE and dihedral violations), and a superposition figure of the final ensemble. If the structure is not well-defined (e.g., backbone RMSD greater than 1.5 Å), the claims about the specific structural features should be tempered accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence for dimerization claims
- **Claim pointer** The manuscript states that the hydrophobic knob is likely to participate in the oligomerization function of the Z0 domain, and describes attempts to identify dimeric contacts from NOE data.
- **Evidence pointer** Section 2.2; Figure 2E; Supplementary Figures S2-S3 (not provided)
- **Concern** The manuscript reports that four NOEs were consistently violated in initial monomer structures and were excluded from structure calculations. The authors state that none of these were consistent with the concomitant presence of an oligomer, but the reasoning for this conclusion is not provided. The concentration-dependent line broadening experiments (Figure S2) and AlphaFold3 dimer modeling (Figure S3) are referenced but not shown or described in sufficient detail. The claim that the hydrophobic knob participates in oligomerization is speculative without direct experimental evidence such as a dimer structure, sedimentation equilibrium, or cross-linking data.
- **Why it matters** The potential oligomerization function of Z0 is presented as a significant aspect of the domain's biological role. Without solid evidence, this claim remains speculative and could mislead readers about the functional significance of the hydrophobic knob.
- **Resolution test** Provide the details of the line-broadening experiments, including the concentrations tested and the specific residues affected. Describe the AlphaFold3 modeling results more thoroughly, including confidence scores and whether the predicted interfaces are consistent across models. If direct evidence for dimerization is not available, revise the language to clearly indicate that the oligomerization function is inferred from the literature and the hydrophobic surface is a candidate interface requiring further validation.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Statistical analysis of sequence data
- **Claim pointer** The manuscript claims significant differences (p < 0.05) between DNA-binding and non-DNA-binding zinc-finger groups based on HMMR bit scores, and describes sequence logo differences between the groups.
- **Evidence pointer** Section 2.3; Figure 3A-C; Tables S2-S4 (not provided)
- **Concern** The statistical analysis appears limited to pairwise comparisons of means without correction for multiple testing. The manuscript does not describe the statistical test used, whether the data meet the assumptions of the test, or how the significance threshold was chosen. The sequence logo analysis is qualitative, and the claim that "DNA-binders are distinguished by contiguous stretches of high-scoring zinc-fingers" is not supported by a quantitative analysis. The control dataset for CCHC-fingers (converting them to CCHH) is described, but the rationale and the results of this control are only briefly mentioned.
- **Why it matters** The sequence analysis is presented as a potentially useful tool for distinguishing DNA-binding from non-DNA-binding zinc-fingers. If the statistical foundation is weak, the practical utility of these findings is questionable.
- **Resolution test** Describe the statistical tests used, including whether multiple testing corrections were applied. Provide the full results of the control experiment. Consider adding a quantitative analysis of the sequence logos, such as calculating information content at key positions or using a machine learning approach to classify DNA-binders versus non-binders. If the sample sizes are too small for robust statistics, acknowledge this limitation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility of sequence datasets
- **Claim pointer** The manuscript describes four datasets: DNA-binders X-ray (102 domains from 26 structures), DNA-binders Δ (57 domains), Non-DNA Δ (91 domains), and CCHC protein-binders (28 domains from 18 proteins).
- **Evidence pointer** Section 2.3; Section 3.4; Tables S2-S4 (not provided)
- **Concern** The criteria for inclusion in the DNA-binders Δ and Non-DNA Δ datasets are not described in sufficient detail. The manuscript states these were derived from 18 literature papers reporting deletion analyses, but does not specify how "necessary and sufficient for DNA-binding" was determined in each case, or how potential discrepancies between papers were resolved. The CCHC protein-binders dataset relies on "literature evidence for protein rather than DNA-binding functions," but the nature and quality of this evidence is not described. The decision to fill in missing C-terminal residues with glycines in five cases could introduce artifacts in the sequence logo analysis.
- **Why it matters** The conclusions drawn from the sequence analysis depend entirely on the quality and consistency of the underlying datasets. If the inclusion criteria are not transparent and reproducible, the results cannot be independently verified.
- **Resolution test** Provide detailed inclusion and exclusion criteria for each dataset, including the specific literature sources and how binding function was determined. Describe how conflicts between sources were resolved. Justify the glycine padding approach and discuss its potential impact on the sequence logo analysis. Consider making the datasets available as supplementary files.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Section 2.1, last paragraph
- **Evidence pointer** Section 2.1
- **Issue** The sentence "The analysis indicates that the Z0 peptide folds in the presence of Zn2+, but that there is a small amount of residual alpha-helix structure in the absence of metal at neutral pH, that becomes unfolded at acidic pH" is grammatically awkward and could be clearer.
- **Required correction** Revise to something like "The analysis indicates that the Z0 peptide folds in the presence of Zn2+. In the absence of metal at neutral pH, the peptide retains a small amount of residual alpha-helical structure, which becomes unfolded at acidic pH."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness of methods
- **Affected element** Section 3.3
- **Evidence pointer** Section 3.3
- **Issue** The methods for NMR structure calculation do not mention the software used for NOE assignment and structure validation beyond X-plor NIH. The manuscript also does not state how many structures were calculated in total and how the final 20 were selected beyond "lowest energy structures without violations."
- **Required correction** Add details on the assignment of NOEs (e.g., manual vs. automated), the protocol for structure validation (e.g., PROCHECK, MolProbity), and the criteria for selecting the final ensemble.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of CD data
- **Affected element** Section 2.1, Figure 1C
- **Evidence pointer** Section 2.1
- **Issue** The manuscript reports a Kd of (3.7 ± 0.3) x 10-12 M for Zn2+ binding using a competition assay with EGTA. The choice of EGTA as the competitor and the assumptions of the competition model are not discussed. The manuscript also does not report the stoichiometry of Zn2+ binding.
- **Required correction** Briefly justify the choice of EGTA and describe the competition model used. If stoichiometry was not determined, state this explicitly and discuss the potential impact on the Kd value.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Figure 2B
- **Evidence pointer** Section 2.2
- **Issue** The manuscript states that Figure 2B summarizes the chemical shift and short-range NOE data used to calculate consensus secondary structure, but the figure is not provided in the text. The description of the figure is insufficient to evaluate the quality of the secondary structure determination.
- **Required correction** Provide the figure or a more detailed description of the data shown, including the specific chemical shift indices and NOE patterns used to define the secondary structure elements.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Section 1, Introduction
- **Evidence pointer** Section 1
- **Issue** The introduction mentions that BCL11A has roles in brain and hematopoietic system development and may contribute to diseases such as type II diabetes and cancers, but does not provide specific references for these claims beyond a general citation to recent reviews.
- **Required correction** Add specific citations for the roles of BCL11A in brain development, hematopoiesis, and disease associations.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Section 2.3
- **Evidence pointer** Section 2.3
- **Issue** The term "CCHC-finger" is used to describe the subfamily, but the manuscript also refers to "CCHC-type ZNF" and "CCHC protein-binders" interchangeably. This could cause confusion, especially since the "knuckle-CCHC" subfamily is mentioned as distinct.
- **Required correction** Define the terminology clearly at first use and use consistent terms throughout the manuscript.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Section 3.5
- **Evidence pointer** Section 3.5
- **Issue** The manuscript states that the NMR assignments and structure were deposited in BMRB and PDB, but does not mention whether the sequence alignments and datasets used for the bioinformatic analysis are available.
- **Required correction** State where the sequence datasets and alignments can be accessed, or provide them as supplementary material.

## Risk / unsupported claims

- The claim that the hydrophobic knob "is likely to participate in the oligomerization function of the Z0 domain" is not directly supported by experimental evidence presented in the manuscript; it is inferred from the literature and the hydrophobic nature of the surface.
- The claim that "DNA-binders are distinguished by contiguous stretches of high-scoring zinc-fingers" is presented as a general principle but is only supported by qualitative observations from a limited dataset.
- The statement that the NMR structure "agrees with that predicted by ColabFold" with RMSDs of 1.3 Å and 2.1 Å is difficult to evaluate without knowing the confidence of the ColabFold prediction and the region over which the RMSD was calculated.
- The manuscript states that the Z0 domain is "thermostable" based on CD thermal denaturation, but the specific temperature range and the reversibility of the unfolding transition are not described in the provided text.
- The claim that the Kd for Zn2+ binding is picomolar relies on a competition assay with EGTA, but the manuscript does not provide the full details of the calculation or the error analysis.