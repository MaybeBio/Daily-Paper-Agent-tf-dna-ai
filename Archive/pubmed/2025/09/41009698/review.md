## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods, conclusions)
- **Assessment boundary** Scientific content, methodological soundness, structural logic, and internal consistency of the reported computational analysis
- **Shared manuscript claim summary** The authors report a systematic structural mapping of all TP53 mutations from the COSMIC database onto experimentally determined and AlphaFold-predicted structures, with classification by structural context and prediction of functional impact using multiple computational tools, to provide a framework for understanding chemoresistance.
- **Visible evidence base** Abstract, Introduction, Results, Discussion, Materials and Methods, Conclusions; references to Supplementary Figures S1, S2 and Supplementary Tables S1, S2; Table 1 referenced but not provided
- **Missing materials affecting confidence** Table 1 (referenced extensively but not included); Supplementary Figures S1, S2; Supplementary Tables S1, S2; PDB validation metrics; specific numerical results for most analyses; figure panels referenced (Figures 1-4) but not visible

## Reviewer
- **Overall assessment** This manuscript presents a large-scale computational analysis of TP53 mutations mapped onto structural data, with the stated goal of linking structural context to chemoresistance. The scope of the data integration is substantial, and the topic is of considerable interest to the cancer biology and structural biology communities. However, the manuscript in its current form has significant structural and presentational problems. The Results section contains incomplete sentences, abrupt transitions, and references to categories and tables that are not adequately introduced or explained. The link between the structural analysis and the specific claim about chemoresistance is asserted rather than demonstrated. The methodological details are insufficient to assess reproducibility, and several key claims are not supported by the evidence presented in the visible text. The manuscript would benefit from substantial revision to clarify the analytical framework, complete the presentation of results, and strengthen the connection between structural findings and chemoresistance mechanisms.

- **Who would be interested in the results, and why** Researchers in cancer genomics, structural biology, and precision oncology would find this work of interest. The systematic mapping of TP53 mutations onto structural contexts could serve as a reference resource for interpreting patient-derived mutations. Computational biologists developing or benchmarking structure-based prediction tools would also be interested in the comparative assessment of mCSM, FoldX, Maestro, and AlphaMissense. Clinicians and translational researchers focused on TP53-mutant cancers and chemoresistance may find the structural framework useful for generating hypotheses about mutation-specific therapeutic vulnerabilities.

