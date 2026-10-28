## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) for the article by Dodero-Rojas et al., titled "Epigenetics is all you need: A transformer to decode chromatin structural compartments from the epigenome," submitted to PLoS Computational Biology.
- **Assessment boundary** Scientific soundness, technical validity, clarity, and significance of the claims as presented in the provided text. No assessment of code functionality, data availability, or reproducibility beyond what is described.
- **Shared manuscript claim summary** The authors present TECSAS, a Transformer-based deep learning model that predicts chromatin subcompartment annotations (A1, A2, B1, B2, B3) and associations with nuclear bodies (LADs, NADs, SPADs) directly from epigenomic data (histone modifications, transcription factor binding, RNA-seq). They report high accuracy (0.78 overall for GM12878 subcompartments; 0.87 and 0.93 for A and B compartments, respectively) and demonstrate transferability across cell types and to higher-resolution data (K562 at 25 kb, accuracy 0.80). They also show that including a broader epigenomic context (up to 14 loci) improves performance, and that the model can be fine-tuned to predict nuclear body associations.
- **Visible evidence base** Main text figures referenced: Fig 1 (model architecture and workflow), Fig 2 (confusion matrices, accuracy metrics, confidence probabilities), Fig 3 (comparison with PyMEGABASE, context length analysis, attention maps), Fig 4 (3D structural simulations comparing TECSAS and PYMB predictions), Fig 5 (nuclear body association predictions, validation against experimental data). Supporting figures referenced: S1–S14, S1 Table, S2 Table. Methods section describes data sources (ENCODE, 4DNucleome), preprocessing, model architecture, training details, and fine-tuning procedures.
- **Missing materials affecting confidence** The manuscript text does not include the actual figures or tables, so visual inspection of the results is not possible. Details on data preprocessing (e.g., normalization, binning) are incomplete. The exact definition of "confidence probability" and its statistical validation are not fully described. The zero-shot experiment (S9 Fig) is mentioned but not detailed. The comparison with PyMEGABASE (Fig 3A) lacks statistical significance testing. The 3D simulation results (Fig 4) are described qualitatively without quantitative metrics. The fine-tuning procedure for nuclear body prediction (Section 4.3) lacks specifics on training data splits, hyperparameters, and evaluation metrics beyond accuracy.

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful application of Transformer architectures to predict chromatin structural annotations from epigenomic data. The core idea is timely and the results, as described, suggest that the model performs well. However, several technical aspects require clarification and additional validation before the claims are fully established. The comparison with existing methods is limited, and the biological insights derived from the model (e.g., attention maps, transition regions) are presented without sufficient quantitative support. The manuscript would benefit from a more rigorous benchmarking strategy and a clearer demonstration of the model's added value over existing approaches.
- **Who would be interested in the results, and why** Researchers in computational biology, epigenomics, and 3D genome organization would be interested. The work addresses a practical need to predict chromatin structure from widely available epigenomic data, which could enable studies in cell types lacking Hi-C data. The use of Transformers may also appeal to the deep learning community interested in genomic applications.
- **Major strengths** The problem is well-motivated and relevant. The model architecture is described in sufficient detail for replication. The authors demonstrate transferability across cell types and resolutions, which is a key practical advantage. The inclusion of nuclear body association prediction extends the utility of the model beyond subcompartments. The attention map analysis provides a potential avenue for biological interpretation.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (limited benchmarking), R1-M2 (lack of statistical validation), R1-M3 (insufficient detail on fine-tuning and zero-shot experiments), R1-M4 (qualitative 3D simulation analysis).
- **Assessment against Nature-style criteria** Originality: Moderate. The application of Transformers to epigenomic prediction is novel, but the underlying concept of linking epigenetics to chromatin structure is established. Scientific importance: Moderate to high. The model could be a useful tool, but its impact depends on demonstrating clear advantages over existing methods. Interdisciplinary readership: The topic bridges genomics and machine learning, but the presentation may be too specialized for a broad audience. Technical soundness: Generally sound, but with gaps in validation and statistical rigor. Readability for nonspecialists: The abstract and introduction are accessible, but the results section assumes familiarity with both epigenomics and deep learning.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising, but the current evidence does not fully establish the model's superiority or the biological insights claimed.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Benchmarking and comparison with existing methods
- **Claim pointer** "TECSAS demonstrated an improvement in performance (Fig 3)" and "regardless of the number of experiments used TECSAS outperforms PYMB."
- **Evidence pointer** Fig 3A and 3B; Section 2.2
- **Concern** The comparison with PyMEGABASE (PYMB) is limited to a single baseline method. The authors do not compare against other deep learning approaches, such as CoRNN or SLICE, which are mentioned in the introduction. Additionally, the comparison in Fig 3A uses a simplified version of TECSAS with reduced input features, which may not be a fair comparison. The claim that TECSAS outperforms PYMB "regardless of the number of experiments" is based on a single random selection of experiments, and no statistical significance testing is reported.
- **Why it matters** To establish TECSAS as a superior method, it must be benchmarked against a broader set of existing tools under consistent conditions. Without statistical tests, the observed differences could be due to chance, especially given the variability in model training.
- **Resolution test** Provide a comprehensive benchmark comparing TECSAS against CoRNN, SLICE, and PYMB using identical training and test sets. Report mean and standard deviation of accuracy across multiple runs, and perform statistical tests (e.g., paired t-test or Wilcoxon signed-rank test) to assess significance.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical validation of results
- **Claim pointer** "The model achieved an overall accuracy of 0.78" and "accuracies of 0.87 and 0.93 for A and B compartments, respectively."
- **Evidence pointer** Fig 2A and 2B; Section 2.1
- **Concern** The reported accuracies are presented as single point estimates without confidence intervals or measures of variability. It is unclear how many independent training runs were performed, and whether the results are stable across different random seeds or data splits. The comparison with the "experimental replicate accuracy limit" (S5 Fig) is mentioned but not quantified in the text.
- **Why it matters** Deep learning models can exhibit significant variability depending on initialization and data partitioning. Without measures of uncertainty, the reported accuracies cannot be properly interpreted or compared.
- **Resolution test** Report the mean and standard deviation of accuracy across at least 5 independent training runs with different random seeds. Provide confidence intervals for the key results. Additionally, quantify the experimental replicate accuracy and show that TECSAS's performance is statistically indistinguishable from this limit.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Clarity and completeness of fine-tuning and zero-shot experiments
- **Claim pointer** "By fine-tuning the final layer of the model, we successfully predicted the association of genomic loci with specific nuclear bodies" and "we performed a zero-shot experiment where the complete model... was applied to predict A/B compartments in the K562 cell line."
- **Evidence pointer** Section 2.3; Fig 5; S9 Fig
- **Concern** The fine-tuning procedure is described only briefly in Section 4.3, with no details on the training data, hyperparameters, or evaluation metrics beyond accuracy. The zero-shot experiment is mentioned in the text but not described in the methods, and the results are only shown in a supplementary figure. It is unclear how the model was adapted for binary classification (e.g., LAD vs. non-LAD) and whether the same architecture was used.
- **Why it matters** The claims of transferability and versatility depend on the reproducibility of these experiments. Without sufficient detail, other researchers cannot replicate or build upon these results.
- **Resolution test** Provide a detailed description of the fine-tuning procedure, including the number of training epochs, learning rate, and data splits. Describe the zero-shot experiment in the methods, including how the model output was thresholded to obtain binary predictions. Report performance metrics (e.g., F1 score, AUC) in addition to accuracy.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretation of 3D structural simulations
- **Claim pointer** "The radial positioning of this segment is significantly different from their respective 3D ensemble of structures" and "local motifs are sensitive to their predicted annotations."
- **Evidence pointer** Fig 4; Section 2.2
- **Concern** The 3D structural simulations are described qualitatively, with no quantitative metrics to support the claim of "significant" differences. It is unclear how the simulations were performed, how many structures were generated, and what statistical tests were used to compare the radial positioning.
- **Why it matters** The biological relevance of the model's predictions is partly supported by these simulations. Without quantitative analysis, the claim that TECSAS predictions lead to different 3D structures is not substantiated.
- **Resolution test** Provide quantitative measures of radial positioning (e.g., mean and standard deviation) for the region of interest, and perform a statistical test (e.g., Mann-Whitney U test) to compare the distributions. Describe the simulation parameters and the number of structures generated.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of figures
- **Affected element** Fig 2C
- **Evidence pointer** Section 2.1
- **Issue** The description of confidence probabilities is vague. It is unclear how the confidence is calculated and what the error bars represent.
- **Required correction** Clarify the definition of confidence probability and describe the error bars in the figure legend.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Data preprocessing details
- **Affected element** Section 4.1.2
- **Evidence pointer** Methods
- **Issue** The preprocessing steps are described only briefly. It is unclear how signal intensities were normalized and how the 14-locus window was chosen.
- **Required correction** Provide a more detailed description of the preprocessing pipeline, including normalization methods and the rationale for the window size.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Hyperparameter selection
- **Affected element** Section 4.2.1
- **Evidence pointer** Methods
- **Issue** The authors mention Bayesian optimization was used to validate hyperparameters, but the results are only shown in a supplementary figure. It is unclear how the final hyperparameters were selected.
- **Required correction** Briefly describe the Bayesian optimization procedure and report the range of hyperparameters explored.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion of limitations
- **Affected element** Section 3
- **Evidence pointer** Discussion
- **Issue** The discussion does not address potential limitations of the model, such as the reliance on the quality of epigenomic data or the generalizability to other species.
- **Required correction** Add a paragraph discussing limitations and potential sources of bias.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Code availability
- **Affected element** Section 4.2.1
- **Evidence pointer** Methods
- **Issue** The code repository is mentioned, but it is unclear whether the training data and preprocessing scripts are also available.
- **Required correction** Clarify what is included in the repository and provide instructions for accessing the data.

## Risk / unsupported claims
- The claim that TECSAS "reveals the influence of long-range epigenomic context on chromatin organization" is supported by the context length analysis (Fig 3C), but the biological interpretation of this finding is not fully developed.
- The claim that "the model’s ability to predict additional structural features... by simply fine-tuning the final layer" is demonstrated, but the generalizability of this approach to other cell types and conditions is not tested.
- The statement that "TECSAS is close to reach the experimental replicate accuracy limit" is based on a comparison with S5 Fig, but the quantitative value of this limit is not provided in the text.
- The attention map analysis (Fig 3D and 3E) is presented as evidence of the model's interpretability, but no quantitative assessment of the attention patterns is provided.
- The zero-shot experiment (S9 Fig) is mentioned as evidence of transferability, but the results are not described in the main text, and the performance is not compared to other methods.