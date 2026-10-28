## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) from bioRxiv preprint
- **Assessment boundary** Scientific and technical evaluation of the presented claims, methods, and results; no assessment of editorial fit or publication venue
- **Shared manuscript claim summary** The authors present MaSIF-PMP, a geometric deep learning model using molecular surface fingerprints to predict interfacial binding sites (IBSs) of peripheral membrane proteins (PMPs). They claim superior performance over existing IBS predictors, distinct feature determinants versus protein-protein interactions, and that MD simulations can validate predictions, refine IBS labels, and capture composition-dependent binding patterns.
- **Visible evidence base** Main text figures referenced (Figures 1-7), supplementary figures and tables referenced but not provided in full, methods section, abstract
- **Missing materials affecting confidence** Supplementary Information (16 figures, 5 tables) not provided; benchmark dataset details not fully specified; hyperparameter choices and model architecture details partially described; statistical significance testing not reported in main text

## Reviewer
- **Overall assessment** The manuscript presents a potentially valuable extension of the MaSIF framework to protein-membrane interactions, with a reasonable methodological approach and promising initial results. However, several technical aspects require clarification and additional validation before the central claims can be fully assessed. The comparison to existing methods, the interpretation of ablation and transfer learning results, and the utility of MD-based label refinement are all areas where the evidence as presented is suggestive but not yet conclusive. The work addresses an important problem and the surface-based approach is well motivated, but the current evidence base is insufficient to fully establish the claimed advantages.

- **Who would be interested in the results, and why** Researchers in computational biophysics, membrane biology, and protein surface prediction would find this work relevant. Those developing geometric deep learning methods for biomolecular surfaces would be interested in the extension of MaSIF to a new interaction type. Experimentalists studying peripheral membrane proteins may find the prediction tool useful for identifying candidate binding regions. The demonstration that MD simulations can refine IBS labels could interest those working at the interface of machine learning and molecular simulation.

