## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, materials and methods) as provided
- **Assessment boundary** Scientific content, technical soundness, and support of claims based solely on the supplied text; no external verification of data or figures beyond what is described
- **Shared manuscript claim summary** The authors map protein-protein interaction networks of the N- and C-termini of all human CHD chromatin remodelers using AP-MS and AlphaFold Multimer, identify a conserved APR in CHD4 that contributes to NuRD and ChAHP complex binding, and demonstrate a role for this APR in erythroid gene expression
- **Visible evidence base** Text descriptions of Figures 1-6, Supplementary Figures 1-2, Supplementary Tables 1-3, and Methods sections; no actual figures, tables, or raw data are viewable in the provided material
- **Missing materials affecting confidence** All figures, supplementary figures, supplementary tables, raw proteomics and RNA-seq data, statistical details, and validation experiments are not directly inspectable; this limits verification of effect sizes, reproducibility, and data quality

## Reviewer
- **Overall assessment** This manuscript addresses a relevant gap in understanding how the poorly characterized terminal regions of CHD chromatin remodelers mediate protein interactions. The integration of AP-MS with AlphaFold Multimer is a reasonable approach, and the identification of a functional APR in CHD4 is potentially interesting. However, the evidence as presented in text form is insufficient to fully evaluate the strength of the claims. Several conclusions appear to extend beyond what the described experiments can support, particularly regarding the directness of APR-mediated interactions and the functional specificity during erythropoiesis. The manuscript would benefit from clearer quantitative reporting and additional validation.
- **Who would be interested in the results, and why** Researchers in chromatin biology, transcriptional regulation, and protein interaction networks would find this resource valuable. The CHD family is central to many developmental and disease processes, and mapping interaction networks of their regulatory termini could inform mechanistic studies. The focus on IDRs and APRs also appeals to the growing community studying phase separation and disordered regions in chromatin factors.
- **Major strengths** The systematic coverage of all CHD family members is a useful resource. The use of complementary approaches (AP-MS and AlphaFold Multimer) is appropriate. The identification of a specific APR in CHD4 with functional consequences in a relevant differentiation model provides a concrete entry point for follow-up studies. The authors acknowledge limitations of AlphaFold for disordered regions.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence strength for direct interaction
  - **Claim pointer** The authors state that "a highly conserved APR within the C-terminus of CHD4 is critical for its interaction with the nucleosome remodeling and deacetylase (NuRD), as well as the CHD, ADNP, and HP1 (ChAHP) complexes" and later that "the CHD4 APR region is important for the physical interaction of CHD4 with GATAD2B"
  - **Evidence pointer** Results sections "Validation of CHD protein interactions with AlphaFold" and "APR contributes to CHD4 interaction with NuRD and ChAHP complexes"; Figure 5
  - **Concern** The claim that the APR is "critical" for interaction is based on deletion and peptide competition experiments, but the text does not report quantitative binding affinities, dose-response relationships, or structural evidence of direct contact. The AlphaFold distance analysis for CHD4-APR with ADNP and GATAD2B suggests distances greater than 7 Å, which the authors acknowledge may not support direct interaction. The deletion mutant could affect protein folding or stability despite the authors' assertion otherwise, and the peptide competition data are described qualitatively without showing complete inhibition or specificity controls beyond a single alanine control. The claim of "critical" appears stronger than the evidence supports.
  - **Why it matters** The central mechanistic conclusion of the paper rests on this interaction being functionally important and mediated by the APR. If the APR is not directly involved in binding, the interpretation of the functional experiments changes substantially.
  - **Resolution test** Provide quantitative binding data (e.g., ITC, MST, or pull-down with purified proteins) showing direct APR-dependent interaction, or demonstrate that APR deletion does not alter protein stability or folding (e.g., circular dichroism, thermal shift, or size-exclusion chromatography). Show dose-dependent inhibition by the APR peptide with appropriate controls and report statistical significance.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Functional specificity of APR in erythropoiesis
  - **Claim pointer** The authors state that "a regulatory role for the CHD4 APR in gene transcription during erythrocyte formation" is demonstrated, and that the APR "coordinates the interaction of key functional proteins such as GATAD2B during erythropoiesis"
  - **Evidence pointer** Results section "The APR region is critical for the function of the NuRD and ChAHP complexes"; Figure 6
  - **Concern** The functional experiments use a single time point (28 h post-induction) and a single concentration of peptide (10 µM). The text reports 248 differentially expressed genes but does not provide effect sizes, false discovery rates, or validation by qPCR or Western blot. The connection between the observed gene expression changes and the specific disruption of CHD4-APR interactions is inferred but not directly demonstrated. The authors do not show that the APR peptide specifically disrupts CHD4-containing complexes in cells, nor do they rule out off-target effects of the peptide. The claim of a "critical interaction hub" for erythropoiesis is not fully supported by the data presented.
  - **Why it matters** The physiological relevance of the APR is a key translational aspect of the paper. Without demonstrating specificity and dose-dependence, the functional claim is not established.
  - **Resolution test** Include dose-response experiments with the APR peptide, show that the peptide enters cells and disrupts CHD4 complex formation (e.g., by co-immunoprecipitation from treated cells), validate key differentially expressed genes by qPCR, and include a rescue experiment or a mutant CHD4 that cannot bind the APR to confirm specificity.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability of interaction network claims
  - **Claim pointer** The authors claim to have "defined the protein-protein interaction (PPI) networks within the N- and C-termini of all CHDs" and to have generated "a comprehensive map of CHD1-9-specific binding proteins"
  - **Evidence pointer** Results sections "The protein interactions of N-termini" and "The protein interactions of C-termini"; Figures 2-3
  - **Concern** The AP-MS experiments were performed with overexpressed fragments in ExP293 cells, which may not reflect endogenous interaction stoichiometry or post-translational modifications. Three fragments (CHD7-N, CHD6-C1, CHD6-C2) were not detected, and CHD8-C1 failed to immunoprecipitate any proteins, meaning the "comprehensive" map is incomplete. The text does not report the number of biological replicates for each fragment beyond stating triplicates, nor does it describe how false positives were filtered beyond using empty vector controls. The lack of validation for most novel interactions (beyond AlphaFold predictions for a subset) limits confidence in the network.
  - **Why it matters** The resource value of the interaction map depends on its reliability and completeness. Overexpression artifacts and missing data for several fragments could mislead the field.
  - **Resolution test** Validate a subset of novel interactions by endogenous co-immunoprecipitation or proximity ligation in a relevant cell type. Report the number of replicates, false discovery rates, and criteria for defining an interaction. Acknowledge the missing fragments as a limitation and consider alternative approaches for those regions.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Statistical reporting
  - **Affected element** Differential gene expression analysis
  - **Evidence pointer** Results section "The APR region is critical for the function of the CHD4 and ChADP complexes"; Figure 6
  - **Issue** The text does not report the number of biological replicates for the RNA-seq experiment, the false discovery rate threshold, or the magnitude of expression changes beyond a log2 fold-change cutoff of 1.5.
  - **Required correction** Provide the number of replicates, FDR values, and a full list of differentially expressed genes with effect sizes in a supplementary table.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Methodological detail
  - **Affected element** AP-MS data analysis
  - **Evidence pointer** Materials and Methods "MS data analysis"
  - **Issue** The text states that proteins with "two missing values" were excluded but does not clarify whether this refers to missing across replicates or across conditions. The criteria for defining an enriched interaction are not fully described.
  - **Required correction** Clarify the missing value handling and describe the statistical test or fold-change threshold used to define enriched proteins.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Figure accessibility
  - **Affected element** All figures
  - **Evidence pointer** Figures 1-6
  - **Issue** The text refers to specific panels and features in figures that are not viewable in the provided material, making it impossible to assess data quality, reproducibility, or the appropriateness of the analyses.
  - **Required correction** Ensure figures are available for review and that all panels are clearly labeled and referenced in the text.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Terminology precision
  - **Affected element** Abstract and Discussion
  - **Evidence pointer** Abstract; Discussion
  - **Issue** The term "critical" is used to describe the APR's role, but the evidence supports a contributory rather than essential function. The phrase "mutually exclusive manner" for CHD4 binding to NuRD versus ChADP is not directly demonstrated.
  - **Required correction** Soften the language to reflect the strength of the evidence, and either provide data showing mutual exclusivity or remove the claim.

