## Review setup
- **Input scope** Full manuscript text including abstract, results, discussion, and materials and methods
- **Assessment boundary** Scientific content, experimental design, data interpretation, and claims as presented in the provided text. No access to figures, supplemental data, or raw sequencing data.
- **Shared manuscript claim summary** The authors report that MEF2C controls segment-specific gene regulatory networks (GRNs) during embryonic heart tube development. Using snRNA-seq and snATAC-seq from wild-type and Mef2c knockout mouse embryos at E7.75, E8.5, and E9, they identify distinct transcriptional programs across heart tube segments, show that MEF2C loss causes posteriorization of the heart tube, identify candidate enhancers with MEF2C-dependent accessibility that show activity in zebrafish, and demonstrate that reducing NR2F2 dosage partially rescues the Mef2c knockout phenotype.
- **Visible evidence base** Abstract, Results sections (5 subsections), Discussion, Materials and methods (partial), Competing interest statement, Acknowledgments. Figure and table references are present in text but figures themselves are not provided.
- **Missing materials affecting confidence** All figures and supplemental figures, supplemental data files (S1-S9), raw sequencing data, detailed bioinformatics parameters, and the full supplemental methods. The manuscript states data are deposited at GEO (GSE280587) and code at GitHub, but these were not accessible for this review.

## Reviewer
- **Overall assessment** This manuscript presents a comprehensive multi-omic analysis of MEF2C function in early heart tube development, with a strong conceptual framework proposing segment-specific gene regulatory networks. The integration of snRNA-seq and snATAC-seq across three developmental time points in wild-type and knockout embryos is ambitious and appropriate for the questions asked. The identification of novel enhancers with in vivo activity in zebrafish and the genetic interaction between Mef2c and Nr2f2 are potentially significant contributions. However, several concerns limit the strength of the conclusions as currently presented. The sample size of n=2 embryos per genotype per stage is small for the scale of claims made. The validation of candidate enhancers in zebrafish, while useful, is a cross-species approach with inherent limitations for drawing conclusions about mouse heart tube development. The GRN inference with CellOracle and the interpretation of network reorganization would benefit from clearer validation metrics. The partial rescue experiment, while conceptually important, is presented with limited quantitative detail. The manuscript would be strengthened by additional validation of key regulatory relationships and more transparent presentation of the robustness of the computational findings.

- **Who would be interested in the results, and why** Developmental biologists studying heart development and congenital heart defects will find the segment-specific GRN framework directly relevant. Researchers interested in transcription factor pleiotropy and how a single TF can regulate distinct programs in different cellular contexts will be interested in the MEF2C mechanism described. The multi-omic integration approach and the use of GRN inference tools will be of interest to computational biologists working on gene regulatory networks. Clinically oriented researchers studying congenital heart disease may find the MEF2C-NR2F2 genetic interaction and the identification of novel enhancers relevant to understanding the etiology of cardiac malformations.

