## Review setup
- **Input scope** Full manuscript text, including abstract, results, discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific claims, experimental design, data interpretation, and technical soundness as presented in the preprint; no assessment of editorial fit or publication venue
- **Shared manuscript claim summary** The authors investigate the functional necessity of enhancer elements at the Gata4 and Hand2 loci in mouse heart development. They report that individual enhancer deletions are phenotypically silent, but some become essential under sensitized genetic backgrounds. They generate a single-nucleus multiome atlas of the developing heart, use it to predict novel Hand2 enhancers, validate several by transgenic reporter assays, and identify a large upstream regulatory interval (H2-URI) whose deletion causes embryonic lethality with endocardial and trabeculation defects.
- **Visible evidence base** Abstract, full results text, discussion, methods, figure legends referenced in text (Figures 1–6, S1–S13), tables referenced (S1–S16), data availability statement
- **Missing materials affecting confidence** Actual figure images and supplementary tables are not provided; quantitative data underlying figures (e.g., RNA-seq counts, C-HiC contact matrices, reporter assay scoring) are not directly inspectable; exact coordinates of enhancer deletions and H2-URI boundaries are not stated in the text; statistical details for several comparisons are not fully described

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive and technically ambitious analysis of enhancer architecture at two key cardiac transcription factor loci. The combination of systematic enhancer deletion, sensitized genetic backgrounds, single-nucleus multiome profiling, and chromatin polymer modeling is impressive and addresses an important question in developmental gene regulation. The finding that individual enhancers are largely dispensable but become essential under genetic stress is consistent with emerging paradigms of enhancer redundancy and shadow enhancer function. However, several technical concerns and gaps in the presented evidence limit the strength of the conclusions as currently stated. The claim that the H2-URI is a "gatekeeper domain" controlling endocardial development is not fully supported by the data presented, and the mechanistic link between specific enhancers within the interval and the observed phenotypes requires further substantiation.
- **Who would be interested in the results, and why** Developmental biologists studying gene regulatory networks and enhancer function, particularly those focused on heart development and congenital heart disease. Researchers interested in enhancer redundancy, shadow enhancers, and the evolutionary conservation of cis-regulatory elements will also find this work relevant. The multiome dataset and the computational framework for enhancer prediction will be of interest to the genomics and bioinformatics communities.
- **Major strengths** The systematic genetic dissection of enhancer elements at two disease-relevant loci is a significant undertaking. The use of sensitized genetic backgrounds to reveal conditional enhancer essentiality is a thoughtful and powerful approach. The generation of a single-nucleus multiome atlas spanning multiple developmental stages provides a valuable community resource. The integration of multiple methodologies, including deep learning, polymer modeling, and in vivo reporter assays, is commendable. The cross-species validation in zebrafish adds an evolutionary dimension to the work.
- **Major Concerns**
  - **R1-M1** (Blocking: Yes)
  - **R1-M2** (Blocking: Yes)
  - **R1-M3** (Blocking: No)
  - **R1-M4** (Blocking: No)
  - **R1-M5** (Blocking: No)
