## Review setup
- **Input scope** Full manuscript text including abstract, results, methods, and figure legends
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and significance of the reported findings
- **Shared manuscript claim summary** The authors propose ESM-DBP, a domain-adaptive pretraining approach that refines the general protein language model ESM2 on a curated set of 170,264 non-redundant DNA-binding protein sequences. They claim improved prediction performance across four downstream tasks (DBP, DBS, TF, DBZF prediction) compared to the original ESM2 and existing state-of-the-art methods, and demonstrate interpretability via saliency analysis and experimental validation via ChIP-seq.
- **Visible evidence base** Main text, Tables 1-3, Figures 1-7, Methods section, Supplementary figure/table references
- **Missing materials affecting confidence** Supplementary Data files 1-6, Supplementary Tables 1-2, Supplementary Figures 1-7, Source Data files, and code availability were referenced but not provided for review

## Reviewer
- **Overall assessment** The manuscript presents a conceptually straightforward yet potentially useful application of domain-adaptive pretraining to improve protein language model representations for DNA-binding protein-related tasks. The core idea is not novel in the broader NLP transfer learning literature, but its systematic application to the protein-DNA interaction domain with multiple downstream tasks and interpretability analyses is commendable. However, several technical concerns regarding dataset construction, evaluation rigor, and statistical validation need to be addressed before the claims are fully established. The ChIP-seq validation is a strength but is limited to only two proteins.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on protein function prediction, particularly those focused on DNA-binding protein identification and residue-level annotation. Researchers developing domain-specific adaptations of foundation models for biological sequences would also find the approach relevant. The interpretability analyses may interest those studying protein-DNA recognition mechanisms.
- **Major strengths**
  1. Systematic evaluation across four distinct downstream tasks with multiple metrics
  2. Inclusion of interpretability analysis (integrated gradients) linking model predictions to known DNA-binding domains
  3. Experimental validation via ChIP-seq for two predicted proteins, providing orthogonal evidence beyond computational benchmarks
  4. Clear demonstration that domain-adaptive pretraining improves over the base ESM2 model
  5. Practical contribution of releasing predictions for all human TrEMBL proteins
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Data quality and leakage
  - **Claim pointer** The authors claim that the UniDBP40 pretraining dataset is constructed by removing sequences sharing high similarity with test sequences using CD-HIT at a threshold of 0.4.
  - **Evidence pointer** Methods section "Benchmark datasets", Results section "Architecture of ESM-DBP"
  - **Concern** The description of how test set sequences were excluded from pretraining is insufficiently detailed. The authors state that sequences sharing high similarity with test sequences were removed, but the exact procedure is unclear. Specifically: (1) Was the CD-HIT clustering performed jointly on pretraining and test sequences, or was a database search approach used? (2) What was the sequence identity threshold for exclusion relative to test sequences? (3) Were all four downstream task test sets considered during this filtering? The threshold of 0.4 for CD-HIT clustering is unusually low for redundancy removal and may not adequately prevent information leakage, particularly for homologous proteins that share functional domains.
  - **Why it matters** If test sequences or their close homologs were present in the pretraining data, the reported performance improvements could be substantially inflated. This is a critical issue for the validity of the central claim that domain-adaptive pretraining improves generalization.
  - **Resolution test** Provide a detailed description of the filtering procedure, including the exact commands or parameters used. Report the number of sequences removed due to similarity with each test set. Ideally, demonstrate that results are robust when pretraining excludes all sequences with >30% identity to any test sequence.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Statistical significance and comparison fairness
  - **Claim pointer** The authors claim that ESM-DBP "outperforms the state-of-the-art methods" across four downstream tasks.
  - **Evidence pointer** Results section "Performance comparison with HMM" and "ESM-DBP outperforms SOTA methods over four prediction tasks", Figure 3
  - **Concern** The manuscript reports performance metrics without any statistical significance testing. For the comparisons with SOTA methods, it is unclear whether the performance differences are statistically significant. Additionally, for methods where training sets are inaccessible (DeepTFactor, iDRBP_ECHF), the comparison may not be fair as these methods were not retrained on the same data. The authors acknowledge this limitation but do not address its impact on the conclusions. Furthermore, the comparison with HMM features uses a single configuration without exploring whether different HMM processing approaches could yield better results.
  - **Why it matters** Without statistical significance testing, the reported improvements could be within the range of random variation, particularly for small test sets. Unfair comparisons undermine the claim of outperforming SOTA methods.
  - **Resolution test** Report confidence intervals or p-values for all key comparisons. For methods with inaccessible training sets, clearly state the limitation and consider additional comparisons using publicly available precomputed results. Perform ablation studies to ensure the comparison with HMM is fair.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Generalizability claim
  - **Claim pointer** The authors claim that "ESM-DBP can still perform well even for those sequences with only a few homologous sequences" and that it demonstrates "robust generalization capability."
  - **Evidence pointer** Results section "ESM-DBP is good at generalizability", Figure 5
  - **Concern** The analysis of generalizability is based on a single test set (UniSwiss-Tst) and uses BLAST-based homology detection against the pretraining datasets. The authors show that ESM-DBP performs better than ESM2 on low-homology proteins, but the analysis is descriptive rather than quantitative. No statistical test is provided to support the claim that the improvement on low-homology proteins is significant. Additionally, the definition of "low homology" is based on BLAST hits, which may not capture more subtle evolutionary relationships. The analysis would be strengthened by using additional measures of sequence similarity and by validating on independent datasets.
  - **Why it matters** The generalizability claim is a key selling point of the method, particularly for orphan proteins. If the evidence is not robust, the practical utility of ESM-DBP for novel protein sequences is questionable.
  - **Resolution test** Provide statistical comparisons of performance between high- and low-homology groups. Validate the generalizability findings on additional independent test sets. Consider using multiple sequence alignment-based or structure-based measures of homology in addition to BLAST.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** ChIP-seq validation scope
  - **Claim pointer** The authors state that "ChIP-seq on two predicted cases further support the validity of the proposed method."
  - **Evidence pointer** Results section "Validation of prediction by ChIP-seq", Figure 6
  - **Concern** The ChIP-seq validation is limited to only two proteins (SUPT6H and GTF2E2). While this provides some experimental support, the selection criteria for these two proteins are not clearly described. It is unclear whether these were chosen randomly, based on predicted confidence, or based on biological interest. The validation would be more convincing with a larger number of experimentally tested predictions, including negative controls. Additionally, the ChIP-seq analysis appears to be primarily descriptive (peak distributions, GO/KEGG enrichment) without clear quantitative metrics linking the predictions to experimental binding.
  - **Why it matters** The ChIP-seq experiments are presented as validation of the method's predictions. With only two examples and unclear selection criteria, the generalizability of this validation is limited.
  - **Resolution test** Clearly describe the criteria for selecting the two proteins for ChIP-seq. Provide quantitative metrics linking predicted binding to experimental enrichment. If feasible, include additional experimental validations or clearly state the pilot nature of this validation.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity of methodology
  - **Affected element** Pretraining procedure
  - **Evidence pointer** Methods section "Benchmark datasets"
  - **Issue** The description of the pretraining procedure is incomplete. The authors mention using masked language modeling but do not specify the masking strategy, learning rate schedule, number of epochs, or early stopping criteria. The statement "The loss function and optimizer are consistent with ESM2" is vague.
  - **Required correction** Provide full details of the pretraining hyperparameters, including the specific masking probability, batch size rationale, learning rate, and convergence criteria. This is essential for reproducibility.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Evaluation metrics
  - **Affected element** Table 1 and Table 2
  - **Evidence pointer** Results section "Role of domain-adaptive pretraining on performance"
  - **Issue** The manuscript reports seven metrics but does not discuss which metric is most appropriate for each task. For imbalanced datasets, accuracy can be misleading. The choice of threshold (0.5 for DBP/TF, 0.4 for DBS) is not justified.
  - **Required correction** Discuss the suitability of each metric for the respective tasks. Justify the threshold choices or perform threshold optimization. Consider reporting precision-recall curves for imbalanced tasks.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Figure quality
  - **Affected element** Figure 2d
  - **Evidence pointer** Results section "Role of domain-adaptive pretraining on performance"
  - **Issue** The t-SNE visualization in Figure 2d is described but the figure itself is not provided in the manuscript text. The claim that ESM-DBP makes "a much clearer distinction" is subjective without quantitative cluster separation metrics.
  - **Required correction** Provide the t-SNE figure and consider adding quantitative metrics such as silhouette score or adjusted Rand index to support the visual claim.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Computational cost
  - **Affected element** Methods section "Architecture of ESM-DBP"
  - **Evidence pointer** Results section "Architecture of ESM-DBP"
  - **Issue** The manuscript does not report the computational resources required for the domain-adaptive pretraining beyond the training time on four GPUs. The total GPU hours, memory usage, and comparison with the cost of training ESM2 from scratch would be informative.
  - **Required correction** Report the total computational cost of the pretraining procedure, including GPU hours and memory requirements.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Code availability
  - **Affected element** Data and code availability statement
  - **Evidence pointer** Not explicitly stated in the manuscript
  - **Issue** The manuscript mentions providing predictions at a Hugging Face repository but does not clearly state whether the code for ESM-DBP pretraining and downstream fine-tuning will be made publicly available.
  - **Required correction** Clearly state the code availability, including the repository URL and any usage restrictions.