- **Major strengths** 1) The multi-omic approach combining snRNA-seq and snATAC-seq across three time points in both genotypes is technically ambitious and provides a rich dataset. 2) The conceptual framework of segment-specific GRNs is a valuable contribution to understanding how a single TF can have distinct roles in different regions of an organ primordium. 3) The integration of computational predictions with in vivo validation in zebrafish provides functional evidence for the identified enhancers. 4) The genetic rescue experiment with Nr2f2 haploinsufficiency provides a direct test of the proposed model and is a strong experimental design. 5) The manuscript is generally well-written and the logic is clearly presented.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that MEF2C regulates distinct transcriptional programs and lineage trajectories during embryonic cardiac tract development, with segment-specific effects on gene expression and chromatin accessibility.
- **Evidence pointer** Results section "Loss of MEF2C reduces the expression of key cardiomyocyte genes across all heart tube segments and alters the expression of anterior/posterior markers"; Figure 2; Supplemental Figures S1, S2
- **Concern** The snRNA-seq and snATAC-seq experiments were performed with n=2 embryos per genotype per stage. This is a very small sample size for drawing conclusions about differential expression and differential accessibility, particularly for the subtle segment-specific differences that are central to the manuscript's thesis. The authors do not report whether the two replicates were concordant, how variability between replicates was handled, or whether any pseudoreplication concerns exist. For a study making claims about distinct regulatory networks in three heart tube segments, the statistical power from n=2 is a substantial limitation.
- **Why it matters** The core claims of segment-specific gene regulation and differential chromatin accessibility depend on the reliability of the differential analysis. With n=2, the false discovery rate could be substantially inflated, and the authors may be overinterpreting noise as biological signal. This affects the foundation of the entire manuscript.
- **Resolution test** The authors should provide evidence of replicate concordance, report the number of cells per cluster per sample, and ideally validate key differential expression and accessibility findings with an orthogonal method (e.g., RT-qPCR, immunohistochemistry, or ATAC-qPCR) for at least a subset of the segment-specific genes and regulatory elements.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that candidate enhancer regions with MEF2C-dependent chromatin accessibility display enhancer activity in zebrafish, and that this validates them as bona fide regulatory elements relevant to mouse heart tube development.
- **Evidence pointer** Results section "Candidate regulatory elements with MEF2C-dependent chromatin accessibility display enhancer activity in zebrafish"; Figure 5; Supplemental Figures S5
- **Concern** The validation of candidate enhancers is performed in zebrafish, a cross-species system. While the authors justify this by noting conservation of cardiac transcription factors, the regulatory logic of enhancers can differ substantially between species. The manuscript does not report whether the orthologous zebrafish sequences were tested, or whether the mouse sequences were tested in a mouse context. Additionally, the authors report that 7 of 11 candidates showed activity, but the criteria for scoring "activity" are not described in the provided text. The variability in timing of enhancer activity (24 vs 72 hpf) is noted but not systematically analyzed.
- **Why it matters** The claim that these are "bona fide enhancers" relevant to mouse heart tube development is stronger than what a cross-species zebrafish assay can support. Enhancer activity in zebrafish does not guarantee relevance in the mouse embryonic heart, particularly for elements that may have evolved species-specific functions. The lack of clear scoring criteria also makes the 7/11 success rate difficult to interpret.
- **Resolution test** The authors should either validate a subset of enhancers in a mouse context (e.g., mouse transgenic reporter assays or in ovo electroporation) or temper the claims to state that these are candidate enhancers with cross-species activity. Clear criteria for scoring enhancer activity in zebrafish should be provided.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors claim that loss of MEF2C causes a network-wide reorganization of gene regulation, with NR2F2 and GATA4 acquiring new targets and altered activity in the Mef2c knockout.
- **Evidence pointer** Results section "Loss of MEF2C induces an overactive posteriorized gene regulatory network driven by NR2F2 and GATA4"; Figure 6; Supplemental Figures S6
- **Concern** The GRN inference using CellOracle is a computational prediction, and the manuscript does not provide sufficient detail on how the networks were validated. The claim of "network-wide reorganization" is based on inferred interactions, not directly measured protein-DNA interactions or functional assays. The validation of the in silico Mef2c knockout simulation achieving 74% accuracy is presented, but the metric and its interpretation need more context. The authors also do not discuss the limitations of GRN inference methods, which can produce false positive and false negative interactions.
- **Why it matters** The GRN analysis is central to the manuscript's conceptual contribution. If the inferred networks are not reliable, the claims about network reorganization and the specific roles of NR2F2 and GATA4 are weakened. The field needs to know how robust these predictions are and what experimental evidence supports them beyond computational inference.
- **Resolution test** The authors should provide additional validation of key GRN predictions, such as confirming direct binding of NR2F2 and GATA4 to the predicted target loci (e.g., ChIP-qPCR or electrophoretic mobility shift assays) and demonstrating functional relevance through perturbation experiments (e.g., knockdown or overexpression in relevant model systems).

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that reducing NR2F2 dosage partially rescues the heart tube phenotype in Mef2c knockout embryos.
- **Evidence pointer** Results section "Reduction of NR2F2 dosage partially rescues the heart tube phenotype in Mef2c KO embryos"; Figure 6J,K; Supplemental Figure S7
- **Concern** The phenotypic analysis is described as initially unblinded, then blinded for re-examination. The manuscript states that phenotypes "ranged in apparent severity and fell into roughly three categories," but the criteria for these categories are not defined in the provided text. The number of embryos analyzed per genotype is not stated. The claim of "partial rescue" is based on qualitative categorization, and the variability of the rescue is acknowledged but not quantified.
- **Why it matters** The genetic rescue experiment is a key functional validation of the proposed model. If the phenotypic assessment is not rigorously quantitative and the sample sizes are small, the strength of the rescue claim is limited. The field needs to know how robust and reproducible this effect is.
- **Resolution test** The authors should provide quantitative morphometric measurements (e.g., ventricular area, loop angle, cell counts) with statistical comparisons, report the number of embryos per genotype, and provide clear, pre-defined criteria for phenotypic categorization.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that MEF2C cobinds certain regulatory elements with NR or GATA factors in the wild-type condition, and that these NR and GATA factors become free to bind different regulatory elements with loss of MEF2C.
- **Evidence pointer** Results section "Loss of MEF2C induces an overactive posteriorized gene regulatory network driven by NR2F2 and GATA4"; Figure 6A,B; Supplemental Figure S6A
- **Concern** The claim of cobinding is based on motif analysis of accessible chromatin regions, not on direct measurement of co-occupancy. The authors infer cobinding from the presence of MEF2 and NR or GATA motifs in the same accessible regions. This is an indirect inference. The statement that NR and GATA factors "become free to bind different regulatory elements" is a hypothesis that is not directly tested.
- **Why it matters** The proposed mechanism of MEF2C acting as a "gatekeeper" that prevents NR and GATA factors from binding inappropriate targets is an interesting model, but the evidence presented is circumstantial. Direct evidence of cobinding and redistribution would substantially strengthen the model.
- **Resolution test** The authors should perform ChIP-seq for NR2F2 and GATA4 in both wild-type and Mef2c knockout hearts to directly test whether their genomic occupancy changes upon MEF2C loss. Alternatively, they could use a more direct biochemical approach to demonstrate cobinding at specific loci.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is very dense and uses field-specific terminology (e.g., "segment-specific gene regulatory networks," "lineage trajectories") without sufficient context for readers outside the immediate field of heart development.
- **Required correction** Consider adding one sentence of broader context about why segment-specific regulation in the heart tube matters for understanding congenital heart defects, and briefly define what is meant by "segment-specific" in this context.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, zebrafish enhancer assay
- **Evidence pointer** Materials and methods, "Cloning of reporter constructions for zebrafish transgenesis"
- **Issue** The filtering criteria for selecting candidate enhancers are described, but the rationale for the specific thresholds (e.g., log2FC values, motif requirements) is not explained. The authors state they selected "12 of the highest priority" but the prioritization scheme is not fully described.
- **Required correction** Provide a more detailed description of the prioritization criteria and rationale, or reference a supplementary table that fully documents the filtering steps and scores for all candidates.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results, differential expression analysis
- **Evidence pointer** Results section "Loss of MEF2C reduces the expression of key cardiomyocyte genes"; Supplemental Data S3
- **Issue** The manuscript does not report the thresholds used for defining differentially expressed genes (e.g., adjusted p-value, log2 fold-change cutoff) in the main text. This information is presumably in the supplemental methods, but it should be stated in the results for clarity.
- **Required correction** State the thresholds for differential expression and differential accessibility in the main text or in a methods summary within the results section.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of GRN inference and network reorganization is quite technical and may be difficult to follow for readers who are not familiar with computational approaches. The broader implications for understanding congenital heart defects could be more explicitly stated.
- **Required correction** Consider adding a paragraph that translates the GRN findings into more accessible biological terms and explicitly states the potential implications for understanding and potentially treating congenital heart defects.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods, mouse models
- **Evidence pointer** Materials and methods, "Mouse models"
- **Issue** The manuscript states that the Mef2c+/− allele is the same as that generated by Lin et al. (1997), but does not describe the nature of the allele (e.g., targeted deletion, gene trap) or its expected effect on MEF2C protein production.
- **Required correction** Briefly describe the nature of the Mef2c mutant allele and confirm that homozygous mutants are embryonic lethal as expected, with the phenotype characterized at the stages examined.

## Risk / unsupported claims
- The claim that MEF2C "controls" segment-specific GRNs implies a direct regulatory role that is supported by correlation (differential expression and accessibility) but not by direct perturbation of MEF2C binding or activity at specific loci.
- The claim that NR and GATA factors "become free to bind different regulatory elements" upon MEF2C loss is a hypothesis inferred from motif analysis, not directly tested.
- The claim that the identified enhancers are "bona fide" is based on zebrafish reporter assays, which demonstrate activity in a heterologous context but do not establish endogenous function in the mouse heart tube.
- The claim of "network-wide reorganization" is based on computational inference (CellOracle) without direct experimental validation of the predicted regulatory interactions.
- The statement that "more than half (three out of five) of the Mef2c−/−;Nr2f2+/− embryos exhibited increased expression of Ttn" is based on a very small sample size and qualitative assessment, limiting the strength of this conclusion.
- The claim that the approach "provides a generalizable framework" is forward-looking and not directly supported by the data presented, though it is a reasonable aspiration.