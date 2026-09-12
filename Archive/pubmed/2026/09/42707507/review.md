## Review setup
- **Input scope** Full manuscript
- **Assessment boundary** The manuscript as provided, including main text, figures referenced in text, and supplementary materials referenced in text. No supplementary data files were provided for independent review.
- **Shared manuscript claim summary** The authors present a transformer-based classifier (ESM-2 with LoRA fine-tuning) for predicting DNA-binding and RNA-binding proteins from human protein sequences. They claim that the model achieves high predictive performance (AUROC 0.84 for DBPs, 0.92 for RBPs) using only sequence information, and that attention-based analysis (VAT scores) reveals biologically meaningful focus on annotated functional domains.
- **Visible evidence base** Main text, figures referenced in text (Figures 1-4 and supplementary figures), tables (Table 1), and methods sections.
- **Missing materials affecting confidence** Supplementary data files (supplementary figures, tables, and data) were not provided. The GitHub repository was not reviewed. The full set of performance metrics across all 20 folds was not provided.

## Reviewer
- **Overall assessment** This manuscript presents a well-motivated and methodologically sound approach to predicting nucleic acid-binding proteins using a protein language model. The use of experimentally validated training data and the integration of attention-based interpretability are notable strengths. However, several technical concerns regarding the evaluation framework, the handling of negative labels, and the interpretation of attention scores need to be addressed before the claims can be fully supported.
- **Who would be interested in the results, and why** Researchers in computational biology, bioinformatics, and functional genomics, particularly those working on protein function prediction, protein-nucleic acid interactions, and interpretable machine learning. The work is also relevant to experimental biologists interested in identifying candidate nucleic acid-binding proteins for validation.
- **Major strengths** 1) Use of exclusively experimentally validated training data (ChIP-seq, eCLIP) rather than computationally inferred annotations, which reduces the risk of propagating biases. 2) Integration of protein-level classification with residue-level interpretability via VAT scores, addressing a known gap in the field. 3) Parameter-efficient fine-tuning (LoRA) that preserves the pretrained representations while enabling task-specific adaptation. 4) Systematic domain enrichment and attention-based analyses that demonstrate biological relevance.
- **Major Concerns** 
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data quality and label definition
- **Claim pointer** "Proteins without experimental evidence for DNA binding (n = 16,774) and RNA binding (n = 17,870) were designated as negative classes for the DBP and RBP models, respectively."
- **Evidence pointer** Section 2.1, Section 3.1
- **Concern** The negative class is defined as proteins lacking experimental evidence of binding, not as proteins experimentally confirmed to be non-binding. This is a critical distinction. The authors acknowledge this limitation in the Discussion, but the impact on model evaluation is not adequately addressed. The 20-fold cross-validation distributes potential hidden positives across folds, but this does not eliminate the bias. The model may be learning to distinguish "well-studied" from "poorly-studied" proteins rather than binding from non-binding. The authors report that some false positives are independently annotated as binding in UniProt, which supports this concern.
- **Why it matters** If the negative set contains a substantial number of unannotated true binders, the reported performance metrics (MCC, AUROC) are likely underestimates of the true performance on a clean dataset, but the model's ability to generalize to truly non-binding proteins is unknown. More importantly, the model's predictions on novel proteins cannot be interpreted as evidence of binding without experimental validation, which limits the practical utility of the framework.
- **Resolution test** The authors should provide an estimate of the proportion of the negative set that is likely to contain hidden positives (e.g., based on UniProt annotations or literature mining). They should also evaluate the model on a held-out set of proteins that have been experimentally confirmed as non-binding, if such a set can be constructed. Alternatively, they could perform a sensitivity analysis by removing proteins with any evidence of binding (even weak or indirect) from the negative set and re-evaluating performance.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model evaluation and benchmarking
- **Claim pointer** "The DBP model outperformed the baselines across major metrics, achieving an MCC of 0.40 and AUROC of 0.84, which exceeded the values obtained by ESM-DBP (0.343 and 0.812, respectively) and TransBind."
- **Evidence pointer** Table 1, Section 3.2
- **Concern** The benchmarking is performed on the authors' own dataset, which uses a different definition of negatives (absence of experimental evidence) than the original studies for the baseline methods. ESM-DBP and TransBind were trained on datasets with different label definitions (e.g., GO annotations, BioLiP). Comparing methods on a dataset with a different label distribution and definition is not a fair comparison. The baseline methods may perform differently on this dataset because they were optimized for a different task. Furthermore, the authors do not report whether the baseline methods were retrained or used as pre-trained models. If they were retrained, the hyperparameters may not be optimal for this dataset.
- **Why it matters** The claim of "outperforming" existing methods is central to the paper's narrative. If the comparison is not fair, the conclusion is not supported. The reader cannot determine whether the proposed model is genuinely better or simply benefits from a different data definition.
- **Resolution test** The authors should either: (1) evaluate all methods on a common, independent benchmark dataset with experimentally confirmed labels for both positive and negative classes, or (2) clearly state that the comparison is on their own dataset and acknowledge that the label definitions differ, and discuss how this might affect the comparison. They should also report whether the baseline methods were retrained and, if so, provide details on the retraining procedure and hyperparameter selection.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Interpretability and causality
- **Claim pointer** "These results demonstrate that attention-based protein language models can accurately identify nucleic acid-binding proteins directly from sequence data. Moreover, these models reveal biologically meaningful sequence determinants of binding."
- **Evidence pointer** Section 3.3, Section 3.4, Section 4
- **Concern** The authors correctly note that attention weights reflect correlation, not causation. However, the manuscript's language often implies a causal relationship (e.g., "the model relies on structural signatures," "the model assigns greater attention to regions of the domain associated with nucleic acid-binding functions"). The VAT score analysis shows that attention is concentrated on known binding domains, but this does not demonstrate that these regions are necessary or sufficient for the model's prediction. The untuned ESM-2 model also shows this pattern, suggesting that the attention patterns are a property of the pretrained model, not of the fine-tuned classifier. The claim that the model "reveals" sequence determinants of binding is therefore overstated.
- **Why it matters** Overstating the interpretability claims could mislead readers into thinking that the model can be used to discover novel binding motifs or mechanisms. The current analysis only shows that the model's attention correlates with known annotations, which is a useful sanity check but not a discovery.
- **Resolution test** The authors should temper the language throughout the manuscript to reflect that the attention analysis shows correlation with known domains, not causal evidence. They should explicitly state that the model does not "reveal" new sequence determinants but rather recapitulates known ones. They could also perform an ablation study (e.g., masking high-attention residues and measuring the drop in prediction score) to provide stronger evidence for the functional importance of these regions.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor and reporting
- **Claim pointer** "In 20-fold cross-validation, the DBP model achieved an AUROC of 0.84 with an MCC of 0.40, while the RBP model achieved an AUROC of 0.92 with an MCC of 0.46."
- **Evidence pointer** Section 3.2, Table 1
- **Concern** The authors report only mean performance metrics across 20 folds. They do not report standard deviations, confidence intervals, or the distribution of metrics across folds. This is important for assessing the stability and reliability of the model. The 20-fold cross-validation uses a 95/5 split, which means each test set contains only ~911 proteins (5% of 18,221). With a small positive class (especially for RBPs, n=351), the performance in individual folds could be highly variable. The authors also do not report the performance on the training set, which would help assess overfitting.
- **Why it matters** Without measures of variability, the reader cannot assess the robustness of the reported performance. A model with high mean performance but high variance across folds is less reliable than one with lower but more consistent performance.
- **Resolution test** The authors should report the standard deviation or 95% confidence interval for all reported metrics (MCC, AUROC, accuracy, precision, recall, F1) across the 20 folds. They should also report the range of values observed. Additionally, they should report the training set performance to assess overfitting.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Data leakage and sequence similarity
- **Claim pointer** "For genes encoding multiple protein isoforms, the longest isoform was selected as the representative sequence."
- **Evidence pointer** Section 2.1
- **Concern** The authors do not address the issue of sequence similarity between training and test sets. If highly similar proteins (e.g., isoforms of the same gene, or paralogs) are present in both training and test sets within a cross-validation fold, the model's performance may be inflated due to data leakage. The 20-fold cross-validation splits the data randomly, which does not guarantee that similar sequences are separated. The authors should perform a sequence-similarity-based split (e.g., clustering at 30-40% identity) to ensure that the test set contains proteins that are not highly similar to training proteins.
- **Why it matters** If the model is evaluated on proteins that are very similar to training proteins, the reported performance may not generalize to truly novel sequences. This is a common issue in protein function prediction and should be addressed.
- **Resolution test** The authors should perform a sequence-similarity-based cross-validation (e.g., using CD-HIT or MMseqs2 to cluster sequences at 30-40% identity and splitting by cluster) and report the performance. They should also report the maximum sequence identity between training and test sets in their current 20-fold cross-validation.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Model architecture and hyperparameter selection
- **Claim pointer** "These rank and scaling parameters were selected based on established configurations in previous protein language model studies rather than through task-specific hyperparameter optimization."
- **Evidence pointer** Section 2.3
- **Concern** The LoRA hyperparameters (rank=8, alpha=32, dropout=0.1) were taken from previous studies without task-specific optimization. While this is a common practice, it is not justified for this specific task. The performance of LoRA can be sensitive to these parameters, and the authors do not demonstrate that the chosen configuration is optimal or even near-optimal for their dataset. Similarly, the learning rate (1e-5), batch size (16), and number of epochs (5) were not optimized.
- **Why it matters** The reported performance may not reflect the true potential of the model. A more thorough hyperparameter search could yield better results, or conversely, the current configuration might be suboptimal. The lack of optimization weakens the claim that the model "achieves high performance."
- **Resolution test** The authors should either: (1) perform a systematic hyperparameter search (e.g., for LoRA rank, alpha, learning rate) and report the best configuration, or (2) provide a justification for why the chosen parameters are expected to be near-optimal for this task (e.g., based on theoretical considerations or empirical evidence from similar tasks). They should also report the sensitivity of the results to these parameters.