- **Major strengths** The manuscript addresses a clinically important question with a comprehensive dataset, integrating COSMIC mutation data with all available experimental structures and AlphaFold predictions. The comparative use of multiple prediction tools is a reasonable approach to increase confidence in the findings. The identification of a subset of mutations with consistent destabilisation predictions across all structural contexts is potentially valuable. The discussion of Y220C as a druggable target is well-grounded in existing literature.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The abstract states that the analysis "revealed distinct mutational hotspots, differential distribution across structural regions, and context-dependent effects on stability and DNA-binding capacity."
- **Evidence pointer** Results section, Figures 2-3, Table 1 (not provided)
- **Concern** The Results section is incomplete and internally inconsistent. Sentences such as "Based on mutation frequency, TP53 variants are categorised into four groups" are followed by descriptions of categories without any indication of the grouping criteria or thresholds. The text jumps between categories without clear transitions or explanations. Table 1, which appears to be central to the presentation of hotspot mutations and their predicted effects, is not provided in the visible material. The referenced figures are not visible, making it impossible to verify the claimed distributions.
- **Why it matters** The central claims of the manuscript rest on the presentation of results that are not fully visible or clearly described. Without the complete results, the analysis cannot be evaluated for correctness, and the reader cannot assess whether the conclusions follow from the data.
- **Resolution test** Provide the complete Results section with all categories clearly defined, all tables and figures included, and all claims explicitly tied to specific data presentations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological reproducibility
- **Claim pointer** The Materials and Methods states that "mutations were mapped using multiple distance thresholds" and that "solvent accessibility was determined using the FreeSASA tool."
- **Evidence pointer** Materials and Methods, Section 4
- **Concern** The methodological description is insufficient for reproducibility. The specific distance thresholds used for mapping mutations to functional sites are not stated. The criteria for classifying residues as core, interface, or non-interface are given as SASA values, but the relationship between these classifications and the structural contexts described in the Results (e.g., "near ligand-binding sites," "around the zinc-binding site") is not defined. The integration of AlphaFold models with experimental structures is described only briefly, without details on how the models were aligned, which regions were covered, or how confidence scores were handled.
- **Why it matters** A computational study of this type must provide sufficient methodological detail for others to reproduce the analysis. The current description is too vague to allow replication or independent verification.
- **Resolution test** Provide explicit parameters for all analyses, including distance thresholds, alignment procedures, AlphaFold model selection criteria, and handling of low-confidence regions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The title and abstract claim a connection between structural disruption of TP53 and chemoresistance; the Discussion states that "structural analysis reveals that these mutations exert their effects through two primary mechanisms: direct disruption of DNA contact and indirect destabilisation of the domain architecture."
- **Evidence pointer** Abstract, Discussion, Section 3
- **Concern** The manuscript does not present any direct evidence linking the structural classifications to chemoresistance outcomes. No clinical data, drug response data, or functional assays are presented. The connection between structural destabilisation and chemoresistance is asserted based on prior literature rather than demonstrated by the current analysis. The claim that specific mutations "contribute to chemoresistance" is not supported by any data in the visible text.
- **Why it matters** The title and framing of the manuscript promise a structural approach to understanding chemoresistance, but the analysis presented is purely descriptive of mutation locations and predicted stability changes. Without any link to chemoresistance data, the central premise of the manuscript is not established.
- **Resolution test** Either reframe the manuscript to accurately reflect the descriptive nature of the analysis, or include data that directly connects the structural findings to chemoresistance outcomes.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The Results states that "In PDB ID: 8DC8, six mutations (I195K, Y234R, L145Q, L257P, L257Q) occur near the ligand-binding site" and that "three unfrquent mutations (V157E, Y234R, I195K) consistently appear in the core region."
- **Evidence pointer** Results section, Supplementary S2
- **Concern** There is an internal inconsistency in the reported numbers. The text lists six mutations near the ligand-binding site but names only five (I195K, Y234R, L145Q, L257P, L257Q). Additionally, Y234R and I195K are listed as being near the ligand-binding site in one context and in the core region in another, without explanation of how a single mutation can be classified in both contexts. The term "unfrquent" appears to be a typographical error for "infrequent."
- **Why it matters** Internal inconsistencies and typographical errors undermine confidence in the accuracy of the reported results and suggest insufficient proofreading.
- **Resolution test** Correct the inconsistencies, clarify the classification criteria for each structural context, and ensure all reported numbers are accurate.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The Results states that "complete agreement among the three structure-based prediction methods was observed for a subset of mutations. Specifically, agreement occurred for 326 mutations (33%) in 8DC8, 356 mutations (34%) in 7EEU, and 331 mutations (31%) in 8R1G."
- **Evidence pointer** Results section, Figure 4
- **Concern** The percentages reported do not match the stated denominators. For 8DC8, 326 out of 988 mutations is 33.0%, which is consistent. For 7EEU, 356 out of 1045 is 34.1%, which is consistent. For 8R1G, 331 out of 1060 is 31.2%, which is consistent. However, the text states that "the majority of mutations were classified as moderately destabilising, a smaller portion as highly destabilising, and only a minority as moderately stabilising" within these consensus sets, but no numerical breakdown is provided. The relationship between the consensus sets and the subsequent statement about "82 mutations classified as highly destabilising" in 7EEU is unclear.
- **Why it matters** The reader cannot determine how the consensus sets relate to the subsequent analysis of highly destabilising mutations, and the lack of numerical detail prevents verification of the claims.
- **Resolution test** Provide a clear breakdown of the consensus classifications and explicitly state how the 82 highly destabilising mutations were identified within the consensus framework.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness
- **Affected element** Results section, paragraph on mutation frequency categories
- **Evidence pointer** Results section, location not provided
- **Issue** The paragraph describing the four mutation frequency categories is incomplete. The text states "Based on mutation frequency, TP53 variants are categorised into four groups" and then describes categories without stating the frequency thresholds that define each group. The descriptions of the second, third, and fourth groups are fragmentary.
- **Required correction** Complete the paragraph with explicit definitions of each frequency category and ensure all four groups are fully described.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Discussion section, final paragraph
- **Evidence pointer** Discussion, location not provided
- **Issue** The final paragraph of the Discussion contains two incomplete sentences: "Future research should focus on:Structure-based drug discovery targeting druggable cavities like Y220C and other destabilised cores.Computational-experimental pipelines to screen and validate small molecules that restore TP53 folding and DNA-binding capacity." These appear to be bullet points that have been incorrectly formatted as running text.
- **Required correction** Format these as proper bullet points or complete sentences.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity and completeness
- **Affected element** Materials and Methods, solvent accessibility classification
- **Evidence pointer** Materials and Methods, Section 4
- **Issue** The classification thresholds for residue categories are given as "Core residues: SASA < 25," "Non-interface residues: 25 ≤ SASA ≤ 80," and "Interface residues: SASA > 80." However, the Results section also refers to "non-interface surface areas" and "interface regions" as distinct categories, and the relationship between these terms and the SASA-based classification is not explained.
- **Required correction** Clarify the terminology and ensure consistent use of categories throughout the manuscript.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Results section, PDB ID 8DC8 analysis
- **Evidence pointer** Results section, location not provided
- **Issue** The text states that PDB ID 8DC8 represents "the monomeric DNA-binding domain of TP53 (residues 91-289) bound to a zinc ion (Zn2+) and (R50) ligand." The notation "(R50) ligand" is unclear and does not correspond to standard ligand nomenclature.
- **Required correction** Clarify the identity of the ligand, using standard chemical or PDB ligand identifiers.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity and completeness
- **Affected element** Results section, PDB ID 7EEU analysis
- **Evidence pointer** Results section, location not provided
- **Issue** The text states "Analysis of the Homo 4-mer DNA-bound TP53 structure PDB ID: 2ATA, 7EEU [44] with R282W mutant." It is unclear whether the analysis was performed on one structure or two, and whether the R282W mutation is present in both.
- **Required correction** Clarify which PDB structures were used and the relationship between them.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Results section, consensus analysis
- **Evidence pointer** Results section, location not provided
- **Issue** The text states "Across all three structures, three unfrquent mutations (V157E, Y234R, I195K) consistently appear in the core region and are predicted as highly destabilising by all methods." The term "unfrquent" is a typographical error, and the claim that these mutations "consistently appear in the core region" across all three structures is difficult to evaluate without knowing the residue ranges covered by each structure.
- **Required correction** Correct the typographical error and provide the residue ranges of each structure to support the claim of consistent core localization.

