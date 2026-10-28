## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions, data availability)
- **Assessment boundary** Scientific validity, methodological soundness, claim substantiation, and presentation quality based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors present DNAffinity, a physics-based machine learning approach that predicts in vitro transcription factor binding affinities using structural and mechanical DNA properties derived from atomistic molecular dynamics simulations. The method reportedly outperforms existing algorithms across uPBM, gcPBM, and HT-SELEX datasets, and when combined with chromatin structure information, provides good estimates of in vivo binding sites in yeast.
- **Visible evidence base** Main text figures referenced (Figures 1–7), Supplementary Figures S2–S12, Supplementary Tables S1–S4, and Supplementary Methods as cited in the text
- **Missing materials affecting confidence** Actual figure content, supplementary data files, detailed hyperparameters for the random forest regressor, exact feature definitions, and the full dataset composition were not available for independent verification

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting approach that integrates physics-based DNA descriptors from molecular dynamics simulations with a machine learning framework for transcription factor binding affinity prediction. The core idea of using theoretically derived, sequence-dependent mechanical properties as features is novel and potentially valuable. However, the manuscript as provided has several significant gaps in methodological detail, and the strength of several key claims cannot be fully assessed without access to the supplementary materials and figures. The in vivo validation is limited to a single transcription factor, which constrains the generalizability of the conclusions. The work is likely of interest to the computational biology and genomics communities, but the current presentation leaves important questions unanswered.

- **Who would be interested in the results, and why** Computational biologists developing transcription factor binding prediction tools, researchers studying DNA mechanics and its role in protein-DNA recognition, experimentalists using in vitro binding assays who need improved predictive models, and bioinformaticians working on integrating structural biophysics with machine learning. The potential extension to epigenetic variants and mismatches would also interest epigenetics researchers.

- **Major strengths**  
  1. The use of physics-based descriptors derived from molecular dynamics simulations is conceptually novel and provides a mechanistic foundation that sequence-only models lack.  
  2. The method is tested across three different experimental platforms (uPBM, gcPBM, HT-SELEX), demonstrating versatility.  
  3. The comparison against multiple existing methods on matched datasets strengthens the benchmarking claims.  
  4. The attempt to bridge in vitro predictions to in vivo binding using chromatin structure is a valuable and practical extension.  
  5. The method is made available via a public GitHub repository, supporting reproducibility.

- **Major Concerns**

  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Methodological transparency  
  - **Claim pointer** The method uses "structural and mechanical DNA properties directly derived from atomistic molecular dynamics simulations" as features for a random forest regressor.  
  - **Evidence pointer** Materials and Methods, Feature classes section; Supplementary Table S1  
  - **Concern** The manuscript does not provide sufficient detail on the exact features used, how they were computed from the MD simulations, the simulation protocols, or the force fields employed. The "Feature classes" section is essentially empty in the provided text, listing only a reference to Supplementary Table S1. Without this information, the method cannot be reproduced or independently evaluated.  
  - **Why it matters** The central novelty of the approach rests on the quality and relevance of the MD-derived descriptors. If the feature definitions, simulation parameters, and extraction procedures are not fully disclosed, the scientific contribution cannot be verified, and other researchers cannot build upon or benchmark against the method.  
  - **Resolution test** Provide a complete description of all feature classes, including mathematical definitions, the MD simulation setup (force field, water model, salt conditions, simulation length, temperature), and the procedure for extracting tetramer-level properties. This information should be in the main text or fully detailed in the supplementary materials.

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Statistical rigor  
  - **Claim pointer** The model achieves R2 values of 0.93 ± 0.02 for gcPBM, 0.69 ± 0.17 for uPBM, and 0.66 ± 0.19 (0.70 ± 0.14 after SVM filtering) for HT-SELEX.  
  - **Evidence pointer** Results and Discussion, Figures 2–4  
  - **Concern** The reported performance metrics are presented as averages with standard deviations, but the manuscript does not specify how these statistics were computed across transcription factors, whether the same train/test splits were used for all compared methods, or whether confidence intervals were calculated. The high variance in uPBM and HT-SELEX results suggests substantial heterogeneity across TFs, and the manuscript does not discuss which TF families perform well or poorly.  
  - **Why it matters** Without clarity on the statistical methodology, the reader cannot assess whether the reported improvements over existing methods are significant or within the range of expected variability. The claim of "excellent performance" requires appropriate statistical support, especially given the wide standard deviations.  
  - **Resolution test** Specify the exact procedure for computing mean and standard deviation, report per-TF results (e.g., as a distribution or box plot), and perform and report statistical significance testing (e.g., paired tests) against each comparator method.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Validation scope  
  - **Claim pointer** "When complemented with chromatin structure information, our in vitro trained method provides also good estimates of in vivo binding sites in yeast."  
  - **Evidence pointer** Results and Discussion, In vivo testing section; Figure 7  
  - **Concern** The in vivo validation is performed for a single transcription factor (CBF1) in a single organism (S. cerevisiae). The manuscript reports a true positive rate of 94% but a precision of only 14% before chromatin correction, which drops to 11% false positive rate after including nucleosome maps. The authors argue that most false positives are explained by nucleosome occupancy, but this interpretation relies on the accuracy of the nucleosome maps and the assumption that nucleosome-occupied sites are universally inaccessible.  
  - **Why it matters** A single TF example is insufficient to establish generalizable claims about in vivo predictive power. The low precision before chromatin correction raises questions about the specificity of the intrinsic affinity predictions. The manuscript acknowledges the difficulty of generalization but still presents this as a key result.  
  - **Resolution test** Validate on additional TFs with available paired in vitro and in vivo data. Provide quantitative comparison against existing in vivo prediction methods. Report precision-recall curves and discuss the biological plausibility of the remaining false positives.

  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Benchmarking fairness  
  - **Claim pointer** "The method is able to predict affinities obtained with techniques as different as uPBM, gcPBM and HT-SELEX with an excellent performance, much better than existing algorithms."  
  - **Evidence pointer** Results and Discussion, Comparison section; Figure 5  
  - **Concern** The comparison against existing methods is described, but the manuscript does not clarify whether all methods were retrained on the same data splits, whether hyperparameters were optimized equally for all methods, or whether the comparator implementations were taken from their original publications or reimplemented. The choice of comparators also appears selective, and some recent deep learning methods are not included.  
  - **Why it matters** Unfair or inconsistent benchmarking can lead to inflated claims of superiority. The reader needs assurance that the comparison was conducted under identical conditions to trust the conclusion that DNAffinity outperforms all existing methods.  
  - **Resolution test** Describe the exact benchmarking protocol, including data splits, hyperparameter tuning procedures, and software versions for all methods. Consider including additional state-of-the-art methods and report results on identical train/test partitions.

  - **Concern ID** R1-M5  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Data leakage and preprocessing  
  - **Claim pointer** The method uses "sequence, direct and indirect readout" features, and preprocessing steps include undersampling and weighting.  
  - **Evidence pointer** Materials and Methods, Undersampling and Weighting sections  
  - **Concern** The undersampling and weighting procedures are described only briefly. It is unclear whether these preprocessing steps were applied to the training set only or to the full dataset before splitting. If applied before splitting, this could introduce data leakage and inflate performance estimates. The weighting scheme (uniform weight of 10 for sequences matching PWM) is also not justified.  
  - **Why it matters** Data leakage is a common pitfall in machine learning studies that leads to overly optimistic results. The preprocessing steps must be applied within cross-validation or train/test splits to ensure unbiased evaluation.  
  - **Resolution test** Clarify the order of operations: preprocessing must be applied independently to training folds only. Describe the exact undersampling ratio and weighting scheme, and justify these choices with sensitivity analyses.

