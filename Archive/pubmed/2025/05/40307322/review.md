## Review setup
- **Input scope** Full manuscript text including Introduction, Materials and Methods, Results, Discussion, Conclusion, and figure legends. Supplementary information referenced but not provided.
- **Assessment boundary** Scientific validity, technical soundness, logical coherence, and support of claims by presented evidence. No assessment of editorial fit or language polishing.
- **Shared manuscript claim summary** The authors propose that AKBA alleviates ARDS by anchoring to BST2 on HPMECs, that unphosphorylated STAT1 (U-STAT1) binds to the BST2 promoter to drive its transcription, and that this pathway reduces autophagy, apoptosis, and inflammation in vitro and in vivo.
- **Visible evidence base** Figures 1-10, supplementary figures S1-S3 referenced, tables S1-S3 referenced. Raw data, statistical outputs, and supplementary files not provided.
- **Missing materials affecting confidence** Supplementary figures S1-S3, tables S1-S3, full Western blot images, CHIP-qPCR primer sequences and validation data, molecular docking scoring details, raw transcriptomic and proteomic datasets, and complete statistical reporting.

## Reviewer
- **Overall assessment** The manuscript addresses a potentially interesting question, namely whether AKBA, a boswellic acid derivative, can protect against ARDS through a BST2-dependent mechanism involving U-STAT1. The authors present a large body of in vitro and in vivo data. However, the central mechanistic claim, that U-STAT1 binds to the BST2 promoter to drive transcription, is supported by only one CHIP-qPCR experiment with no IgG control shown in the main text, no primer validation, and no demonstration of specificity. The causal chain from AKBA anchoring to BST2, to STAT1 activation, to BST2 transcription, to functional protection, is not rigorously established. Several experiments lack appropriate controls, and some statistical descriptions are incomplete. The current evidence does not fully support the title's definitive assertion.
- **Who would be interested in the results, and why** Researchers studying ARDS pathophysiology, endothelial cell biology, natural product pharmacology (specifically boswellic acids), and transcriptional regulation by unphosphorylated STAT proteins. The potential link between a natural compound and a specific molecular pathway in a clinically relevant disease model would be of interest if the mechanism were more rigorously established.
- **Major strengths**
  1. The study combines in vitro, in vivo, and multi-omics approaches, which is commendable in scope.
  2. The use of clinically relevant models (LPS for in vitro, CLP for in vivo) strengthens translational relevance.
  3. The identification of BST2 as a potential AKBA target via docking and CETSA is an interesting starting point.
  4. The inclusion of patient samples, albeit small, adds a translational dimension.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Mechanistic claim