- **Major strengths** The problem is well motivated and important. The surface-based approach is a sensible extension of a proven framework. The use of a large dataset (nearly 1,200 PMPs) is a strength. The integration of MD simulations for label refinement is a creative and potentially valuable contribution. The ablation study and transfer learning analysis represent thoughtful attempts to understand feature contributions and model transferability.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "MaSIF-PMP outperformed all other predictors in both per-protein residue-level ROC AUC and MCC"
- **Evidence pointer** Section 2.2, Figure 3
- **Concern** The benchmark comparison against existing methods is described only at a high level. The number of benchmark proteins (21) is small, and the details of how predictions from other methods were obtained (e.g., whether they were retrained, used with default parameters, or applied to the same surface representations) are not provided. The manuscript states that labels for three benchmark proteins were updated to match the authors' test set labels, which introduces a potential source of bias in favor of MaSIF-PMP. Statistical significance of the performance differences is not reported.
- **Why it matters** The central claim of superior performance is the primary basis for recommending MaSIF-PMP over existing tools. Without clear benchmarking protocols, statistical testing, and transparency about label modifications, the claim cannot be reliably evaluated.
- **Resolution test** Provide full details of benchmark setup, including how each competing method was configured, whether hyperparameters were optimized, and whether the label updates for the three proteins were applied consistently to all methods. Report confidence intervals or significance tests for the performance differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "feature ablation studies and transfer learning analyses reveal distinct determinants governing protein-membrane versus protein-protein interactions"
- **Evidence pointer** Section 2.3, Figure 5
- **Concern** The ablation study is performed using five-fold cross-validation on the full dataset, but the manuscript does not report the variance across folds. The conclusion that geometric features are "more critical" than chemical features is based on median ROC AUC values, but the magnitude of the differences and their statistical significance are not reported. The transfer learning results show that MaSIF-PMP trained from scratch outperforms both transfer learning strategies, which is interpreted as evidence for distinct feature spaces. However, the transfer learning architectures are not described in sufficient detail to assess whether the comparison is fair (e.g., whether the frozen convolutional layers from MaSIF-site are appropriate for the different input feature distributions of PMPs).
- **Why it matters** The claim of distinct determinants is a key scientific contribution of the work. If the differences are within noise or arise from suboptimal transfer learning configurations, the conclusion would be substantially weakened.
- **Resolution test** Report fold-wise results with variance or confidence intervals for the ablation study. Provide full architectural details of the transfer learning models and justify the design choices. Consider testing whether fine-tuning all layers (rather than freezing convolutional layers) changes the conclusions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "molecular dynamics (MD) simulations can validate model predictions, refine IBS labels, and capture composition-dependent membrane binding patterns"
- **Evidence pointer** Sections 2.4, 2.5, Figures 6-7
- **Concern** The claim that MD simulations can validate model predictions is not clearly demonstrated. For the α-TTP case study, the manuscript reports ROC AUC values of 0.81 (crystal structure) and 0.75 (MD-derived conformation) against HMMS-derived labels, but it is unclear how these values compare to what would be expected by chance or by simpler baselines. The claim that MD can "refine IBS labels" is based on the observation that MaSIF-PMP achieves higher ROC AUC against HMMS-derived labels than against original dataset labels for poorly predicted proteins. However, this could reflect that the HMMS labels are more permissive or differently defined rather than more accurate. The manuscript does not provide evidence that the HMMS-derived labels are biologically correct, only that they differ from the original labels.
- **Why it matters** The MD-based label refinement is presented as a significant contribution. If the HMMS labels are not validated against experimental data, the claim that they represent improved ground truth is not established.
- **Resolution test** Provide evidence that HMMS-derived IBS labels correspond to experimentally known binding regions for at least some cases. Compare MaSIF-PMP performance against HMMS labels versus original labels using the same evaluation protocol. Discuss potential circularity if HMMS labels are derived from the same structural features used by the model.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "we present MaSIF-PMP, a geometric deep learning model"
- **Evidence pointer** Section 4 (Methods)
- **Concern** The manuscript does not state whether the model code, trained weights, or the dataset will be made publicly available. The dataset is described as "previously published" but the specific accession or download information is not provided. The preprocessing pipeline (MSMS, PyMESH, feature computation) is described but the exact parameters and scripts are not provided.
- **Why it matters** Reproducibility is a core expectation for computational methods papers. Without access to code and data, other researchers cannot apply or extend the method.
- **Resolution test** State data and code availability clearly. Provide links to repositories or state explicitly if materials will not be shared.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1, Figure 1
- **Evidence pointer** Figure 1
- **Issue** The description of the model architecture in the main text is brief. The number of convolutional layers, kernel sizes, pooling strategies, and the architecture of the MLP head are only partially described in the main text and the reader is referred to the Methods and Supplementary Information.
- **Required correction** Provide a concise summary of the full architecture in the main text or ensure the Methods section contains all necessary details for reproduction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 2.2, Figure 3
- **Evidence pointer** Figure 3
- **Issue** The manuscript reports median ROC AUC and MCC values but does not report the distribution or spread of these metrics across the 21 benchmark proteins.
- **Required correction** Report interquartile ranges or full distributions, and consider reporting per-protein results in a supplementary table.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 2.5, Figure 7
- **Evidence pointer** Figure 7
- **Issue** The statement that "the broader IBS predicted by MaSIF-PMP likely reflects regions that approach the membrane during interaction" is speculative. The manuscript does not provide direct evidence that these broader regions are functionally relevant.
- **Required correction** Soften the language or provide additional analysis (e.g., distance measurements from MD trajectories) to support this interpretation.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4
- **Issue** The MD simulation details (force field parameters, simulation length, number of replicas, convergence criteria) are only briefly mentioned in the main text and deferred to the Supplementary Information.
- **Required correction** Ensure the Methods section contains sufficient detail for reproduction, including system setup, equilibration protocol, and production run lengths.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.3, Figure 5
- **Evidence pointer** Figure 5
- **Issue** The transfer learning results are presented as a single comparison in Figure 5b, but the manuscript does not explain why the two transfer learning strategies were chosen or what specific hypotheses they test.
- **Required correction** Add a brief explanation of the rationale for the two transfer learning configurations and what each is intended to reveal.

- **Technical failings that need to be addressed before the case is established** R1-M1 (benchmark fairness and statistical rigor), R1-M2 (ablation and transfer learning conclusions without variance or full architectural details), R1-M3 (MD label validation without independent ground truth)

## Assessment against Nature-style criteria
- **Originality** Moderate. The application of surface fingerprints to protein-membrane interactions is a reasonable extension of existing work rather than a fundamentally new concept. The integration of MD simulations for label refinement is a novel element, though its value is not yet fully demonstrated.
- **Scientific importance** Potentially significant. Accurate IBS prediction for PMPs would be valuable for understanding membrane biology and for drug discovery. However, the demonstrated improvement over existing methods is not yet conclusive.
- **Interdisciplinary readership** The work bridges machine learning, biophysics, and membrane biology, which could attract interest across these communities. The writing is generally accessible, though some domain-specific terminology may limit broader readership.
- **Technical soundness** The core methodology is sound in principle, but several technical concerns (benchmark fairness, statistical reporting, MD label validation) need to be addressed. The lack of code and data availability is a significant limitation.
- **Readability for nonspecialists** The abstract and introduction are clear and well written. The results section becomes more technical, and some claims would benefit from more explicit explanation of the methods and their limitations.

## Risk / unsupported claims
- The claim that MaSIF-PMP "outperforms" existing methods is not fully supported without statistical testing and transparent benchmarking protocols.
- The claim that feature ablation and transfer learning "reveal distinct determinants" is not fully supported without reporting variance and providing complete architectural details.
- The claim that MD simulations can "validate" model predictions is not established; the HMMS-derived labels lack independent experimental validation.
- The claim that MD simulations can "refine" IBS labels is suggestive but not conclusive, as the improved agreement could reflect label definition differences rather than improved accuracy.
- The statement that broader predicted IBSs "likely reflect regions that approach the membrane" is speculative and not directly supported by the presented data.