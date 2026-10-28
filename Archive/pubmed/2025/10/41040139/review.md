## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, extended data descriptions)
- **Assessment boundary** Scientific content, technical soundness, claims versus evidence, and alignment with Nature-style criteria. No line-by-line editorial review.
- **Shared manuscript claim summary** The authors present a high-resolution atlas of RNA Polymerase II-engaged transcriptional regulatory elements (TREs) across human tissues, developmental lineages, and disease states, generated using an optimized PRO-cap protocol. They demonstrate that transcription initiation at TREs is a sensitive and functionally informative marker of regulatory activity, complementing epigenomic annotations. They further integrate this atlas with deep learning models (ProCapNet), statistical fine-mapping, and functional assays to prioritize noncoding variants and dissect regulatory architecture, including tissue-specific evolutionary constraints and metastatic cancer signatures.
- **Visible evidence base** Full text including results, methods, figure legends (referenced but not shown), supplementary table descriptions, and data/code availability statements.
- **Missing materials affecting confidence** Figures, extended data figures, and supplementary tables are referenced but not provided. This limits independent verification of quantitative results, statistical analyses, and methodological details.

## Reviewer
- **Overall assessment** This manuscript presents a substantial and potentially valuable resource: a nascent transcriptome atlas of regulatory elements across diverse human tissues and disease states. The optimized PRO-cap protocol and the scale of data generation are commendable. The conceptual framing, that transcription initiation is a defining and functionally informative layer of regulatory activity, is well supported by the presented analyses. The integration with deep learning and fine-mapping provides a useful framework for variant prioritization. However, the manuscript's impact is currently constrained by the absence of key figures and supplementary data, which prevents full assessment of technical rigor and the strength of several central claims. The clinical and biological insights, while promising, are largely descriptive at this stage.
- **Who would be interested in the results, and why** Researchers in gene regulation, genomics, and epigenomics will find this atlas a valuable resource for studying enhancer and promoter activity. Clinicians and translational scientists interested in the regulatory basis of complex diseases, particularly autoimmune disorders and cancer metastasis, will be interested in the tissue- and cell-type-specific variant prioritization framework. Computational biologists developing and applying deep learning models to regulatory genomics will also find the ProCapNet integration and interpretation analyses relevant.
- **Major strengths**
  1.  The generation of a large, tissue-resolved nascent transcriptome atlas using an optimized PRO-cap protocol is a significant technical achievement and a valuable community resource.
  2.  The systematic benchmarking against existing epigenomic and transcriptomic annotations (e.g., ENCODE cCREs, FANTOM CAGE-seq) provides a clear and quantitative demonstration of the unique value of transcription-based TRE identification.
  3.  The integration of the atlas with ProCapNet and statistical fine-mapping to prioritize and interpret noncoding variants in a tissue-specific manner is a powerful and timely analytical framework.
  4.  The functional validation through CRISPRi screens and luciferase assays, particularly for the MYC locus and the IL2RB variant, strengthens the biological relevance of the identified regulatory elements.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that the optimized PRO-cap protocol is "highly concordant" with the original protocol and produces high-quality data across diverse biospecimens.
  - **Evidence pointer** Results section "A transcription-based atlas...", Figure 1a, Supplementary Figure 1a-e
  - **Concern** The manuscript states that libraries have "sufficient sequencing depth" and "high reproducibility," but the actual data (Supplementary Figure 1) is not provided. The median correlation of 0.902 for replicates, while acceptable, needs to be assessed in the context of the specific analyses. More critically, the claim of concordance with the original protocol is not quantitatively demonstrated in the text. The quality control metrics (gene body ratio, RNA length) are described, but their distributions and thresholds for inclusion/exclusion are not fully specified.
  - **Why it matters** The entire atlas is built on this protocol. Without seeing the quality control data, it is impossible to verify that the identified TREs are not artifacts of the modified protocol or library preparation. This is a foundational claim that underpins all subsequent analyses.
  - **Resolution test** Provide the actual data in Supplementary Figure 1. Show a direct comparison of TREs identified by the optimized protocol versus the original protocol on the same cell type. Clearly state the thresholds for quality control metrics and how many samples were excluded based on these criteria.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence strength
  - **Claim pointer** The claim that "TRE landscapes capture regulatory signatures reflecting both tissue of origin and adaptive responses to distant niches" in metastatic cancer.
  - **Evidence pointer** Results section "Tissue-specific TRE profiles inform primary site prediction in metastatic cancers", Figure 6a-b
  - **Concern** The prediction of primary site with 87% top-1 accuracy is impressive. However, the analysis is based on a small number of metastatic samples (n=23) and a limited number of tissue types (n=15). The claim of "adaptive responses to distant niches" is a strong interpretation. The data shows that metastatic samples cluster closer to their tissue of origin, but this does not directly demonstrate adaptation. The differential analysis between lung and brain metastases (Figure 6c-f) is more direct, but the sample size for each metastatic site is not stated.
  - **Why it matters** This is a key translational claim of the paper. Over-interpreting correlation with primary tissue as evidence for adaptation could mislead the field. The clinical utility of this finding depends on robust, well-powered validation.
  - **Resolution test** State the number of samples for each metastatic site. Provide a more nuanced interpretation of the clustering results. The differential enhancer analysis between lung and brain metastases is more compelling evidence for adaptation; consider making this the primary focus of the claim. Validate the predictive model in an independent cohort.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The claim that ProCapNet models can predict the functional impact of noncoding variants and enable prioritization, as exemplified by the IL2RB variant.
  - **Evidence pointer** Results section "Sequence determinants of transcription initiation...", Figure 4, Figure 3f
  - **Concern** The manuscript demonstrates that ProCapNet can predict the effect of a known variant (rs17712208) in a liver-specific TRE. However, the generalizability of this approach is unclear. The example is a single, hand-picked case. The claim that this framework is "broadly applicable" needs more systematic validation. The performance of the model on held-out chromosomes is described, but the actual metrics are not shown.
  - **Why it matters** The utility of the atlas for variant prioritization is a major selling point. A single example, however compelling, is not sufficient to establish the framework's general utility. The field needs to see systematic benchmarking of prediction accuracy against known functional variants.
  - **Resolution test** Provide a systematic evaluation of ProCapNet's variant effect predictions against a larger set of validated regulatory variants. Show the distribution of predicted effects and how they correlate with experimental measurements. Provide the actual performance metrics for the held-out chromosome predictions.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Methods section "Profile features"
  - **Evidence pointer** Methods, "Profile features" section
  - **Issue** The methods section for "Profile features" is incomplete. It defines the three features (shape index, directionality index, distance between TSSs) but does not provide the precise mathematical definitions or the computational tools used to calculate them.
  - **Required correction** Provide the full definitions and cite the specific software or code used for these calculations.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Data and code availability
  - **Evidence pointer** Data and Code Availability sections
  - **Issue** While the data and code are deposited, the code repository link is generic. It is unclear if the specific scripts for all analyses (e.g., S-LDSC, TORUS, ProCapNet training, CRISPR screen analysis) are included and documented.
  - **Required correction** Provide a more detailed description of the code repository contents, including a README that outlines how to reproduce the key analyses.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Figure 3e, differential TRE analysis in T1D
  - **Evidence pointer** Results, "Tissue-specific effects..." section
  - **Concern** The differential expression analysis of TREs between T1D and control T cells uses DESeq2, which is appropriate. However, the number of biological replicates per group is not stated. This is critical for assessing the power and reliability of the differential calls.
  - **Required correction** State the number of T1D and control samples used in the differential analysis.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Interpretation
  - **Affected element** Discussion of evolutionary constraints
  - **Evidence pointer** Results, "Evolutionary forces..." section
  - **Concern** The finding that broadly active TREs are more conserved is presented as a novel insight. This is consistent with established knowledge about housekeeping gene regulation and the general properties of promoters versus enhancers. The authors should more explicitly acknowledge prior work in this area.
  - **Required correction** Add citations to prior studies that have shown similar relationships between tissue breadth, expression level, and evolutionary conservation for regulatory elements.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1: The quality control data for the PRO-cap protocol is not shown, which is foundational.
  - R1-M2: The sample size for the metastatic cancer analysis is small, and the interpretation of "adaptation" is not fully supported.
  - R1-M3: The generalizability of the ProCapNet variant prioritization framework is not established beyond a single example.