- **Concern ID** R1-M7
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and data availability
- **Claim pointer** "Code is available on GitHub (https://github.com/CSB-hub/DRBP)."
- **Evidence pointer** Availability and implementation section
- **Concern** The GitHub repository was not reviewed. The authors state that trained model weights are provided, but it is unclear whether the repository contains all necessary code, data, and instructions to reproduce the results. The manuscript does not provide a detailed description of the computational environment (e.g., software versions, dependencies). The data sources (hPDI, hTFtarget, ENCODE) are publicly available, but the exact versions and processing steps are not fully specified.
- **Why it matters** Reproducibility is a cornerstone of scientific research. Without access to the code and data, the results cannot be independently verified.
- **Resolution test** The authors should ensure that the GitHub repository contains: (1) all code for data preprocessing, model training, and evaluation, (2) a requirements file with exact software versions, (3) a README with detailed instructions for reproducing the results, (4) the trained model weights, and (5) a script to download and preprocess the data. The authors should also provide a DOI for the repository (e.g., via Zenodo) to ensure long-term access.

- **Minor Comments**
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Section 2.5
- **Evidence pointer** Location not provided
- **Issue** The MCC formula is presented in the text but is not rendered correctly (the equation is missing). The authors should ensure that the equation is properly formatted.
- **Required correction** Ensure the MCC equation is correctly rendered in the final manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Section 2.2
- **Evidence pointer** Location not provided
- **Issue** The authors state that "The input sequence length was set to 1024 amino acids based on constraints imposed by the ESM-2 model and sequence coverage analysis (Fig. 1, available as supplementary data at Bioinformatics Advances online)." The reference to "Fig. 1" is ambiguous, as Figure 1 in the main text shows the data collection and model training workflow. The supplementary figure should be clearly labeled.
- **Required correction** Clarify the reference to the supplementary figure (e.g., "Supplementary Fig. S1").

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Section 3.2
- **Evidence pointer** Location not provided
- **Issue** The authors state that "The DBP model identified 2412 proteins with predicted binding probabilities above 0.7, and the RBP model predicted 529 proteins with predicted binding probabilities above 0.9 as potential binding proteins." It is unclear whether these numbers are from the full dataset predictions or from the cross-validation. The context suggests they are from applying the trained models to the full dataset, but this should be explicitly stated.
- **Required correction** Clarify that these numbers are from applying the final model to the full dataset of 18,221 proteins.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Section 3.3
- **Evidence pointer** Location not provided
- **Issue** The authors state that "Comparison between binding and non-binding predicted groups showed no consistent pattern for proteins with fewer than six IPR domains; however, proteins containing six or more domains were notably more prevalent in the binding groups for both models (Fig. 3A)." This observation is interesting but not explained. Why would proteins with more domains be more likely to be predicted as binding? This could be an artifact of the model or a genuine biological signal.
- **Required correction** Provide a brief explanation or hypothesis for this observation.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Section 3.4
- **Evidence pointer** Location not provided
- **Issue** The authors state that "The untuned model displayed a similar preference for annotated DNA- or RNA-binding domains prior to optimization." This is a key observation, but the authors do not discuss its implications in detail. If the untuned model already focuses on binding domains, then the fine-tuning is only calibrating the classification head, not learning new features. This supports the claim that the model is interpretable, but it also suggests that the model is not learning anything new about binding.
- **Required correction** Expand the discussion of this finding, including its implications for the novelty of the approach.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Section 4
- **Evidence pointer** Location not provided
- **Issue** The Discussion section is well-written but somewhat repetitive. Some points (e.g., the use of experimentally validated data, the advantages of LoRA) are mentioned multiple times.
- **Required correction** Condense the Discussion to avoid redundancy.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Section 2.4
- **Evidence pointer** Location not provided
- **Issue** The authors state that "positive samples were up-sampled by each sample 12-fold for DBP prediction and 50-fold for RBP prediction to approximate the size of the negative set." The phrase "by each sample 12-fold" is awkward. It should be "positive samples were up-sampled by a factor of 12 for DBP prediction and 50 for RBP prediction."
- **Required correction** Rephrase for clarity.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Clarity and presentation
- **Affected element** Section 2.7
- **Evidence pointer** Location not provided
- **Issue** The description of the VAT score calculation and normalization is somewhat technical and could be clarified. Specifically, the authors state that "a cubic smoothing spline was applied to the model to remove the position-dependent baseline bias." It is unclear what "the model" refers to here. Is the spline applied to the VAT scores or to the model's attention weights?
- **Required correction** Clarify that the spline is applied to the VAT scores, not to the model itself.

