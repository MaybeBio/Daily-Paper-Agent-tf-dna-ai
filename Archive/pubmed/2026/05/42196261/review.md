## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodological rigor, validity of conclusions, and adherence to Nature-style standards
- **Shared manuscript claim summary** The authors present a computational analysis of SPI1 missense mutations, identifying nine deleterious variants, evaluating their structural and stability impacts, and assessing cinnamic acid as a potential ligand for the PU.1 ETS domain via molecular docking and ADMET profiling
- **Visible evidence base** Abstract, Introduction, Results (Sections 2.1-2.12), Discussion, Materials and Methods, Conclusions
- **Missing materials affecting confidence** Figures 1-9, Tables 1-5, supplementary data, PDB structure identifiers, and raw computational outputs were not available for independent verification

## Reviewer

- **Overall assessment** This manuscript presents a purely computational study combining variant effect prediction, structural modeling, and ligand docking. While the workflow is systematic and the authors acknowledge several limitations, the study lacks experimental validation, comparative benchmarking, and methodological depth in several areas. The conclusions drawn are largely consistent with the computational evidence presented, but the scientific impact is limited by the absence of novel methodological approaches or experimentally validated findings. The manuscript would benefit from substantial revision to clarify methodological choices, strengthen the docking analysis, and temper overinterpretation of computational predictions.

- **Who would be interested in the results, and why** Researchers in computational biology, structural bioinformatics, and cancer genomics may find the variant prioritization workflow of interest. Investigators studying SPI1/PU.1 function in hematopoiesis and leukemia could use the identified variants as candidates for experimental validation. The docking analysis of cinnamic acid may interest medicinal chemists exploring natural product scaffolds, though the weak binding affinity limits immediate therapeutic relevance.

