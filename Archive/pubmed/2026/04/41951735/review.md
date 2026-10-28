## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, novelty, and significance of the presented claims; assessment is limited to the provided manuscript content
- **Shared manuscript claim summary** The authors present the Human Development Multiomic Atlas (HDMA), a single-cell atlas of chromatin accessibility and gene expression from 817,740 fetal cells across 12 organs, spanning 203 cell types and over 1 million candidate cis-regulatory elements. They train deep learning models (ChromBPNet) to predict accessibility from DNA sequence, identify a lexicon of 508 regulatory motifs, and systematically characterize motif syntax, distinguishing "hard" and "soft" cooperative rules. They further link motif disruption to disease-associated variants and expression quantitative trait loci.
- **Visible evidence base** Main text figures 1-6, Extended Data Figures 1-10, Supplementary Tables 1-14, Supplementary Notes 1-3, and Methods section
- **Missing materials affecting confidence** Supplementary Notes and Tables are referenced but not fully provided; detailed model architecture hyperparameters are not fully specified; raw data quality metrics for individual samples are not shown; code availability is mentioned but not verified

## Reviewer

### Overall assessment
This manuscript presents a substantial and impressive resource: a multi-organ, multi-modal single-cell atlas of human fetal development with deep learning-based regulatory analysis. The scale of data (817,740 cells, 12 organs, 203 cell types) and the integration of chromatin accessibility with gene expression from the same cells represents a significant advance over existing resources. The deep learning framework for motif discovery and syntax analysis is methodologically rigorous and yields biologically meaningful insights, including the identification of hard versus soft syntactic constraints and the discovery of negative regulatory motifs. The validation using VENUS enhancer assays and the connection to disease-associated variants strengthen the translational relevance. However, several technical concerns regarding model validation, statistical rigor, and the interpretation of negative motifs warrant clarification before the claims are fully established.