- **Claim pointer** "Unphosphorylated STAT1 binds to the BST2 transcription promoter" and "STAT1 may be a transcription factor of BST2" (Results, CHIP-qPCR section; Discussion).
- **Evidence pointer** Figure 5M-N; Methods section "CHIP-qPCR"
- **Concern** The central mechanistic claim rests on a single CHIP-qPCR experiment. The methods section is extremely brief and lacks critical details: no primer sequences for the BST2 promoter region, no validation of chromatin shearing, no positive or negative control loci, and no demonstration that the antibody specifically immunoprecipitates U-STAT1 versus total STAT1. The figure legend states "IgG served as an antibody control" but the results text does not describe the IgG signal. Without these controls and details, the binding event cannot be considered established.
- **Why it matters** The title and the entire mechanistic model depend on this direct interaction. If U-STAT1 does not bind the BST2 promoter, the proposed pathway collapses. The current evidence is insufficient to support this claim.
- **Resolution test** Provide full CHIP-qPCR methodology including primer sequences, shearing validation, a clear IgG control with quantified signal, and ideally a second independent method such as electrophoretic mobility shift assay (EMSA) or a luciferase assay with a mutated STAT1 binding site. Show that the STAT1 antibody used can distinguish U-STAT1 from YP-STAT1.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Causal logic
- **Claim pointer** "AKBA can significantly reduce the inflammation and apoptosis of CLP induced lung tissue in mice, inhibit LPS-induced autophagy of HPMECs and protect cell proliferation migration and tube formation" and the implication that this is mediated by BST2 and STAT1.
- **Evidence pointer** Figures 1, 2, 6, 7, 8, 9, 10
- **Concern** The manuscript demonstrates correlations and rescue effects but does not establish causality. The knockdown and overexpression experiments (sh-BST2, sh-STAT1, OE-BST2, OE-STAT1) are used to show that these genes are necessary and sufficient for AKBA's effects. However, the logic is incomplete. For example, if AKBA works by increasing BST2, then knocking down BST2 should abolish AKBA's protective effect. The data in Figures 6 and 7 appear to show this, but the rescue experiment with recombinant BST2 protein (HY-P75469) is only shown in vivo (Figure 6) and not in vitro. Furthermore, the relationship between STAT1 and BST2 is not tested in a linear fashion. Does OE-STAT1 rescue the effect of sh-BST2? Does OE-BST2 rescue the effect of sh-STAT1? These epistasis experiments are essential to support the proposed linear pathway.
- **Why it matters** Without epistasis experiments, alternative explanations remain. For example, STAT1 and BST2 could act in parallel pathways, both contributing to AKBA's effects, rather than in a linear pathway where STAT1 drives BST2. The proposed model is not uniquely supported by the data.
- **Resolution test** Perform epistasis experiments. For example, in LPS-treated HPMECs with sh-STAT1, add OE-BST2 and assess whether AKBA's protective effects are restored. Conversely, in cells with sh-BST2, add OE-STAT1 and assess whether BST2 expression is increased and whether AKBA's effects are restored. This would test the linearity of the proposed pathway.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical validation
- **Claim pointer** "the anchoring sites may be GLN-87, ALA-88 and ASN-92" and "BST2 may be indispensable for AKBA to recognize and anchor HPMECs" (Results, Figure 5C; Discussion).
- **Evidence pointer** Figure 5C; Methods section "Molecular docking and molecular dynamics simulation"
- **Concern** The molecular docking and molecular dynamics simulation are used to support the claim that AKBA anchors to BST2. However, the methods section is confusing and contains errors. It mentions "HNADOCK takes the information of base pairing between Rnas into account" which is irrelevant for a protein-small molecule docking. The docking program is described as "hierarchical FFT HDOC global docking program" which is not a standard name. The scoring function and the validation of the docking protocol are not described. The MD simulation parameters are incomplete. The claim of specific anchoring sites (GLN-87, ALA-88, ASN-92) is made without any experimental validation, such as mutagenesis.
- **Why it matters** The physical interaction between AKBA and BST2 is a foundational claim. If the docking is not performed correctly or is not validated, the entire premise of "AKBA anchoring" is unsupported. The methods as written are not reproducible.
- **Resolution test** Provide a clear, standard description of the docking software and protocol, including the preparation of the protein and ligand structures, the search space, and the scoring function. Validate the docking results with a positive control. Experimentally test the predicted binding site by mutating GLN-87, ALA-88, and ASN-92 and assessing AKBA binding via CETSA or surface plasmon resonance.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Data interpretation
- **Claim pointer** "AKBA can effectively alleviate the decreased proliferation ability of HPMECs induced by LPS" and "AKBA treatment can significantly reduce Bad level and protect lung tissue from apoptosis"
- **Evidence pointer** Figures 1, 2, 9, 10
- **Concern** The manuscript reports many experiments with statistical significance, but the effect sizes are often small and the biological relevance is unclear. For example, in Figure 1, the differences between LPS and LPS+AKBA groups, while statistically significant, appear modest. The manuscript does not discuss whether these magnitudes are clinically or biologically meaningful. Additionally, the statistical methods are not fully described. The methods state "One-way ANOVA analysis was used between multiple groups, while Least Significance Difference was used to compare the difference of two groups." LSD is not appropriate for multiple comparisons without a significant overall F-test, and it inflates Type I error. The use of "n=3" for most in vitro experiments is low, and no power analysis is provided.
- **Why it matters** The conclusions are based on the assumption that the observed differences are meaningful. If the effect sizes are small and the statistical approach is flawed, the conclusions may not be robust.
- **Resolution test** Provide a more rigorous statistical analysis, including appropriate multiple comparison corrections (e.g., Tukey's HSD or Bonferroni). Report effect sizes and confidence intervals. Justify the sample sizes with a power analysis. For key experiments, consider increasing the number of independent replicates.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Model relevance
- **Claim pointer** "AKBA can significantly reduce the inflammation and apoptosis of CLP induced lung tissue in mice" and the implication that this is a model of ARDS.
- **Evidence pointer** Figures 2, 6, 10
- **Concern** The CLP model is a model of sepsis, which can lead to ARDS, but it is not a direct model of ARDS. The manuscript does not clearly establish that the lung injury observed is specifically ARDS-like (e.g., through measurement of arterial oxygenation, lung compliance, or histological criteria such as hyaline membranes). The authors use histological scoring and wet-to-dry ratio, which are supportive but not definitive. The translational relevance to human ARDS, where the initiating insult is often direct lung injury (pneumonia, aspiration), is not fully discussed.
- **Why it matters** The clinical relevance of the findings depends on the model accurately reflecting human ARDS. If the model is primarily a sepsis model, the conclusions may not generalize to ARDS from other causes.
- **Resolution test** Provide additional characterization of the lung injury in the CLP model, such as PaO2/FiO2 ratio, lung compliance, or evidence of hyaline membrane formation. Discuss the limitations of the CLP model as a model of ARDS and consider validating key findings in a direct lung injury model (e.g., intratracheal LPS or acid aspiration).

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Title
- **Evidence pointer** Title
- **Issue** The title states "Unphosphorylated STAT1 binds to the BST2 transcription promoter, promoting increased AKBA anchoring on HPMECs to alleviate ARDS." This is a very strong and specific mechanistic claim. Given the concerns raised in R1-M1, the title overstates the certainty of the findings.
- **Required correction** Consider softening the title to reflect the correlative nature of the evidence, for example, "STAT1 and BST2 are implicated in AKBA-mediated protection against ARDS in preclinical models."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, CHIP-qPCR
- **Evidence pointer** Methods section "CHIP-qPCR"
- **Issue** The CHIP-qPCR methods are described in a single sentence. Critical details such as the antibody catalog number, the amount of chromatin used, the number of cells per IP, and the qPCR conditions are missing.
- **Required correction** Provide a full, detailed CHIP-qPCR protocol, including all reagents, antibody information, primer sequences, and cycling conditions. This is essential for reproducibility.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data presentation
- **Affected element** Figure 5
- **Evidence pointer** Figure 5C
- **Issue** The molecular docking figure is not described in the legend. It is unclear what is being shown. The legend states "Molecular docking results and site prediction of AKBA and BST2" but does not explain the visualization.
- **Required correction** Expand the figure legend to explain the docking pose, the protein surface, the ligand, and the predicted interacting residues.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** All figures
- **Evidence pointer** Figure legends
- **Issue** The figure legends state "n=3" or "n=5" but do not specify what n represents (e.g., number of independent experiments, number of biological replicates, number of technical replicates). The type of error bars (SD vs. SEM) is stated in the methods but not consistently in the legends.
- **Required correction** Clarify in each figure legend what n represents and what the error bars indicate. Ensure consistency between methods and legends.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Logical consistency
- **Affected element** Results, Figure 1
- **Evidence pointer** Figure 1H-K
- **Issue** The text states "there was no significant difference between the control group and LPS group" for migration, but the figure appears to show a difference. This is confusing.
- **Required correction** Re-check the statistical analysis and the figure. Ensure the text accurately reflects the data.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Patient data
- **Evidence pointer** Methods section "Patient specimen acquisition"
- **Issue** The patient cohort is small (15 per group) and no demographic or clinical data are provided. It is unclear if the groups are matched for age, sex, or other relevant variables.
- **Required correction** Provide a table of patient demographics and clinical characteristics. Discuss the limitations of the small sample size.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Methods, Molecular dynamics
- **Evidence pointer** Methods section "Molecular docking and molecular dynamics simulation"
- **Issue** The methods section contains an error: "HNADOCK takes the information of base pairing between Rnas into account" is irrelevant for a protein-ligand docking. This suggests a copy-paste error from a different protocol.
- **Required correction** Correct the methods section to accurately describe the software and protocol used for protein-small molecule docking.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion speculates about ISG15-mediated ISGylation maintaining BST2 and U-STAT1 expression, but no data are presented to support this. This is presented as a hypothesis, which is fine, but it should be clearly labeled as such.
- **Required correction** Clearly distinguish between findings and speculation. The ISG15 hypothesis should be presented as a future direction, not as a conclusion of this study.

## Risk / unsupported claims
- The direct binding of U-STAT1 to the BST2 promoter is not established due to insufficient CHIP-qPCR details and lack of controls.
- The claim that BST2 is the "anchor" for AKBA on HPMECs is based on docking and CETSA but lacks experimental validation of the specific binding sites.
- The linear pathway AKBA -> U-STAT1 -> BST2 -> protection is not tested with epistasis experiments and is therefore not uniquely supported.
- The claim that AKBA "alleviates ARDS" is based on a CLP model, which is a sepsis model, and the manuscript does not provide definitive evidence of ARDS-specific pathology.
- The clinical relevance of the patient data is limited by the small sample size and lack of demographic information.
- The statistical approach (LSD for multiple comparisons) is not robust and may lead to inflated Type I error rates.
- The manuscript does not provide raw data or full Western blots, limiting the ability to assess data quality.