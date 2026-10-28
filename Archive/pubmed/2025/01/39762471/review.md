## Review setup
- **Input scope** Full manuscript text, including Introduction, Materials and methods, Results, Discussion, Conclusion, and references to supplementary material. No figures or supplementary files were provided for review.
- **Assessment boundary** The review is limited to the content of the provided manuscript text. Figures, tables, and supplementary materials referenced in the text were not available for independent evaluation.
- **Shared manuscript claim summary** The authors present a computational pipeline integrating multiple in silico prediction tools, molecular dynamics simulations, and molecular docking to identify and characterize malignant non-synonymous single nucleotide polymorphisms (nsSNPs) in the FOXM1 gene that may be relevant to triple-negative breast cancer (TNBC) prognosis. Four nsSNPs (E235Q, R256C, G429E, S756P) were prioritized as potentially damaging based on consensus across prediction tools, and two (E235Q, S756P) were further characterized as most destabilizing via MD simulations and docking analyses.
- **Visible evidence base** The manuscript text includes descriptions of methods, results summaries, and two tables (Table 1 listing 76 high-risk nsSNPs; Table 2 listing 4 disease-associated nsSNPs; Table 3 with stability predictions; Table 4 with conservation and PTM data). Figures 1-6 are referenced but not provided. Supplementary Tables 1-3 and Supplementary Figures 1-2 are referenced but not provided.
- **Missing materials affecting confidence** Figures 1-6, all supplementary materials, the complete Table 1 data, and the full SNP dataset from dbSNP were not available. This substantially limits the ability to verify the accuracy of reported results, the quality of structural models, and the validity of simulation analyses.

