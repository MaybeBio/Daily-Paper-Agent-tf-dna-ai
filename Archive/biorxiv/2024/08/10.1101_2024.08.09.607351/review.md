## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, results, methods, and bibliography
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and suitability for a Nature-style journal
- **Shared manuscript claim summary** The authors present Xenusia, a neural network-based tool for identifying DNA-binding proteins in archaea, trained exclusively on bacterial proteins to avoid bias, validated on archaeal datasets including Asgard metagenomics data, and supported by experimental characterization of three predicted archaeal DNA-binding proteins
- **Visible evidence base** Abstract, introduction, results sections (computational approach, computational validation, large-scale analysis of Asgard metagenomics, experimental characterization), methods sections (datasets, NN1, NN2, experimental characterization), bibliography
- **Missing materials affecting confidence** Figures 1, 2, and 3 are referenced but not provided; Supplementary Tables 1, 2, and 3 and Supplementary Figures 1 and 2 are referenced but not provided; no detailed performance metrics beyond AUC and AP values; no code or dataset availability verification; no statistical significance testing reported

## Reviewer

- **Overall assessment** The manuscript addresses a genuinely important problem, the under-annotation of archaeal proteins, and proposes a creative solution that avoids reliance on evolutionary information. The two-stage architecture, separating DNA-interacting residue prediction from domain prediction, is conceptually sound and well motivated. However, the evidence presented in the visible text is insufficient to fully evaluate the claims. Key performance metrics are reported without confidence intervals or statistical comparisons, the experimental validation is described qualitatively without quantification, and the referenced figures and supplementary materials, which would provide critical supporting evidence, are not available for assessment. The claim of superiority over state-of-the-art methods rests on a single table that cannot be inspected. The experimental section, while commendable for including wet-lab validation, lacks controls and quantitative binding data. The manuscript has potential but, in its current form, the case is not fully established from the provided materials.

- **Who would be interested in the results, and why** Computational biologists working on protein function prediction, particularly those focused on under-studied organisms, would find the approach relevant. Archaeal microbiologists studying Asgard archaea and eukaryotic origins would value the identification of novel DNA-binding proteins in this under-explored group. Researchers developing machine learning methods for protein annotation that avoid evolutionary dependencies would be interested in the architectural choices. The experimental validation of computational predictions, while limited, may interest researchers who advocate for combining in-silico and wet-lab approaches.