- **Major strengths** The study addresses a relevant gap in understanding missense variants in SPI1, a transcription factor critical for hematopoiesis. The use of multiple complementary computational tools for variant prioritization and stability prediction is methodologically sound. The authors appropriately restrict structural analysis to the ETS domain, avoiding artifacts from disordered regions. The acknowledgment of limitations and proposal of future experimental directions is commendable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that nine nsSNPs were "consistently predicted to be deleterious across all tools employed" and that these represent pathogenic variants with implications for hematopoietic dysregulation and leukemogenesis.
- **Evidence pointer** Section 2.1, Table 1
- **Concern** The manuscript does not provide the specific predictions from each individual tool for each variant. Without this data, it is impossible to assess whether the "consensus" designation is meaningful or driven by a single tool. Furthermore, the authors do not compare their predictions against established variant effect databases such as ClinVar, gnomAD, or cancer-specific mutation databases (e.g., COSMIC). The claim of pathogenicity is therefore unsupported by population frequency data or clinical annotations.
- **Why it matters** The central claim of the paper rests on the reliability of the variant prioritization. Without transparent reporting of per-tool predictions and cross-referencing with known databases, the biological significance of the nine identified variants cannot be evaluated.
- **Resolution test** Provide a supplementary table with individual tool predictions for all 825 variants and the nine prioritized ones. Cross-reference the nine variants against ClinVar, gnomAD allele frequencies, and COSMIC to establish whether any have been previously reported in patients or are absent from healthy populations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that molecular docking of cinnamic acid into the PU.1 ETS domain produced a "reproducible interaction" with a binding affinity of −4.27 kcal/mol, and that this represents a "fragment-like" binding mode.
- **Evidence pointer** Sections 2.9, 2.10, Figure 6, Figure 7
- **Concern** A binding affinity of −4.27 kcal/mol is extremely weak and within the range of non-specific binding. The authors do not provide a comparative analysis with known PU.1 binders, DNA-bound conformations, or a decoy set to establish specificity. The docking grid was centered at (6, −2, −9) Å, but the rationale for this grid placement is not provided. The re-docking validation is mentioned but no RMSD value is reported to demonstrate the protocol's accuracy. The claim that cinnamic acid "binds" the ETS domain is therefore not established.
- **Why it matters** The docking analysis is a major component of the paper and the basis for suggesting cinnamic acid as a scaffold for therapeutic development. Weak, potentially non-specific binding does not support this conclusion.
- **Resolution test** Report the RMSD from re-docking validation. Provide docking results for a set of decoy compounds or known non-binders to demonstrate specificity. Justify the grid placement with reference to known functional sites. If possible, compare with a known PU.1 inhibitor or DNA fragment to contextualize the binding energy.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors conclude that "cinnamic acid is a structurally simple yet pharmacologically versatile framework which could be used as starting point for rational derivatization and optimization to improve target specificity and therapeutic potential."
- **Evidence pointer** Sections 2.11, 2.12, 5
- **Concern** The ADMET predictions are presented as favorable, but the predicted hepatotoxicity risk (probability 0.91) is a major liability that is mentioned only briefly. The Swiss Target Prediction results show a multi-target profile with the highest probability being only 0.887 for HCAR2, which is not a known target for leukemia therapy. The connection between cinnamic acid's predicted targets and the proposed therapeutic application in leukemia is not established. The conclusion overreaches the evidence.
- **Why it matters** The therapeutic implications suggested in the conclusion are not supported by the computational data. A compound with high predicted hepatotoxicity and weak, non-specific target engagement does not constitute a viable lead scaffold.
- **Resolution test** Provide a more balanced interpretation of the ADMET data, specifically addressing the hepatotoxicity risk. Discuss how the predicted targets relate to leukemia biology. If the compound is proposed as a scaffold, provide specific medicinal chemistry strategies to address the identified liabilities.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors state that "SPI1 expression was significantly upregulated in LAML tumor tissue compared to normal tissue" based on TCGA analysis.
- **Evidence pointer** Section 2.8, Figure 5
- **Concern** The statistical analysis is not described. The authors report p < 0.01 but do not specify the statistical test used, whether multiple testing correction was applied, or the sample sizes in each group. The choice of normal tissue comparator for LAML is problematic, as bone marrow or peripheral blood from healthy donors would be the appropriate control, not solid tissue normal samples.
- **Why it matters** The expression analysis is used to support the relevance of SPI1 in leukemia. If the statistical approach or comparator selection is inappropriate, this conclusion is weakened.
- **Resolution test** Describe the statistical test used, report sample sizes, and clarify the nature of the normal tissue comparator. If possible, validate the finding using an independent dataset or at least discuss the limitations of the TCGA normal comparator for LAML.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors used SWISS-MODEL to generate wild-type and mutant structures of the PU.1 ETS domain, and then performed structural alignment in UCSF Chimera to calculate Cα–Cα distances.
- **Evidence pointer** Sections 2.3, 4.4
- **Concern** The methodology for structural comparison is inadequately described. The authors do not specify which template structure was used for homology modeling, the sequence identity between the target and template, or the quality metrics of the generated models (e.g., QMEAN, GMQE). The Cα–Cα distance calculation is a limited metric that does not capture broader conformational changes. The statement that "I189F and H211P displayed a significant structural impact" based on distances of 0.302 Å and 0.365 Å is questionable, as these are very small displacements.
- **Why it matters** The structural analysis is used to differentiate between variants with "minimal" versus "significant" structural impact. Without proper model quality assessment and more comprehensive structural comparison metrics, these distinctions are not reliable.
- **Resolution test** Report template information, model quality scores, and provide a more comprehensive structural analysis (e.g., RMSD across the entire domain, secondary structure changes, side-chain interaction networks). Justify the threshold used to define "significant" structural impact.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.3, Figure 2
- **Evidence pointer** Section 2.3
- **Issue** The text states "The Cα–Cα distance between the wild-type and the other five missense mutant residues ranged from 0.010 Å to 0.060 Å (Figure 2." The figure reference is incomplete and the sentence structure is awkward.
- **Required correction** Complete the figure reference and rephrase for clarity.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.5, Table 3
- **Evidence pointer** Section 2.5
- **Issue** The PTM prediction scores are reported without context. The authors state "lysine 242 exhibited the highest score at 0.413" but do not explain what threshold was used to consider a site as a confident prediction.
- **Required correction** Provide the prediction thresholds used by MusiteDeep and justify the significance of the reported scores.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.6, Table 1
- **Evidence pointer** Section 2.6
- **Issue** The text refers to "Table 1 presents information about the predicted functional partners of SPI1" but Table 1 is described in Section 2.1 as listing the nine deleterious nsSNPs. The table numbering appears inconsistent.
- **Required correction** Verify table numbering and ensure correct cross-referencing throughout the manuscript.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 3, Discussion
- **Evidence pointer** Section 3
- **Issue** The Discussion section contains a run-on sentence: "The limitations of this study are as follows:The study is entirely in silico, lacking experimental validation (e.g., biochemical or cellular assays).Absence of positive and negative control ligands, limiting the interpretability of docking scores."
- **Required correction** Format the limitations list properly with appropriate spacing and punctuation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 4.10.3
- **Evidence pointer** Section 4.10.3
- **Issue** The docking protocol states "AutoDock Vina version 1.2.0 1.2.0" with a duplicated version number.
- **Required correction** Remove the duplicated version number.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 4.10.5
- **Evidence pointer** Section 4.10.5
- **Issue** The ADMET server is described as "https://admet.ai.greenstonebio.com/" but the specific tools used for each ADMET parameter are not described. The authors mention SwissADME in the abstract but not in the methods.
- **Required correction** Clarify which specific tools were used for which parameters and ensure consistency between abstract and methods.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Readability
- **Affected element** Section 2.12
- **Evidence pointer** Section 2.12
- **Issue** The text states "The Swiss Target Prediction analysis of cinnamic acid provided a multi-target interaction pattern involving G protein-coupled receptors (GPCRs), metabolic enzymes, ion channels, nuclear receptors, transporters, proteases, phosphatases and kinases" but does not discuss the relevance of these targets to the proposed therapeutic application.
- **Required correction** Add a brief discussion of how the predicted targets relate to the proposed use in hematologic disease.

## Risk / unsupported claims
- The claim that the nine identified variants are "pathogenic" is unsupported without population frequency data, clinical annotations, or functional validation.
- The claim that cinnamic acid demonstrates "reproducible binding" to the PU.1 ETS domain is not established given the weak affinity and lack of specificity controls.
- The conclusion that cinnamic acid is a viable scaffold for therapeutic development is not supported given the predicted hepatotoxicity and weak target engagement.
- The structural impact classification of variants (minimal vs. significant) is based on very small Cα–Cα displacements without clear biological relevance.
- The expression analysis conclusion relies on unspecified statistical methods and potentially inappropriate normal tissue comparators.
- The ADMET profile is presented as favorable despite a high predicted hepatotoxicity risk, which is a significant liability that is underemphasized.
- The PTM predictions are reported without validation against known post-translational modification databases or experimental evidence.
- The interaction network analysis is descriptive and does not provide quantitative evidence of the strength or specificity of the predicted interactions.
- The conservation analysis is limited to three species and does not include more distantly related organisms that could strengthen the evolutionary conclusions.
- The docking results are not contextualized with known PU.1 inhibitors or DNA-binding affinities, making the reported binding energy difficult to interpret.