## Reviewer
- **Overall assessment** This manuscript describes a straightforward computational workflow for prioritizing potentially deleterious nsSNPs in FOXM1, a gene of established relevance to TNBC. The methodological approach is conventional and follows patterns widely used in the literature. However, the study lacks experimental validation, does not establish a clear link between the identified variants and TNBC-specific biology beyond what is already known about FOXM1 overexpression, and contains several internal inconsistencies and methodological ambiguities that undermine confidence in the conclusions. The claim that these variants are "malignant" or clinically relevant to TNBC is not supported by the evidence presented, which is entirely computational and predictive in nature.
- **Who would be interested in the results, and why** Researchers working on FOXM1 biology or TNBC genetics might find the prioritized SNP list a useful starting point for future experimental studies. The paper could also serve as a template for similar computational SNP prioritization studies in other genes. However, the audience is likely narrow, as the findings are hypothesis-generating rather than definitive, and the TNBC-specific relevance is asserted rather than demonstrated.
- **Major strengths** The study uses multiple complementary computational tools to increase confidence in SNP prioritization, which is a reasonable strategy. The inclusion of MD simulations and docking analyses adds a structural dimension beyond simple sequence-based prediction. The authors are transparent about the need for future in vitro validation.
- **Major Concerns** The core conclusion that specific nsSNPs are "malignant" and relevant to TNBC is not established by the data. The study is purely computational and predictive, with no experimental validation, no patient cohort analysis, and no functional assays. The link between the identified variants and TNBC, as opposed to cancer in general or FOXM1 function broadly, is not demonstrated. There are also significant methodological ambiguities and apparent inconsistencies in the reported results that need clarification.
- **Minor Comments** Several statements in the Discussion appear to contain errors or inconsistencies with the Results section. The writing contains some typographical and grammatical errors. The rationale for choosing Olaparib as the control drug, while explained, could be more thoroughly justified given that FOXM1 is not a canonical PARP target.
- **Technical failings that need to be addressed before the case is established** The manuscript does not provide evidence that the identified variants have any functional consequence in TNBC cells or patients. The structural analyses are based on homology models without clear validation of model quality. The relationship between the computational predictions and TNBC pathogenesis is asserted but not tested. The reported MD simulation parameters and results contain inconsistencies that need to be resolved.
- **Assessment against Nature-style criteria** Originality: Low to moderate. The approach is a standard computational pipeline applied to a well-studied gene. Scientific importance: Low to moderate. The findings are hypothesis-generating but do not provide new biological insight into TNBC or FOXM1 function. Interdisciplinary readership: Limited. The paper is likely to appeal mainly to computational biologists and FOXM1 researchers. Technical soundness: Questionable. Several methodological details are unclear or inconsistent, and the lack of validation data weakens the overall technical case. Readability for nonspecialists: Acceptable. The paper is generally readable, though some sections are dense and contain errors.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires substantial revision, clarification of methods and results, and ideally experimental validation before the claims can be considered supported.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim validity
- **Claim pointer** The manuscript claims that the identified nsSNPs, particularly E235Q and S756P, are "malignant" and may affect TNBC progression and prognosis.
- **Evidence pointer** Results sections on MDS analysis and molecular docking; Discussion; Conclusion
- **Concern** The central claim that these variants are "malignant" or clinically relevant to TNBC is based entirely on computational predictions. No experimental data, patient genotype-phenotype correlations, or functional assays are provided to support this claim. The term "malignant" implies a demonstrated pathogenic role, which is not established by in silico tools alone.
- **Why it matters** The conclusion overreaches the evidence. Computational predictions can prioritize candidates for further study, but they cannot establish pathogenicity or clinical relevance. Without validation, the claim that these SNPs are "malignant" is unsupported and potentially misleading.
- **Resolution test** Provide experimental validation, such as cell-based assays demonstrating effects on proliferation, migration, or FOXM1 transcriptional activity, or patient cohort data linking these variants to TNBC outcomes. Alternatively, substantially soften the language to clearly frame the findings as predictions requiring validation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The manuscript reports specific quantitative results from MD simulations, including mean RMSD, RMSF, Rg, and SASA values, and states that E235Q and S756P are the most destabilizing variants.
- **Evidence pointer** Results section on MDS analysis; Table 3; Supplementary Table 2; Figures 3 and 4
- **Concern** The reported values contain apparent inconsistencies. For example, in the Results section, the mean RMSF for E235Q is reported as 1.66501 nm, but in the Discussion, the same value is attributed to Rg. Additionally, the text states that the G variant showed enhanced conformational compactness with a mean Rg value of 1.23707 nm, which is inconsistent with the range of Rg values (3.94575 to 4.45637 nm) reported earlier in the Results. These discrepancies suggest errors in reporting or analysis.
- **Why it matters** The quantitative results are central to the claim that specific variants are destabilizing. If the reported values are incorrect or inconsistent, the conclusions drawn from them are unreliable. The reader cannot determine which values are correct, undermining confidence in the entire analysis.
- **Resolution test** Correct the inconsistencies in reported values. Provide the full data in supplementary tables and ensure that values cited in the text, tables, and figures are consistent. Clarify which metric corresponds to which variant.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The manuscript claims that the four prioritized nsSNPs were identified as "highly damaging" by consensus across five prediction tools, and that this consensus enhances reliability.
- **Evidence pointer** Materials and methods section on detrimental nsSNP prediction; Results section on identification of detrimental nsSNPs; Table 1
- **Concern** The manuscript does not provide the full list of 76 nsSNPs with their individual scores from each tool, nor does it explain the criteria for "consensus" beyond stating that all five tools identified them as damaging. The thresholds for each tool are not clearly defined, and the potential for bias in tool selection is not discussed. Additionally, the text in the Discussion states that "seven different computational webservers" were used, but only five are described in the Methods.
- **Why it matters** The reliability of the prioritization depends on the transparency and rigor of the consensus approach. Without detailed scoring data and clear criteria, the reader cannot assess whether the consensus is meaningful or an artifact of tool selection. The discrepancy between five and seven tools further confuses the methodology.
- **Resolution test** Provide the complete scoring data for all 76 nsSNPs across all tools used. Clarify the number of tools used and the exact consensus criteria. Discuss the limitations and potential biases of the chosen tools.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Relevance to TNBC
- **Claim pointer** The manuscript claims that the identified FOXM1 nsSNPs may affect TNBC progression and prognosis, and that the findings could aid in TNBC therapeutics.
- **Evidence pointer** Introduction; Discussion; Conclusion
- **Concern** The study does not establish any TNBC-specific context for the identified variants. The computational analyses are performed on FOXM1 in isolation, without considering TNBC-specific genetic background, expression patterns, or pathway context. The choice of Olaparib as a control drug is not clearly justified in relation to FOXM1 biology. The claim that these variants are relevant to TNBC, as opposed to FOXM1 function in general, is not supported by any TNBC-specific data.
- **Why it matters** The title and framing of the manuscript promise insights into TNBC, but the study design does not include any TNBC-specific elements. Without such context, the relevance to TNBC is speculative. The findings could apply equally to any FOXM1-expressing cancer, weakening the manuscript's contribution to TNBC research specifically.
- **Resolution test** Include TNBC-specific analyses, such as expression data from TNBC cohorts, correlation with clinical outcomes in TNBC patients, or functional studies in TNBC cell lines. Alternatively, reframe the manuscript to focus on FOXM1 variants in cancer generally, without claiming TNBC specificity.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Structural model quality
- **Claim pointer** The manuscript claims that structural analyses of the FOXM1 variants were performed using homology models and that these models are suitable for drawing conclusions about protein stability and function.
- **Evidence pointer** Materials and methods section on native and mutant FOXM1 structure preparation; Results section on MDS analysis
- **Concern** The manuscript does not report the quality of the homology models, such as sequence identity to the template, coverage, or validation scores (e.g., QMEAN, GMQE). The template structure (PDB ID 3G73) is a DNA-bound forkhead domain, which may not cover the full-length protein. The impact of modeling on the conclusions is not discussed.
- **Why it matters** The reliability of MD simulations and docking analyses depends critically on the quality of the starting structures. Poor-quality models can produce misleading results. Without reporting model quality metrics, the reader cannot assess the validity of the structural conclusions.
- **Resolution test** Report model quality metrics and discuss the limitations of the homology models. If possible, validate key findings using experimentally determined structures or additional modeling approaches.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Internal consistency
- **Affected element** Discussion section
- **Evidence pointer** Discussion, paragraph 3
- **Issue** The Discussion states that "seven different computational webservers" were used, but the Methods section describes only five tools. This discrepancy is confusing and should be resolved.
- **Required correction** Correct the number of tools used, or clarify whether additional tools were used but not described in the Methods.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Table 1
- **Evidence pointer** Table 1
- **Issue** Table 1 lists 76 nsSNPs, but the full table is not provided in the manuscript text. The reader cannot verify the data or assess the scoring details.
- **Required correction** Include the full Table 1 in the main text or as a supplementary file, with all relevant scores from each prediction tool.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity of methods
- **Affected element** Materials and methods, MD simulation section
- **Evidence pointer** Materials and methods, MDS analysis
- **Issue** The description of the MD simulation setup is incomplete. Key parameters such as the force field version, water model details, temperature and pressure coupling specifics, and the length of equilibration are mentioned but not fully specified. The choice of 100 ns and extension to 200 ns is not justified.
- **Required correction** Provide a complete description of the MD simulation parameters, including software version, force field parameters, ensemble conditions, and any validation of simulation convergence.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Language and writing quality
- **Affected element** Throughout the manuscript
- **Evidence pointer** Multiple sections
- **Issue** The manuscript contains several typographical and grammatical errors, such as "thi9s" in the Discussion and "these aberrant alterations these aberrant alterations" in the same section. These errors detract from the readability and professionalism of the manuscript.
- **Required correction** Perform a thorough proofreading of the manuscript to correct typographical and grammatical errors.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Justification of control drug choice
- **Affected element** Materials and methods, molecular docking section
- **Evidence pointer** Materials and methods, molecular docking of FOXM1 variants with Olaparib
- **Issue** The choice of Olaparib as the control drug is explained in the Methods, but the rationale for selecting this drug over other TNCC therapeutics is not fully developed. The connection between FOXM1 and PARP inhibition is not established.
- **Required correction** Provide a more detailed justification for the choice of Olaparib, including any known links between FOXM1 and PARP pathways, or acknowledge that the choice is exploratory.

## Risk / unsupported claims
- The claim that the identified nsSNPs are "malignant" is unsupported by the evidence, which is entirely computational and predictive.
- The claim that the findings could aid in TNBC therapeutics is speculative and not supported by any functional or clinical data.
- The claim that the prioritized nsSNPs are relevant specifically to TNBC, as opposed to cancer in general, is not supported by any TNBC-specific analysis.
- The quantitative results from MD simulations contain inconsistencies that make the reported values unreliable.
- The structural conclusions are based on homology models whose quality is not reported, making the conclusions difficult to assess.
- The claim that consensus across five prediction tools enhances reliability is not fully supported, as the full scoring data and consensus criteria are not provided.