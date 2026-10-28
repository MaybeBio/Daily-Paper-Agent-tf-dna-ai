## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, materials and methods, and conclusions. Figures and supplementary materials referenced but not provided.
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the manuscript text. No assessment of editorial quality or journal fit beyond Nature-style criteria.
- **Shared manuscript claim summary** The authors report cloning and characterizing MdWRKY31, a group II WRKY transcription factor from apple (Malus × domestica), which is upregulated by cold stress, localizes to the nucleus, and when overexpressed in tomato enhances cold tolerance through improved antioxidant defense, osmotic adjustment, and activation of CBF-dependent and ABA-related signaling pathways. Molecular docking suggests direct binding of MdWRKY31 to W-box elements in the SlCBF1 promoter.
- **Visible evidence base** Text descriptions of results, including qRT-PCR expression data, physiological measurements (SOD, POD, CAT, proline, soluble protein, MDA, H2O2, O2−), survival rates, subcellular localization, phylogenetic analysis, and molecular docking predictions. Figures S1, S2, and Figures 1–6 are referenced but not provided.
- **Missing materials affecting confidence** All figures and supplementary materials, including raw data, statistical details, Western blots, staining images, and docking output. Experimental details for transgenic line generation and confirmation are incomplete. No accession numbers for the MdWRKY31 sequence are provided.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant topic in plant stress biology, namely the role of a WRKY transcription factor in cold tolerance. The experimental approach is conventional and the data, as described, are consistent with the main conclusions. However, the study is largely descriptive and relies on heterologous overexpression in tomato, which limits the direct relevance to apple. The molecular docking claim is presented as evidence of regulatory function but is not experimentally validated. Several technical details are missing, and the mechanistic depth is insufficient for the claims made. The work may be of interest to specialists in fruit tree stress physiology, but it does not currently meet the standard of a high-impact general journal.
- **Who would be interested in the results, and why** Researchers working on WRKY transcription factors, cold stress signaling in plants, and fruit tree abiotic stress tolerance. The identification of MdWRKY31 as a candidate gene for breeding cold-resistant apple may also interest applied plant breeders. The study is unlikely to attract a broad readership beyond these specialized groups.
- **Major strengths** The study addresses an important agronomic problem, cold stress in apple. The experimental design includes multiple physiological parameters and gene expression analyses. The use of heterologous expression in tomato is a practical approach for functional characterization. The identification of a candidate gene for breeding is a useful contribution.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that MdWRKY31 overexpression in tomato enhances cold tolerance based on physiological measurements and survival rates.
  - **Evidence pointer** Section 2.3, Section 2.4, Figures 3 and 4 (not provided)
  - **Concern** The manuscript states that T2 transgenic lines were used, but no data are shown confirming the presence and expression of the transgene at the protein level. Western blot or at least semi-quantitative RT-PCR data for MdWRKY31 protein/transcript in the selected lines are not described. Furthermore, the number of independent transgenic events is not stated, and it is unclear whether the three lines (S2, S5, S8) represent independent transformation events or clonal replicates. This is critical for excluding position effects or insertional mutations as the cause of the observed phenotype.
  - **Why it matters** Without confirmation of transgene expression at the protein level and demonstration of independence of the lines, the observed phenotype cannot be reliably attributed to MdWRKY31 function. This is a fundamental requirement for functional characterization studies.
  - **Resolution test** Provide Western blot data for MdWRKY31 in the three lines, state the number of independent transformation events, and show that the phenotype correlates with expression level across independent lines.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Support for claims
  - **Claim pointer** The authors claim that molecular docking shows MdWRKY31 has strong binding affinity to W-box elements in the SlCBF1 promoter, suggesting direct regulation.
  - **Evidence pointer** Section 2.6, Figure 6 (not provided)
  - **Concern** Molecular docking is a predictive tool and cannot establish physical binding. The claim that MdWRKY31 "may regulate the expression of these genes through direct protein–DNA interactions" is presented as a finding, but no experimental validation (EMSA, ChIP-qPCR, or dual-luciferase reporter assay) is provided. The authors acknowledge this limitation in the Discussion, but the Results section presents the docking as a substantive result. The docking model between MdWRKY31 and SlCBF1 protein is also mentioned, but its relevance is unclear and not experimentally supported.
  - **Why it matters** The regulatory mechanism is a central claim of the manuscript. Presenting in silico predictions as evidence of regulation without experimental validation is insufficient and could mislead readers.
  - **Resolution test** Either remove the docking data from the Results and present it only as a hypothesis, or provide experimental evidence of binding (EMSA, ChIP-qPCR, or reporter assays).
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that MdWRKY31 is localized in the nucleus based on transient expression in tobacco leaves.
  - **Evidence pointer** Section 2.2, Figure 2 (not provided)
  - **Concern** The subcellular localization experiment is described, but no details are given regarding the number of independent transformations, the percentage of cells showing nuclear localization, or whether a nuclear marker was used. The text mentions co-expression with pBI221-mCherry, but it is not clear if this was used as a nuclear marker or for another purpose. Without these details and the actual images, the localization claim cannot be fully evaluated.
  - **Why it matters** Nuclear localization is consistent with the proposed transcription factor function and is a key piece of evidence. Incomplete reporting weakens this claim.
  - **Resolution test** Provide representative images with a nuclear marker, state the proportion of cells with nuclear signal, and describe the controls used.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors claim that MdWRKY31 improves cold tolerance by CBF-dependent pathways to modulate antioxidant defenses and osmotic balance.
  - **Evidence pointer** Sections 2.4, 2.5, 2.6, Figures 4 and 5 (not provided)
  - **Concern** The mechanistic model is inferred from gene expression changes and physiological measurements in a heterologous system. The connection between MdWRKY31, CBF pathway activation, and the observed physiological changes is correlative. The authors do not demonstrate that the CBF genes are direct targets of MdWRKY31, nor do they show that the antioxidant and osmotic changes are dependent on CBF activation. The relevance of these findings to apple, the actual target crop, is not experimentally addressed.
  - **Why it matters** The title and conclusions imply a regulatory role in apple cold tolerance, but all functional data come from tomato. Without experiments in apple (e.g., RNAi or CRISPR lines, or at least apple callus), the significance for apple breeding remains speculative.
  - **Resolution test** Provide experimental evidence in apple or apple-derived tissues, or temper the conclusions to clearly state that the findings are from a heterologous system and require validation in apple.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Section 2.1
  - **Evidence pointer** Figure 1 (not provided)
  - **Issue** The text states that MdWRKY31 is 1836 bp in length encoding a 611-amino-acid protein. It is unclear whether 1836 bp refers to the coding sequence or the genomic sequence including introns. This should be clarified.
  - **Required correction** Specify whether the length refers to the CDS or genomic DNA, and provide the accession number for the sequence.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Section 4.6
  - **Evidence pointer** Location not provided
  - **Issue** The transformation protocol is described briefly, but the number of independent transgenic events obtained, the selection marker used, and the method for confirming stable integration (e.g., PCR, Southern blot) are not stated.
  - **Required correction** Provide details on the number of independent events, selection method, and molecular confirmation of stable transformation.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Section 4.10
  - **Evidence pointer** Location not provided
  - **Issue** The statistical methods are described, but it is not stated how many biological replicates were used for the physiological measurements and whether the data met assumptions for ANOVA. The number of plants per line used in the cold tolerance assay is not given.
  - **Required correction** Specify the number of biological replicates and plants per line, and state whether data were tested for normality and homogeneity of variance.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Section 2.6
  - **Evidence pointer** Figure 6 (not provided)
  - **Issue** The docking analysis between MdWRKY31 and SlCBF1 protein is mentioned, but the biological rationale for this protein-protein interaction is not explained. It is unclear what functional significance this interaction would have.
  - **Required correction** Either provide a clear hypothesis for the protein-protein interaction or remove this data point.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Section 2.1
  - **Evidence pointer** Figure S1 (not provided)
  - **Issue** The secondary and tertiary structure predictions are mentioned, but their relevance to the study is not discussed. It is unclear what insight these predictions provide.
  - **Required correction** Either explain the relevance of the structural predictions or remove them.