- **Technical failings that need to be addressed before the case is established**
  1. Insufficient detail on test set leakage prevention during pretraining data construction (R1-M1)
  2. Lack of statistical significance testing for all performance comparisons (R1-M2)
  3. Incomplete description of pretraining hyperparameters for reproducibility (R1-m1)
  4. Unclear selection criteria for ChIP-seq validation targets (R1-M4)
- **Assessment against Nature-style criteria**
  - **Originality** Moderate. Domain-adaptive pretraining is well-established in NLP, and its application to protein language models is a natural extension. The specific focus on DNA-binding proteins and the multi-task evaluation provide some novelty, but the approach is not conceptually groundbreaking.
  - **Scientific importance** Moderate to high. DNA-binding protein prediction is an important problem in genomics and drug discovery. The demonstrated improvements over general protein language models could have practical utility. However, the incremental nature of the improvement and the limited experimental validation temper the significance.
  - **Interdisciplinary readership** Moderate. The work bridges machine learning and molecular biology, and the interpretability analyses may attract readers from both communities. However, the technical depth in both areas may limit accessibility for non-specialists.
  - **Technical soundness** The core methodology is sound, but several technical concerns need to be addressed, particularly regarding data leakage prevention, statistical validation, and fairness of comparisons. The lack of these elements weakens the technical rigor.
  - **Readability for nonspecialists** The manuscript is generally well-written and the figures are informative. However, some sections assume familiarity with protein language models and may be challenging for readers without computational biology background. The abstract and introduction are accessible.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript addresses a relevant problem and demonstrates a potentially useful approach. However, the concerns regarding data leakage, statistical validation, and comparison fairness must be adequately addressed before the claims can be fully accepted. The ChIP-seq validation, while limited, is a positive feature that strengthens the practical relevance.

## Risk / unsupported claims
- The claim that ESM-DBP "outperforms the state-of-the-art methods" is not fully supported due to potential unfair comparisons and lack of statistical testing
- The claim of "robust generalization capability" for low-homology proteins is based on descriptive analysis without statistical validation
- The statement that "most cases can be distinguished by the naked eye" in t-SNE visualization is subjective and not quantitatively supported
- The claim that ChIP-seq results "further support the validity of the proposed method" is based on only two proteins without clear selection criteria
- The assertion that the model "spontaneously perceives DBD-specific sequence knowledge without label guidance" is not rigorously demonstrated beyond visual inspection of clustering
- The performance improvement on the DBZF task appears modest (MCC improvement from 0.239 to 0.349) and may not be practically significant despite being reported as an improvement