- **Assessment against Nature-style criteria**
  - **Originality** The work is not entirely original in concept, as transcription initiation has been used to identify regulatory elements before. However, the scale and breadth of the tissue atlas, combined with the deep learning integration, represents a significant and original contribution.
  - **Scientific importance** The atlas is a potentially important resource for the field. The demonstration that transcription-based TREs are more functionally enriched than epigenomic annotations alone is an important conceptual point. The framework for tissue-specific variant prioritization has clear scientific and clinical importance.
  - **Interdisciplinary readership** The work will appeal to molecular biologists, genomicists, computational biologists, and clinical geneticists. The clinical applications in cancer and autoimmune disease broaden its appeal.
  - **Technical soundness** The core PRO-cap protocol appears sound, but the lack of quality control data is a major concern. The computational analyses are state-of-the-art, but the validation of the variant prioritization framework is limited.
  - **Readability for nonspecialists** The abstract and introduction are clear and accessible. The results section is dense and will be challenging for nonspecialists, but this is typical for a methods-heavy genomics paper. The figures, if they match the descriptions, would greatly aid comprehension.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a valuable resource and a compelling conceptual framework. However, the foundational quality control data must be provided, and the key claims regarding metastatic cancer and variant prioritization need to be either more robustly supported or more carefully qualified. The current evidence, as presented in the text alone, is not sufficient to fully establish all the major claims.

## Risk / unsupported claims
- The claim of "high concordance" between the optimized and original PRO-cap protocols is unsupported without the data.
- The claim that metastatic TRE landscapes reflect "adaptive responses to distant niches" is an interpretation that is not directly supported by the presented analysis.
- The claim that the ProCapNet framework enables "prioritization and functional interpretation of noncoding variants" is only supported by a single example and is therefore not fully established.
- The claim that the atlas provides a "one-stop-shop" for prioritizing active enhancers and promoters is an overstatement, as the manuscript itself notes limitations in detecting low-level transcription.