## Technical failings that need to be addressed before the case is established
- Lack of protein-level confirmation of transgene expression in tomato lines (R1-M1).
- Molecular docking presented as evidence of regulation without experimental validation (R1-M2).
- Incomplete details on subcellular localization experiments (R1-M3).
- No experimental validation in apple, despite claims relevant to apple breeding (R1-M4).
- Missing information on transgenic line independence and number of events (R1-M1, R1-m2).

## Risk / unsupported claims
- The claim that MdWRKY31 regulates SlCBF1 through direct protein-DNA interaction is unsupported; only in silico docking is provided.
- The claim that MdWRKY31 improves cold tolerance via CBF-dependent pathways is correlative and not mechanistically demonstrated.
- The relevance of the findings to apple cold tolerance is asserted but not experimentally tested.
- The statement that MdWRKY31 is an "early-responsive transcription factor" is based on a single time-course experiment and is not strongly supported.
- The claim that MdWRKY31 "potently activated cold stress signaling" is an overstatement based on gene expression data alone.

## Assessment against Nature-style criteria
- **Originality** Moderate. The study adds MdWRKY31 to the list of WRKY transcription factors implicated in cold tolerance, but the approach and findings are largely consistent with prior work on other WRKY genes. No novel mechanism or unexpected finding is presented.
- **Scientific importance** Limited. The work is of interest to a specialized audience working on fruit tree stress physiology, but the lack of mechanistic depth and absence of validation in the target crop reduce its broader significance.
- **Interdisciplinary readership** Low. The manuscript is unlikely to attract readers outside plant stress biology and horticulture.
- **Technical soundness** The experimental design is generally sound, but key technical details are missing (transgene confirmation, line independence, statistical replication). The molecular docking claim is not experimentally validated.
- **Readability for nonspecialists** The manuscript is clearly written and accessible to a broad biological audience, but the specialized topic and lack of broader context limit its appeal.

## Recommendation posture
Currently not established from the provided evidence. The manuscript presents a descriptive characterization of MdWRKY31 with correlative data. The major claims regarding regulatory mechanism and relevance to apple breeding require additional experimental support, including protein-level confirmation of transgene expression, validation of the proposed DNA-binding interaction, and ideally functional studies in apple or apple-derived tissues. The study may be suitable for a specialized journal after these concerns are addressed.