## Risk / unsupported claims
- The claim that the analysis provides a "structural approach to understanding chemoresistance" is not supported by any direct evidence linking structural classifications to chemoresistance outcomes; this connection is asserted rather than demonstrated.
- The claim that "AlphaFold provides deeper insights into the mechanisms by which TP53 mutations disrupt protein function" is not supported by any specific analysis showing what the AlphaFold models contributed beyond the experimental structures.
- The statement that "the Y220C mutation creates a solvent-accessible cavity that has been successfully targeted in previous studies using small molecules to restore TP53 stability and function" is presented as a finding of this study but is a well-established fact from prior literature; the manuscript does not present any new data on Y220C druggability.
- The claim that "a subset of mutations with consistent predictions of high destabilisation across all structural contexts" was identified cannot be fully evaluated because the specific mutations and their classifications are not presented in the visible text.
- The statement that "complete agreement among the three structure-based prediction methods was observed for a subset of mutations" is not verifiable without the underlying data or a clear presentation of the consensus analysis.
- The claim that "mutations within IDRs may still perturb regulatory interactions with partners such as MDM2 and transcriptional co-activators" is speculative and not supported by any analysis presented in the manuscript.
- The manuscript states that "a total of 1472 unique TP53 variants were mapped onto 277 experimentally resolved 3D structures, accounting for 185,383 individual missense mutation events" but does not explain the relationship between unique variants and individual events, nor how the counting was performed.
- The claim that "the predicted AlphaFold model closely aligns with the experimental structure of the DNA-binding domain (PDB ID: 8DC8), showing an RMSD of 0.345" is presented without specifying the units or the alignment method, and the significance of this value is not discussed.