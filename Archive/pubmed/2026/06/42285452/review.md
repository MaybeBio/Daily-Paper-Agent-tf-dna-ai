## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no access to full text, figures, tables, or supplementary materials
- **Shared manuscript claim summary** The authors report that in *Lindera aggregata*, a medicinal plant, sesquiterpenoid biosynthesis is negatively regulated by two WRKY transcription factors, LaWRKY23 and LaWRKY65, which directly bind to the promoter of the terpene synthase gene *LaTPS39*. The study integrates metabolomics, genome-wide TPS identification, in vitro enzyme assays, molecular docking, WGCNA, and promoter-binding assays to support this regulatory model.
- **Visible evidence base** Abstract text only; no figures, tables, methods details, or statistical outputs provided
- **Missing materials affecting confidence** Full methods, all figures and tables, statistical analyses, raw data, supplementary files, and any validation of transgenic or in planta functional data

## Reviewer
- **Overall assessment** The abstract presents a coherent and potentially interesting regulatory model for sesquiterpenoid biosynthesis in a medicinal plant. The multi-omics approach is ambitious and the combination of in vitro biochemistry with promoter-binding assays is appropriate. However, the abstract alone does not provide sufficient evidence to evaluate the robustness of the key claims, particularly the negative regulatory effect of the WRKY factors on *LaTPS39* expression and the functional significance of this regulation in planta. Several claims are stated without quantitative support or clear experimental context.
- **Who would be interested in the results, and why** Researchers in plant specialized metabolism, transcriptional regulation of terpenoid biosynthesis, and medicinal plant genomics would find these results relevant. The work may also interest those studying WRKY transcription factors as regulators of secondary metabolism, and groups working on synthetic biology or metabolic engineering of terpenoids in non-model plants.
- **Major strengths** The study integrates multiple complementary approaches, including metabolomics, genome-wide gene family analysis, in vitro enzyme characterization, and molecular binding assays. The identification of a hub TPS gene via WGCNA and the subsequent validation of direct WRKY binding to its promoter provides a plausible mechanistic link. The use of *L. aggregata*, a species with published genome but limited metabolic regulation studies, addresses a gap in the field.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "LaWRKY23 and LaWRKY65 directly bind to the W-box within the LaTPS39 promoter, potentially negatively regulating its expression and inhibiting sesquiterpenoid synthesis"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract states that Y1H, Dual-Luciferase Reporter Assay, and EMSA confirmed direct binding and "potentially" negative regulation. However, no quantitative data are presented, such as repression fold, binding affinity, or reporter activity changes. The word "potentially" weakens the claim, and it is unclear whether the negative regulation was demonstrated in a functional assay (e.g., transient expression in planta) or only inferred from binding.
  - **Why it matters** Direct promoter binding does not necessarily equate to transcriptional repression. Without functional evidence showing that LaWRKY23 and LaWRKY65 reduce *LaTPS39* expression or sesquiterpenoid levels, the central regulatory model remains unproven.
  - **Resolution test** Provide quantitative data from the Dual-Luciferase assay showing reduced LUC activity upon co-expression of each WRKY with the *LaTPS39* promoter construct, and ideally show that overexpression or silencing of these WRKYs alters sesquiterpenoid content in planta.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Functional validation
  - **Claim pointer** "LaTPS25, LaTPS35, and LaTPS39 were functionally validated to catalyze farnesyl pyrophosphate into sesquiterpenes, such as beta-selinene and germacrene D, through in vitro assays and molecular docking"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract claims functional validation of three TPS enzymes, but no product yields, enzyme kinetics, or product spectra are reported. Molecular docking is mentioned as part of the validation, which is unusual for confirming catalytic function and does not substitute for biochemical evidence. It is unclear whether all three enzymes produce the same products or differ in specificity.
  - **Why it matters** The identification of *LaTPS39* as a hub gene and the focus on its regulation depend on the reliability of its functional assignment. If the in vitro data are incomplete or the docking results are overinterpreted, the foundation of the regulatory model is weakened.
  - **Resolution test** Present chromatographic evidence of product formation for each enzyme, with authentic standards where possible, and clarify the role of docking (e.g., substrate binding prediction) rather than as a validation of catalysis.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Statistical and quantitative support
  - **Claim pointer** "HS-SPME-GC-MS identified 69 sesquiterpenoids, and the roots showed the highest accumulation"
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract reports identification of 69 sesquiterpenoids and tissue-specific accumulation, but no statistical comparisons, replicate numbers, or quantitative measures (e.g., relative abundance, fold differences) are provided. It is unclear how "highest accumulation" was determined and whether this difference is significant.
  - **Why it matters** The tissue-specific accumulation pattern is used to justify the focus on roots and the relevance of the regulatory mechanism. Without statistical support, this claim is anecdotal.
  - **Resolution test** Provide statistical analysis of sesquiterpenoid levels across tissues, including replicate numbers and significance thresholds.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Title
  - **Evidence pointer** Title
  - **Issue** The title states that LaWRKY23 and LaWRKY65 "negatively regulate" LaTPS39, but the abstract only says "potentially negatively regulating." This discrepancy overstates the evidence.
  - **Required correction** Align the title with the strength of the evidence, or provide functional data that supports the definitive wording.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** WRKY identification
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract mentions "three WRKY transcription factors" identified by WGCNA but only names two (LaWRKY23 and LaWRKY65). The third is not described, and its role is unclear.
  - **Required correction** Either name the third WRKY and state its relationship to the other two, or explain why it was excluded from further analysis.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Terminology
  - **Affected element** "Headspace Solid Phase Micro-extraction Gas Chromatography-Mass Spectrometry"
  - **Evidence pointer** Abstract
  - **Issue** The abbreviation "HS-SPME-GC-MS" is used, but the technique is a sampling method coupled to GC-MS, not a standalone analytical method. The phrasing could be clarified.
  - **Required correction** Rephrase as "Headspace Solid Phase Micro-extraction coupled to Gas Chromatography-Mass Spectrometry (HS-SPME-GC-MS)".