- **Major strengths** The problem is well defined and important. The decision to train exclusively on bacterial proteins and validate on archaeal proteins is a thoughtful design choice that directly addresses overfitting concerns. The two-stage architecture, separating residue-level from domain-level prediction, is a reasonable and interpretable approach. The inclusion of experimental validation, even if limited, is a strength that many purely computational papers lack. The tool is made available as a PyPI package and Colab notebook, which supports reproducibility and community use.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that Xenusia provides the best predictions compared to all other available methods, with a Matthew's correlation coefficient surpassing the second best predictor by 25 percent
- **Evidence pointer** Table 1, location not provided
- **Concern** The central performance claim rests entirely on Table 1, which is not visible in the provided material. Without access to the table, the comparison with state-of-the-art methods cannot be verified. Furthermore, no confidence intervals, standard deviations, or statistical significance tests are reported for any of the performance metrics. The threshold selection procedure, setting the threshold equal to the specificity of the best performing method, is described but the resulting confusion matrix and its components are not shown.
- **Why it matters** The claim of state-of-the-art performance is the primary quantitative basis for the tool's utility. Without verifiable data and statistical rigor, the claim cannot be assessed, and the reader cannot determine whether the observed differences are meaningful or within noise.
- **Resolution test** Provide Table 1 with full performance metrics, including confidence intervals or error bars, and report statistical significance tests comparing Xenusia to each baseline method. If possible, include precision-recall curves and ROC curves for all methods on the same validation set.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation rigor
- **Claim pointer** The manuscript claims experimental validation of Xenusia predictions, stating that three Asgard proteins were produced, purified, and assessed for DNA-binding capability
- **Evidence pointer** Figure 3, Supplementary Figure 2, Supplementary Tables 2 and 3, location not provided
- **Concern** The experimental section describes gel electrophoresis followed by autoradiography for three proteins against three DNA probes each. However, the results are described only qualitatively, with statements such as "Figure 3 clearly shows that OLS17986 binds to all three probes." No quantification of binding is provided, no negative control protein is described, and no competition experiments with unlabeled specific or nonspecific DNA are reported. The use of salmon sperm DNA as competitor is mentioned, but the concentration and specificity of competition are not detailed. The crescent protein concentration experiment for OLS23561 is mentioned but the results are not described.
- **Why it matters** DNA-binding assays are prone to false positives from nonspecific electrostatic interactions. Without proper controls, quantification, and competition experiments, the experimental evidence for DNA-binding is suggestive but not conclusive. The claim of experimental validation is a key differentiator of this work and must be rigorously supported.
- **Resolution test** Provide quantified binding data, such as fraction of probe shifted or dissociation constants, include a negative control protein known not to bind DNA, and perform competition experiments with unlabeled specific and nonspecific DNA to demonstrate specificity. Show the crescent concentration data for OLS23561 with quantification.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Dataset representativeness and validation
- **Claim pointer** The manuscript claims that the validation dataset contains solely archaeal proteins and that all datasets were curated to ensure sequence identity below 20 percent
- **Evidence pointer** Methods section, Datasets, location not provided
- **Concern** The validation dataset is described as containing 211 archaeal proteins, of which 174 are negative and 37 are positive. The positive set was identified from literature, but the criteria for literature selection are not described. The negative set was selected based on extensive UniProt annotations with no reported DNA-binding activity, but the absence of evidence is not evidence of absence. The 20 percent sequence identity threshold is stated but the clustering method and its parameters are not fully detailed. The number of proteins in the training datasets is not stated, and the balance between positive and negative examples in training is not described.
- **Why it matters** The validity of the performance claims depends entirely on the quality and representativeness of the validation set. A small positive set, potential mislabeling of negatives, and unclear literature selection criteria could bias the reported performance. The training set composition directly affects the model's ability to generalize.
- **Resolution test** Provide detailed statistics on dataset sizes, positive-negative ratios, literature sources for positive annotations, and the exact procedure for negative set selection. Describe the CD-HIT clustering parameters and report the distribution of sequence identities within and across datasets.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability and biological insight
- **Claim pointer** The manuscript claims that the unannotated Asgard protein OLS30097 displays a reversed topology compared to a known archaeal HTH DNA-binding protein, suggesting independent convergent evolution
- **Evidence pointer** Figure 2, Supplementary Figure 1, location not provided
- **Concern** The structural comparison between the AlphaFold predicted structure of OLS30097 and the crystal structure of 5box is described as showing reversed topology, with the former beginning with a globular domain and concluding with a long alpha helix, while the latter starts with a long alpha helix and finishes with the globular domain. This is an interesting observation, but the structural alignment result in Supplementary Figure 1 is not visible. The claim of convergent evolution is speculative and would require phylogenetic or additional structural evidence to support.
- **Why it matters** The biological insight derived from the structural comparison is a notable aspect of the paper, but the evidence is not assessable without the figures. The interpretation of reversed topology as convergent evolution is a strong claim that requires careful support.
- **Resolution test** Provide Figure 2 and Supplementary Figure 1 with clear structural alignments and RMSD values. Discuss alternative explanations for the observed topology, such as domain swapping or evolutionary descent with structural rearrangement, and justify the convergent evolution interpretation.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and completeness
- **Affected element** Abstract
- **Evidence pointer** Abstract, location not provided
- **Issue** The abstract states that Xenialis has proven effective across diverse datasets, including metagenomics data, with experimental validation of its predictions. However, no quantitative performance figures are given in the abstract, and the term "proven effective" is vague.
- **Required correction** Include key performance metrics, such as AUC or MCC values, in the abstract to give readers a concrete sense of the tool's performance.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** NN1 architecture
- **Evidence pointer** Methods, Prediction of DNA-interacting residues, location not provided
- **Concern** The description of NN1 states that it uses a 2-layer gated recurrent unit (GRU) neural network with a hidden size of 7, followed by max-pooling and sigmoid activation. The choice of hidden size 7 is unusually small and not justified. The number of parameters and the potential for underfitting are not discussed.
- **Required correction** Justify the choice of hidden size 7, or report a hyperparameter search that led to this value. Discuss the model capacity in relation to the training set size.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Experimental detail
- **Affected element** DNA-binding assay
- **Evidence pointer** Methods, Experimental characterization, location not provided
- **Issue** The DNA-binding assay description mentions protein concentrations of 11.24, 5.20, and 64.22 micromolar for the three proteins, but the DNA probe concentration is not stated. The ratio of protein to DNA is critical for interpreting binding results.
- **Required correction** Report the DNA probe concentration used in the assay and the molar ratio of protein to DNA for each experiment.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Code and data availability
- **Evidence pointer** Abstract, location not provided
- **Issue** The manuscript states that the tool is available as a PyPI package and on GitHub, and that datasets are available in the associated Git repository. However, the specific repository structure, versioning, and any dependencies are not described.
- **Required correction** Provide a clear description of the repository contents, including training and validation datasets, model weights, and a usage example. Consider adding a persistent DOI for the code and data.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction, location not provided
- **Issue** The introduction mentions the observational selection bias and the challenges of annotating archaeal proteins, but does not discuss existing computational tools for DNA-binding protein prediction in detail. The comparison with state-of-the-art methods in Table 1 would benefit from a more thorough introduction of these methods.
- **Required correction** Briefly describe the existing methods compared in Table 1, their approaches, and their limitations, to provide context for the claimed improvements.

## Risk / unsupported claims

- The claim that Xenialis provides the best predictions compared to all other available methods is unsupported without access to Table 1 and statistical significance testing
- The claim of experimental validation of DNA-binding capability is not fully supported without quantification, controls, and competition experiments
- The claim of convergent evolution for OLS30097 is speculative and not fully supported without additional structural and phylogenetic evidence
- The claim that the tool is resistant to overfitting due to exclusive training on bacterial proteins is plausible but not empirically demonstrated beyond the reported validation performance
- The claim that the tool can identify convergent evolution is not directly tested or demonstrated
- The generalizability of the tool to all archaeal proteins, beyond the Asgard dataset, is not established
- The performance of the tool on metagenomics data is mentioned but not quantified in the visible text