- **Technical failings that need to be addressed before the case is established** R1-M1 (negative label definition), R1-M2 (benchmarking fairness), R1-M4 (statistical reporting), R1-M5 (sequence similarity leakage), R1-M7 (reproducibility)
- **Assessment against Nature-style criteria** 
  - **Originality:** Moderate. The application of ESM-2 with LoRA to nucleic acid-binding protein prediction is not entirely novel, as similar approaches have been reported. The main novelty lies in the exclusive use of experimentally validated data and the integration of VAT-based interpretability. However, the finding that the untuned model already focuses on binding domains reduces the novelty of the interpretability aspect.
  - **Scientific importance:** Moderate to high. Accurate prediction of nucleic acid-binding proteins is important for understanding gene regulation and disease. The use of high-quality experimental data is a significant strength. However, the limitations of the negative label definition and the lack of causal evidence for the attention analysis reduce the immediate impact.
  - **Interdisciplinary readership:** Moderate. The work is primarily of interest to computational biologists and bioinformaticians. The biological implications are discussed but not experimentally validated, which may limit its appeal to experimental biologists.
  - **Technical soundness:** Moderate. The methodology is generally sound, but several technical concerns (label definition, benchmarking, statistical reporting, data leakage) need to be addressed. The lack of hyperparameter optimization and the reliance on a single model architecture (ESM-2) are also limitations.
  - **Readability for nonspecialists:** Good. The manuscript is well-written and clearly structured. The authors explain technical concepts (e.g., LoRA, VAT) in an accessible manner. The figures are informative, although the supplementary figures were not reviewed.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising, and the use of experimentally validated data is commendable. However, the major concerns regarding the negative label definition, benchmarking fairness, and statistical rigor must be addressed before the claims can be fully supported. The authors should also provide a more nuanced discussion of the interpretability claims and the limitations of the attention analysis.

## Risk / unsupported claims
- The claim that the model "outperforms" existing methods is not fully supported due to the unfair benchmarking comparison (R1-M2).
- The claim that the model "reveals biologically meaningful sequence determinants of binding" is overstated, as the attention analysis only shows correlation with known domains, not causation (R1-M3).
- The claim that the model can be used for "proteome-wide characterization of protein–nucleic acid interactions" is not supported, as the model was trained only on human proteins and has not been validated on other species.
- The claim that the model "reduces the risk of false positives that are common in models trained on purely computational predictions" is not directly tested, as the authors do not compare the false positive rates of their model with those of other models on a common benchmark.