- **Technical failings that need to be addressed before the case is established** R1-M1 and R1-M2 are blocking. The negative regulatory model requires functional evidence beyond binding assays, and the TPS functional validation needs quantitative biochemical data. R1-M3, while not blocking, requires statistical support for the tissue-specific claim.
- **Assessment against Nature-style criteria**  
  *Originality*: The study addresses a less-characterized species and a specific regulatory node, which is of interest, but the general concept of WRKY-mediated regulation of terpenoid biosynthesis is not novel.  
  *Scientific importance*: Moderate. The findings could inform metabolic engineering of sesquiterpenoid production, but the significance depends on the robustness of the regulatory model, which is not yet established from the abstract.  
  *Interdisciplinary readership*: Limited. The work is primarily relevant to plant biologists and natural product researchers; broader appeal is not evident.  
  *Technical soundness*: Cannot be fully assessed from the abstract. The combination of methods is appropriate, but the lack of quantitative data and functional validation prevents a positive assessment.  
  *Readability for nonspecialists*: The abstract is reasonably clear, though some terms (e.g., WGCNA, Y1H) are used without explanation, which may hinder nonspecialist readers.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a plausible model, but the key claims of negative regulation and functional TPS validation require additional data. I would be supportive if the authors provide quantitative functional evidence and clarify the statistical basis of their metabolomic and expression data.

## Risk / unsupported claims
- The claim that LaWRKY23 and LaWRKY65 "negatively regulate" *LaTPS39* is unsupported by the abstract, which only states "potentially" negative regulation and provides no functional repression data.
- The functional validation of LaTPS25, LaTPS35, and LaTPS39 is not supported by quantitative biochemical evidence in the abstract; molecular docking is not a substitute for enzymatic assays.
- The statement that roots show the "highest accumulation" of sesquiterpenoids is unsupported without statistical comparison.
- The existence and role of a third WRKY transcription factor identified by WGCNA is mentioned but not described, making this claim unassessable.