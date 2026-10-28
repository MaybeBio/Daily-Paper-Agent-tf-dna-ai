## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, supplementary references)
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, reproducibility, and suitability for a computational biology methods journal
- **Shared manuscript claim summary** The authors present Xenusia, a two-stage neural network tool for predicting DNA-binding proteins in archaea, which does not rely on multiple sequence alignment or homology. They report improved performance over existing methods, successful application to Asgard archaeal metagenomic data, and experimental validation of three predicted proteins.
- **Visible evidence base** Methods sections 2.1–2.3, Results sections 3.1–3.4, Figures 1–3, Tables 1, Supplementary Tables S1–S3, Supplementary Figures S1–S2
- **Missing materials affecting confidence** Supplementary data (Tables S1–S3, Figures S1–S2) not provided; training/validation datasets not accessible in the provided material; hyperparameter details for NN1/NN2 incomplete; code repository not reviewed; experimental raw data (gels, quantification) not shown

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in archaeal genomics, where DNA-binding protein annotation is limited. The two-stage architecture is a reasonable design choice given data scarcity. However, several methodological details are missing, the reported performance metrics require closer scrutiny, and the experimental validation has limitations that are only partially acknowledged. The claims of improved performance and successful identification of novel DNA-binding proteins are partially supported but not fully established from the provided evidence.
- **Who would be interested in the results, and why** Researchers working on archaeal genomics and metagenomics, particularly those studying Asgard archaea and their evolutionary significance. Computational biologists developing protein function prediction tools, especially those targeting understudied organisms. Experimentalists seeking to prioritize candidate DNA-binding proteins for validation.
- **Major strengths** 1) Addresses an important gap in archaeal protein annotation. 2) The two-stage architecture is a thoughtful approach to integrate structural and domain-level information while limiting parameters. 3) The tool is made available as a pip package and Google Colab, enhancing accessibility. 4) The inclusion of experimental validation, albeit limited, is commendable. 5) The authors acknowledge limitations of their validation approach.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria** Originality: Moderate. The two-stage architecture is not entirely novel, but its application to archaea is a useful contribution. Scientific importance: Moderate. The tool could be valuable for understudied archaeal genomes, but the impact is limited by the modest performance and validation scope. Interdisciplinary readership: Limited. The manuscript is primarily of interest to computational biologists and archaeal microbiologists. Technical soundness: Partially adequate. Several methodological details are missing, and the performance evaluation has weaknesses. Readability for nonspecialists: Adequate. The manuscript is generally clear, though some technical sections could be expanded for clarity.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding dataset construction, performance evaluation, and experimental validation rigor.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Dataset construction and representativeness
- **Claim pointer** The training datasets (contact and domain) contain only bacterial proteins, and the validation dataset contains only archaeal proteins. The authors claim this design reduces overfitting risk.
- **Evidence pointer** Section 2.1, Section 2.1.1, Section 2.1.2, Section 2.1.3
- **Concern** The decision to train exclusively on bacterial proteins and validate on archaeal proteins is a significant domain shift. While the authors argue this mitigates overfitting, it also means the model may not learn archaeal-specific features. The validation dataset is small (211 proteins, 37 positive) and manually curated, which may introduce selection bias. The authors do not report the sequence identity distribution within the validation set or between validation and training sets beyond the stated <20% threshold. This makes it difficult to assess whether the reported performance generalizes to diverse archaeal proteins.
- **Why it matters** If the model performs well only on proteins similar to those in the small validation set, its utility for large-scale archaeal proteome screening is questionable. The domain shift from bacteria to archaea could lead to systematic errors that are not captured by the current evaluation.
- **Resolution test** Provide a detailed analysis of the validation dataset composition, including sequence identity distribution, functional categories, and taxonomic representation. Report performance stratified by these factors. Additionally, consider including a small set of archaeal proteins in training to assess whether performance improves or degrades.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Performance evaluation and comparison
- **Claim pointer** The authors claim Xenusia provides the best predictions compared to all other available methods, with an MCC surpassing the second best predictor by 25%.
- **Evidence pointer** Section 3.1, Table 1
- **Concern** The comparison with state-of-the-art methods is described only in Table 1, which is not provided in the manuscript text. The authors state that they set a threshold for Xenusia to match the specificity of the best-performing method, but the details of this thresholding procedure are not described. It is unclear whether the comparison is fair, as other methods may have been evaluated under different conditions. Additionally, the reported AUC of 0.79 and precision-recall AUC of 0.60 are modest, and the authors do not report confidence intervals or statistical significance tests for the performance differences.
- **Why it matters** Without a transparent and statistically rigorous comparison, the claim of superior performance is not fully supported. The thresholding procedure could artificially inflate Xenusia's performance relative to other methods.
- **Resolution test** Provide the full Table 1 with all methods, their performance metrics, and the thresholding procedure. Report confidence intervals for all metrics and perform statistical significance tests (e.g., DeLong test for AUC) where appropriate. Describe how the threshold was chosen and whether it was applied consistently to all methods.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation rigor
- **Claim pointer** The authors claim experimental validation of three predicted Asgard DNA-binding proteins, with all three showing DNA-binding activity.
- **Evidence pointer** Section 2.3, Section 3.3, Figure 3, Supplementary Figure S2
- **Concern** The experimental validation is described qualitatively. Figure 3 is not provided, and the authors do not report quantitative measures of binding affinity or specificity. The DNA-binding assay uses promoter regions of nearby genes, which is a reasonable approach, but the choice of probes is not justified in detail. For OLS23561, the authors note that the concentration was too high and only aggregated complexes were observed, requiring a repeat with lower concentrations. This suggests potential issues with experimental reproducibility. The authors also acknowledge that no completely novel proteins (lacking any homology) were tested, which limits the generalizability of the validation.
- **Why it matters** The experimental validation is a key component of the manuscript's claim that Xenusia can identify novel DNA-binding proteins. Without quantitative data and a more rigorous experimental design, the validation is suggestive but not conclusive.
- **Resolution test** Provide quantitative binding data (e.g., dissociation constants, band-shift quantification) for each protein-probe pair. Include negative controls (e.g., a known non-DNA-binding protein) and demonstrate specificity. Justify the choice of probes and include a discussion of potential off-target effects. Consider testing at least one protein with no detectable homology to known DNA-binding proteins.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological transparency
- **Claim pointer** The authors describe the NN1 and NN2 architectures but provide limited details on hyperparameter selection, training procedures, and feature engineering.
- **Evidence pointer** Section 2.2, Section 2.2.1, Section 2.2.2
- **Concern** The manuscript states that NN1 uses a 2-layer GRU with hidden size 7, and NN2 uses a feed-forward network with three layers of 30 neurons. However, details on the number of trainable parameters, regularization techniques, early stopping criteria, and data augmentation are not provided. The feature encoding for NN1 includes DynaMine predictions, but the rationale for choosing these specific features is not fully explained. The authors also do not describe how the sliding window size of 11 was determined.
- **Why it matters** Reproducibility is a core requirement for computational tools. Without complete methodological details, other researchers cannot fully replicate or build upon the work.
- **Resolution test** Provide a comprehensive description of the model architecture, including the number of parameters, training details, and hyperparameter search. Justify the choice of features and window sizes. Consider releasing the training code and configuration files to facilitate reproducibility.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Large-scale analysis interpretation
- **Claim pointer** The authors ran Xenusia on 16,946 Asgard proteins and report the top 10 scoring proteins in Supplementary Table S1.
- **Evidence pointer** Section 3.2, Supplementary Table S1
- **Concern** The large-scale analysis is presented as a demonstration of the tool's utility, but the interpretation is limited. The authors discuss the top hits individually but do not provide a global analysis of the predictions, such as the distribution of scores, the proportion of proteins predicted as DNA-binding, or the functional enrichment of predicted positives. The claim that the tool can identify convergent evolution is based on a single example (OLS30097) and is speculative.
- **Why it matters** A large-scale analysis should provide insights into the predicted DNA-binding protein landscape in Asgard archaea, not just highlight individual examples. The current presentation is anecdotal and does not fully demonstrate the tool's value for genome-wide screening.
- **Resolution test** Provide a summary of the score distribution across the 16,946 proteins, the number of proteins predicted as DNA-binding at various thresholds, and a functional enrichment analysis of the predicted positives. Discuss the implications of the predictions for Asgard archaeal biology.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2.1
- **Evidence pointer** Section 2.2.1
- **Issue** The section title for NN2 (Section 2.2.2) is "NN2 architecture: prediction of DNA-interacting residues," which is identical to the title for NN1. This is likely a typo, as NN2 predicts DNA-binding domains, not residues.
- **Required correction** Change the title of Section 2.2.2 to "NN2 architecture: prediction of DNA-binding domains."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.1.1
- **Evidence pointer** Section 2.1.1
- **Issue** The contact dataset construction uses a PyMOL script to label residues, but the script is not provided or referenced. The distance threshold of 1.5 Å is stated, but the definition of "DNA atom" is not specified (e.g., which atoms in nucleotides are considered).
- **Required correction** Provide the PyMOL script or a detailed description of the labeling procedure, including the specific atoms considered and any additional criteria for defining interactions.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 3.1
- **Evidence pointer** Section 3.1
- **Issue** The performance metrics (AUC, AP, MCC) are reported without confidence intervals or variability measures. The five-fold cross-validation results for NN1 are reported as a single value, but the variance across folds is not shown.
- **Required correction** Report the mean and standard deviation (or confidence intervals) for all performance metrics across cross-validation folds.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Experimental details
- **Affected element** Section 2.3.3
- **Evidence pointer** Section 2.3.3
- **Issue** The DNA-binding assay uses three probes per protein, but the rationale for choosing these specific probes is not fully explained. The authors mention that probes represent promoter regions of nearby genes, but the criteria for selecting these genes are not described.
- **Required correction** Provide a more detailed justification for the choice of probes, including how the genes were selected and whether any prior evidence suggests they are regulated by the protein of interest.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The datasets are stated to be available in the associated Git repository, but the specific file names and formats are not described. This makes it difficult for readers to access and use the data.
- **Required correction** Provide a clear description of the dataset files, their formats, and how to access them in the repository.

## Risk / unsupported claims
- The claim that Xenusia identifies "novel" DNA-binding proteins is not fully supported, as the experimental validation only tested proteins with some sequence similarity to known DNA-binding proteins.
- The claim of convergent evolution for OLS30097 is speculative and based on a single example with no functional validation.
- The claim that Xenusia is resistant to overfitting due to the lack of MSA-based features is not directly tested; no overfitting analysis is presented.
- The performance comparison with state-of-the-art methods is not fully transparent, as the thresholding procedure and full results table are not provided in the manuscript text.
- The generalizability of the tool to diverse archaeal lineages beyond Asgard is not demonstrated.