- **Minor Comments**

  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Abstract  
  - **Evidence pointer** Abstract  
  - **Issue** The abstract states the method "can be extended to epigenetic variants, mismatches, mutations, or any non-coding nucleobases" but no results demonstrating these extensions are presented in the main text.  
  - **Required correction** Either add supporting results or rephrase to indicate this is a potential future direction rather than a demonstrated capability.

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Terminology  
  - **Affected element** Introduction and Methods  
  - **Evidence pointer** Introduction, Materials and Methods  
  - **Issue** The term "physics-based" is used to describe the approach, but the machine learning model is a random forest regressor, which is not inherently physics-based. The physics enters through the MD-derived features. This distinction should be clarified to avoid overstating the nature of the method.  
  - **Required correction** Rephrase to "a machine learning approach using physics-derived features" or similar.

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Reproducibility  
  - **Affected element** Data availability  
  - **Evidence pointer** Data Availability section  
  - **Issue** The GitHub repository is mentioned, but it is not stated whether the trained models, the full feature database, and the exact code for reproducing all figures are included.  
  - **Required correction** Specify the contents of the repository, including trained model files, feature databases, and scripts for reproducing all main and supplementary figures.

  - **Concern ID** R1-m4  
  - **Severity** Minor  
  - **Axis** Presentation  
  - **Affected element** Results and Discussion  
  - **Evidence pointer** Results and Discussion, In vivo testing section  
  - **Issue** The definition of "consensus exo peaks" is given, but the number of peaks used for evaluation is not stated. The manuscript reports percentages (94% TP, 14% precision) but not absolute numbers, making it difficult to assess the statistical robustness of these estimates.  
  - **Required correction** Report the total number of consensus peaks, the number of true positives, false positives, and the total number of predictions made.

  - **Concern ID** R1-m5  
  - **Severity** Minor  
  - **Axis** Completeness  
  - **Affected element** Methods  
  - **Evidence pointer** Materials and Methods, Feature classes section  
  - **Issue** The "Feature classes" subsection is incomplete in the provided text, with no actual description of the features. This is a critical omission.  
  - **Required correction** Provide a full description of all feature classes in the main text or ensure the supplementary material contains complete details.

## Risk / unsupported claims
- The claim that DNAffinity "can be extended to epigenetic variants, mismatches, mutations, or any non-coding nucleobases" is unsupported by any results in the provided manuscript.
- The claim of "excellent performance, much better than existing algorithms" is only partially supported; the statistical significance of the improvements is not established.
- The in vivo validation claim is based on a single transcription factor and cannot be generalized without additional evidence.
- The statement that "a vast majority of the theoretically false positive are at locations occupied by nucleosomes" is presented as an explanation but the quantitative support depends on the accuracy of the nucleosome maps and the definition of accessibility, which are not fully discussed.
- The relative importance of different feature classes (sequence, direct, indirect readout) is discussed qualitatively but no quantitative ablation study is presented to support the claims about which features matter most.