### Who would be interested in the results, and why
This work will be of broad interest to developmental biologists, regulatory genomics researchers, computational biologists, and clinicians studying congenital disorders. The HDMA resource itself will be a valuable reference for the community, enabling studies of cell-type-specific gene regulation during human development. The deep learning framework and the systematic characterization of motif syntax provide a methodological template applicable to other tissues and organisms. The identification of fetal-specific regulatory elements and disease-associated variant effects has implications for understanding the developmental origins of adult disease.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of deep learning model validation
- **Claim pointer** The authors claim that ChromBPNet models "learn likely causal sequence features that are directly predictive of chromatin accessibility" and use these models to identify regulatory motifs and predict variant effects.
- **Evidence pointer** Methods: ChromBPNet model training; Figure 3b,c; Extended Data Figures 4 and 5a,b
- **Concern** The manuscript reports median Pearson correlation of 0.78 between predicted and observed log counts in held-out peaks, but does not provide a rigorous comparison against baseline models or alternative architectures. It is unclear whether this performance reflects genuine sequence-based predictive power or simply captures local sequence composition biases. Furthermore, the authors do not report performance on negative control sequences (e.g., shuffled sequences with matched GC content) or demonstrate that the models generalize across chromosomes in a strictly held-out manner. The fivefold cross-validation scheme uses chromosome-level splits, which is appropriate, but the manuscript does not specify whether the same chromosomes are used across all cell types, which could introduce confounding.
- **Why it matters** The validity of all downstream analyses, including motif discovery, syntax characterization, and variant effect prediction, depends critically on the models learning genuine sequence determinants of accessibility rather than artifacts. Without adequate baseline comparisons and negative controls, the biological interpretations may be overclaimed.
- **Resolution test** Provide model performance comparisons against (1) a simple sequence composition model, (2) a model trained on shuffled sequences, and (3) an alternative architecture (e.g., BPNet or Basenji). Report performance stratified by genomic context (promoter, enhancer, heterochromatin) and demonstrate that motif importance scores are specific to the trained models by comparing to models trained with randomized labels.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor of motif syntax classification
- **Claim pointer** The authors classify 67 of 138 composite motifs as synergistic, with 48 exhibiting "hard" syntax and 19 exhibiting "soft" syntax, based on in silico marginalization.
- **Evidence pointer** Methods: In silico marginalizations; Figure 4h-j; Supplementary Table 7
- **Concern** The classification of hard versus soft syntax relies on a z-score threshold of 4 for identifying preferred arrangements. This threshold appears arbitrary and is not justified statistically. The manuscript does not report the distribution of z-scores across all composite motifs, nor does it provide confidence intervals for the classification. Additionally, the in silico marginalization approach uses only 100 background sequences, which may be insufficient to capture the full diversity of genomic contexts, potentially leading to unstable estimates of joint effects. The authors also do not address multiple testing concerns when classifying 138 motifs.
- **Why it matters** The distinction between hard and soft syntax is a central conceptual contribution of the paper. If the classification is not statistically robust, the conclusions about the prevalence and nature of syntactic constraints in human development may be unreliable.
- **Resolution test** Provide a more rigorous statistical framework for classifying syntax, such as permutation-based significance testing with false discovery rate control. Report the full distribution of z-scores and effect sizes for all 138 composite motifs. Increase the number of background sequences and demonstrate that classifications are stable across different background sets.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of negative motifs
- **Claim pointer** The authors identify 15 motifs with negative contributions to accessibility and propose that they represent "ubiquitous motifs reducing accessibility," with variants disrupting these motifs associated with increased gene expression.
- **Evidence pointer** Figure 5; Extended Data Figure 9
- **Concern** The interpretation of negative motifs as active repressors of accessibility is intriguing but not fully supported. The authors show that negative motifs are enriched near nucleosome dyads and depleted near peak summits, and that ablation leads to small increases in predicted accessibility. However, the magnitude of these effects is modest, and the authors do not provide experimental validation for any negative motif. The eQTL analysis shows enrichment for upregulating variants, but the odds ratio for negative motifs is reported as infinity, which is suspicious and suggests zero counts in the shuffled background, potentially indicating a statistical artifact. The authors also do not rule out alternative explanations, such as negative motifs representing transcription factor binding sites that compete with positive regulators or that are associated with nucleosome positioning rather than active repression.
- **Why it matters** The discovery of negative regulatory motifs is a novel claim that challenges conventional views of accessibility. If not rigorously validated, this claim could mislead the field. The infinity odds ratio raises concerns about the statistical methodology.
- **Resolution test** Provide experimental validation for at least one negative motif, such as reporter assays or CRISPR-based perturbation. Re-analyze the eQTL enrichment using a more robust statistical approach that avoids infinite odds ratios, such as adding pseudocounts or using Fisher's exact test with a continuity correction. Discuss alternative interpretations of negative motifs and provide additional analyses to distinguish between active repression and passive competition.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability of VENUS enhancer validation
- **Claim pointer** The authors state that "many of which exhibit organ-specific in vivo enhancer activity" based on VENUS enhancer assays.
- **Evidence pointer** Figure 2f-h; Extended Data Figure 3
- **Concern** The VENUS validation is performed in mouse embryos at E11.5, which is developmentally earlier than the human fetal samples (PCW 10-23). The authors acknowledge this limitation but do not fully address how cross-species and cross-temporal differences might affect the interpretation. The number of enhancers tested is not clearly stated, and the selection criteria for which enhancers to validate are not described. The authors report that 6 enhancers previously annotated as heart-specific showed liver activity, but the total number of enhancers tested and the overall validation rate are unclear.
- **Why it matters** The VENUS validation is a key piece of evidence supporting the biological relevance of the HDMA enhancers. If the validation is not systematic or representative, the claim of organ-specific enhancer activity may be overstated.
- **Resolution test** Clearly state the number of enhancers tested, the selection criteria, and the overall validation rate. Discuss the implications of cross-species and cross-temporal differences for the interpretation of enhancer activity. Consider validating a random sample of enhancers to assess the overall precision of the atlas.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Completeness of variant effect predictions
- **Claim pointer** The authors identify 28 fetal-specific disease-associated variants predicted to alter accessibility and highlight two examples.
- **Evidence pointer** Figure 6; Supplementary Tables 11-13
- **Concern** The manuscript presents only two detailed examples of variant effect predictions. The remaining 26 fetal-specific variants are listed in supplementary tables but not discussed. The authors do not provide a systematic evaluation of the predicted effects, such as the distribution of effect sizes, the concordance with eQTL data, or experimental validation of any predicted variant effect. The choice to highlight the asthma and CAD variants appears selective, and it is unclear whether these are representative or exceptional cases.
- **Why it matters** The clinical relevance of the atlas depends on the reliability of variant effect predictions. Without systematic evaluation or experimental validation, the predictive power of the models for disease-associated variants remains uncertain.
- **Resolution test** Provide a systematic summary of all 28 fetal-specific variants, including predicted effect sizes, confidence intervals, and concordance with eQTL data. Validate at least one additional variant experimentally. Discuss the limitations of the prediction approach and the potential for false positives and false negatives.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of cell type annotation
- **Affected element** Figure 1c,d; Methods: Cell type annotation
- **Evidence pointer** Figure 1c,d; Methods
- **Issue** The iterative cell type annotation approach is described, but the manuscript does not provide a detailed assessment of annotation confidence or a comparison with existing atlases. The number of cells per cell type and the balance across organs are not clearly presented.
- **Required correction** Provide a supplementary figure showing the number of cells per cell type and organ, and include a discussion of annotation confidence, perhaps using marker gene expression heatmaps or comparison with published atlases.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical details of VENUS enhancer analysis
- **Affected element** Figure 2f; Methods: VENUS enhancer analysis
- **Evidence pointer** Figure 2f; Methods
- **Issue** The Wilcoxon rank-sum test P values for VENUS enhancer enrichment are reported, but the effect sizes (AUROC) are only given for brain, heart, and eye. The number of enhancers in each category and the total number tested are not stated.
- **Required correction** Report the number of enhancers in each category and the total number tested. Provide AUROC values for all organs, not just the three highlighted.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity of motif nomenclature
- **Affected element** Figure 3e; Supplementary Table 6
- **Evidence pointer** Figure 3e; Supplementary Table 6
- **Issue** The motif naming scheme is complex and may be difficult for non-specialists to interpret. The relationship between de novo motif IDs and known transcription factor families is not always clear.
- **Required correction** Provide a simplified summary table mapping de novo motif IDs to transcription factor families, with a brief description of the evidence for each assignment.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability statement
- **Affected element** Data availability section
- **Evidence pointer** Data availability section
- **Issue** The data availability section is not included in the provided text. Given the resource nature of this work, clear and detailed data availability statements are essential.
- **Required correction** Ensure the final manuscript includes a comprehensive data availability statement detailing accession numbers for raw and processed data, model weights, and code.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Discussion section
- **Evidence pointer** Discussion section
- **Issue** The discussion of limitations is brief and does not fully address the potential biases in the dataset (e.g., tissue sampling, gestational age range) or the limitations of the deep learning approach for capturing long-range regulatory interactions.
- **Required correction** Expand the limitations paragraph to include a more thorough discussion of dataset biases and the scope of the deep learning models.