## Risk / unsupported claims
- The claim that the CHD4 APR is "critical" for interaction with NuRD and ChADP complexes is not fully supported by the described experiments, as direct binding and specificity are not quantitatively demonstrated.
- The claim of a "comprehensive map" of CHD interaction networks is weakened by the exclusion of several fragments that were not expressed or did not yield interactions.
- The functional role of the APR in erythropoiesis is inferred from a single peptide treatment condition without demonstrating on-target effects in cells.
- The statement that CHD4 binds NuRD and ChADP in a "mutually exclusive manner" is not supported by the data presented.
- The generalizability of the interaction network to endogenous contexts is not established, given the overexpression system used.

## Assessment against Nature-style criteria
- **Originality** The systematic mapping of CHD terminal region interactions is a useful contribution, and the focus on IDRs and APRs in this context is relatively novel. However, the conceptual advance is incremental, as the role of disordered regions in chromatin regulators is an active area.
- **Scientific importance** The CHD family is biologically significant, and a reliable interaction map could be valuable. The specific finding regarding CHD4 APR function in erythropoiesis has potential relevance, but the strength of the evidence is not yet at the level required for a high-impact claim.
- **Interdisciplinary readership** The topic is primarily of interest to chromatin biologists and biochemists. The use of AlphaFold and proteomics may attract computational biologists, but the presentation is not tailored to a broad interdisciplinary audience.
- **Technical soundness** The experimental design is reasonable, but the lack of quantitative validation, incomplete coverage of all fragments, and limited functional specificity testing reduce confidence. The AlphaFold analysis is appropriately cautious in some areas but overinterpreted in others.
- **Readability for nonspecialists** The manuscript is written in a technical style that assumes familiarity with chromatin biology and proteomics. The abstract is accessible, but the results and discussion would be challenging for nonspecialists. The structure is logical, but the text is dense and would benefit from clearer summaries of key findings.

## Recommendation posture
**Currently not established from the provided evidence.** The manuscript presents a potentially useful resource and an interesting hypothesis regarding CHD4 APR function, but the evidence as described does not fully support the central claims of direct APR-mediated interaction and specific functional relevance in erythropoiesis. The authors should be encouraged to resubmit after providing quantitative binding data, additional validation of interaction specificity, and more rigorous functional experiments with appropriate controls. The interaction map, if made fully accessible and validated, could be a valuable contribution, but the current version does not meet the standard for a high-impact journal.