- **Minor Comments**
  - **R1-m1**
  - **R1-m2**
  - **R1-m3**
  - **R1-m4**
  - **R1-m5**
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2
- **Assessment against Nature-style criteria** Originality: High. The study addresses a fundamental question in developmental biology with a comprehensive and multi-faceted approach. The concept of conditional enhancer essentiality under genetic stress is not entirely new but is applied here in a particularly rigorous and systematic manner. Scientific importance: High. The findings have implications for understanding the genetic basis of congenital heart disease and the general principles of enhancer function and redundancy. The multiome dataset will be a valuable resource. Interdisciplinary readership: Moderate. The work will primarily appeal to developmental biologists, geneticists, and genomics researchers. The clinical relevance to CHD may broaden its appeal. Technical soundness: Moderate. The experimental design is generally sound, but several technical concerns (see R1-M1, R1-M2) need to be addressed to fully support the conclusions. Readability for nonspecialists: Moderate. The manuscript is dense and assumes significant background knowledge in genomics and developmental biology. The abstract is accessible, but the results section is challenging for a general audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core findings are potentially important, and the resource generated is valuable. However, the current presentation has gaps in evidence and potential over-interpretation that must be addressed before the case is fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that deletion of the H2-URI causes embryonic lethality and that this is due to loss of endocardial enhancer activity, specifically implicating hE2, hE4, and hE5 in regulating endocardial gene expression and downstream effects on trabeculation and cushion formation.
- **Evidence pointer** Results section "The Hand2-upstream regulatory interval controls endocardial development and embryonic survival"; Figures 6B–I; S11–S13
- **Concern** The causal link between the H2-URI deletion, loss of Hand2 in the endocardium, and the observed phenotypes is not fully established. The authors show that H2-URIΔ/Δ embryos have reduced Hand2 expression and endocardial defects, but they do not demonstrate that these defects are specifically due to loss of Hand2 in the endocardium. The H2-URI deletion removes multiple enhancers, some of which (e.g., hE1) also drive expression in the myocardium. The observed reduction in myocardial Hand2 could contribute to the phenotype. Rescue experiments, such as endocardial-specific expression of Hand2 in the H2-URIΔ/Δ background, would be needed to establish this causal link. Furthermore, the claim that the H2-URI is a "gatekeeper domain" implies a specific structural or functional role beyond simply harboring enhancers, which is not directly tested.
- **Why it matters** The central conclusion of the paper rests on the specific function of the H2-URI in endocardial development. Without a direct demonstration that the phenotypes are due to loss of endocardial Hand2, the interpretation remains correlative. This distinction is critical for understanding the mechanism of action and for potential clinical relevance.
- **Resolution test** Provide rescue experiments with endocardial-specific Hand2 expression in the H2-URIΔ/Δ background. Alternatively, generate a more targeted deletion of only the endocardial enhancers (hE2, hE4, hE5) to see if it phenocopies the H2-URI deletion. If rescue is achieved or the targeted deletion phenocopies the full deletion, the claim would be substantially strengthened.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors use ChromBPNet to predict transcription factor motifs within the identified enhancers and claim that these predictions reveal the regulatory logic, including the involvement of GATA and ETS factors.
- **Evidence pointer** Results section "Decoding the Hand2 cardiac enhancer landscape at cell type resolution"; Figure 4C; Methods section "ChromBPNet deep learning variant and motif predictions"
- **Concern** The ChromBPNet analysis is used to infer functional motifs and transcription factor dependencies. However, the manuscript does not provide sufficient details on the validation of these predictions. The authors state that the models were trained on their multiome data, but no metrics of model performance (e.g., AUROC, calibration) are provided. More importantly, the predictions are not experimentally validated. For example, the claim that GATA motifs are critical for hE1 activity could be tested by mutating the predicted motifs in the reporter assays. Without such validation, the ChromBPNet predictions remain computational hypotheses, and the statement that they "reveal" the regulatory logic is an overstatement.
- **Why it matters** The paper proposes a framework for enhancer prediction and regulatory logic inference. The credibility of this framework depends on the accuracy of the underlying models and the validation of their predictions. If the predictions are not robust, the utility of the framework and the specific conclusions about Hand2 regulation are weakened.
- **Resolution test** Provide performance metrics for the ChromBPNet models. Experimentally test the predicted functional motifs by introducing mutations into the enhancer-reporter constructs and assessing the impact on reporter activity in vivo or in vitro. This would directly validate the computational predictions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** The authors state that the multiome dataset enables the delineation of cardiac cistromes and the systematic prediction of enhancer activity across cell types, and they use this to identify the H2-URI enhancers.
- **Evidence pointer** Results section "Multiome profiling uncovers regulatory landscapes and TF cistromes across cardiac cell types"; Figures 3, 4; S5–S7
- **Concern** The multiome dataset is a key resource of this paper. However, the manuscript does not provide a thorough validation of the cell type annotations. The clustering is based on gene expression and chromatin accessibility, but the authors do not show orthogonal validation of the identity of each cluster (e.g., by immunostaining for known markers or by comparison to published datasets). The "early" and "late" designations for clusters are based on the developmental stage of the samples, but it is not clear if these represent distinct progenitor states or simply a continuum. A more rigorous validation of the cell types would increase confidence in the downstream analyses.
- **Why it matters** The accuracy of the enhancer predictions and the interpretation of cell type-specific regulatory logic depend on the correct identification of cell types. If the clusters are not accurately annotated, the conclusions about which enhancers are active in which cell types could be misleading.
- **Resolution test** Provide additional validation of cell type identities, such as co-staining for known markers or comparison with published single-cell datasets from the developing heart. Show that the "early" and "late" clusters are distinct states, for example by pseudotime analysis or by demonstrating differential expression of known progenitor markers.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** The authors conclude that the H2-URI functions as an "insulated, modular regulatory hub" based on polymer modeling and the presence of CTCF sites.
- **Evidence pointer** Results section "Polymer modelling defines cardiac-specific regulatory architecture"; Figures 5, 6; S10, S11
- **Concern** The polymer modeling is used to infer the 3D structure of the Hand2 locus and to predict the effects of the H2-URI deletion. While the modeling is sophisticated, the conclusions about the "insulated" nature of the domain and the specific role of CTCF are not directly tested. The authors do not perform experiments to disrupt CTCF binding or to alter the 3D structure (e.g., by deleting the CTCF site) to see if this affects Hand2 expression or the phenotypes. The modeling is correlative and does not establish causality.
- **Why it matters** The claim of an "insulated hub" is a strong structural and functional statement. Without direct experimental manipulation of the proposed structural elements, this conclusion remains speculative and is not fully supported by the data.
- **Resolution test** Perform experiments to disrupt the predicted CTCF site or to alter the 3D structure, such as by using CRISPR to delete the CTCF binding site and assessing the impact on Hand2 expression, enhancer-promoter interactions, and the resulting phenotype. This would directly test the role of the proposed structural elements.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Evidence sufficiency
- **Claim pointer** The authors suggest that the identified enhancers and the H2-URI may be relevant for interpreting congenital heart disease (CHD)-associated variants.
- **Evidence pointer** Results section "Multiome profiling uncovers regulatory landscapes and TF cistromes across cardiac cell types"; Figure S6D, E; Discussion
- **Concern** The analysis of CHD-associated variants is limited. The authors state that they did not find a significant enrichment of de novo CHD variants in their putative enhancer elements. This negative result is presented without much discussion of its implications. The lack of enrichment could be due to the limited power of the variant datasets, the specific cell types and developmental stages profiled, or the possibility that CHD variants are not concentrated in these particular enhancers. The manuscript would benefit from a more nuanced discussion of this negative result and its implications for the utility of the resource.
- **Why it matters** The potential clinical relevance of the resource is a stated motivation for the work. A more thorough analysis and discussion of the variant data would strengthen the paper's impact and provide a more balanced view of the limitations and potential applications.
- **Resolution test** Provide a more detailed analysis of the variant data, including power calculations, analysis of common variants, and a discussion of the potential reasons for the lack of enrichment. Consider analyzing variants in other regulatory elements or using different statistical approaches.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and uses technical terms (e.g., "multiome profiling," "cistromes," "polymer modeling") without sufficient context for a general reader. The key finding of conditional enhancer essentiality is stated but could be more clearly highlighted.
- **Required correction** Consider revising the abstract to briefly explain the significance of the multiome approach and to more explicitly state the main conclusion: that individual enhancers are largely redundant but become essential under genetic stress, and that a specific upstream interval is critical for endocardial development.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section "Resilience of cardiac TF regulatory landscapes to individual heart enhancer loss"
- **Evidence pointer** Figure 1C–E; S2C
- **Issue** The authors state that homozygous enhancer deletion mice are viable and fertile, but the text does not specify the number of animals examined or the statistical power of this analysis. For a claim of "no phenotype," it is important to know the sample size and the sensitivity of the assays used.
- **Required correction** Provide details on the number of animals analyzed for each genotype and the specific assays used to assess viability and fertility. A statement about the statistical power to detect a phenotype would be helpful.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section "Decoding the Hand2 cardiac enhancer landscape at cell type resolution"
- **Evidence pointer** Figure 4B; S8
- **Issue** The description of the enhancer reporter assay results is brief. The authors state that the enhancers drive "overlapping" or "specific" activity, but the figures are not available for review. A more detailed description of the observed patterns, including any variability between embryos, would be helpful.
- **Required correction** Provide a more detailed description of the reporter assay results, including the number of embryos analyzed per construct and the consistency of the observed patterns.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section "Bulk RNA-seq"
- **Evidence pointer** Methods
- **Issue** The methods for bulk RNA-seq analysis are described, but the criteria for selecting the three biological replicates per genotype are not stated. The authors mention "stage-matched" hearts, but the exact developmental stage matching criteria are not defined.
- **Required correction** Clarify the criteria for selecting replicates and the developmental stage matching process.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion is comprehensive but could be more focused. The connection between the findings on enhancer redundancy and the broader implications for understanding gene regulation and disease could be made more explicitly.
- **Required correction** Consider tightening the discussion to more directly link the findings to the central question of how enhancer architecture contributes to phenotypic robustness and disease susceptibility.

## Risk / unsupported claims
- The claim that the H2-URI is a "gatekeeper domain" is not directly supported by the data, as the specific structural or functional role of the domain beyond harboring enhancers is not tested.
- The claim that ChromBPNN predictions "reveal" the regulatory logic of the enhancers is an overstatement, as the predictions are not experimentally validated.
- The conclusion that the H2-URI deletion phenotype is specifically due to loss of endocardial Hand2 is not fully supported, as the deletion also affects myocardial enhancers.
- The statement that the multiome resource will "enhance the functional interpretation of CHD-associated variants" is not directly supported by the analysis, which found no significant enrichment of CHD variants in the identified enhancers.
- The assertion that the H2-URI deletion does not cause morphological abnormalities at E9.5 is based on whole-mount analysis, which may not be sensitive enough to detect subtle defects.