### Technical failings that need to be addressed before the case is established
R1-M1 (model validation) and R1-M2 (statistical rigor of syntax classification) are the most critical technical issues. The lack of baseline comparisons and negative controls for the deep learning models undermines confidence in the motif discovery and variant effect predictions. The arbitrary z-score threshold for hard versus soft syntax classification needs to be replaced with a statistically justified approach. R1-M3 (negative motifs) also requires additional validation and more robust statistical analysis.

### Assessment against Nature-style criteria
- **Originality** High. The integration of multi-organ, multi-modal single-cell data with deep learning-based regulatory analysis is novel. The systematic characterization of hard versus soft syntactic constraints and the identification of negative regulatory motifs represent conceptual advances.
- **Scientific importance** High. The HDMA resource will be a valuable community reference. The findings on motif syntax and negative regulation have implications for understanding developmental gene regulation and interpreting disease-associated variants.
- **Interdisciplinary readership** High. The work bridges developmental biology, genomics, and machine learning, and will appeal to a broad readership across these fields.
- **Technical soundness** Moderate. The scale and quality of the data are impressive, and the deep learning approach is appropriate. However, the lack of rigorous model validation and the arbitrary statistical thresholds for syntax classification are significant weaknesses that need to be addressed.
- **Readability for nonspecialists** Good. The manuscript is generally well-written and accessible, with clear figures. The complex methodology is explained in the Methods section, and the main text focuses on biological insights. However, the motif nomenclature and some of the deep learning concepts may be challenging for non-specialists.

### Recommendation posture
Supportive if technical concerns are resolved. The manuscript presents a valuable resource and novel biological insights, but the technical concerns regarding model validation and statistical rigor must be addressed before the claims are fully established. I recommend major revision to address these issues.