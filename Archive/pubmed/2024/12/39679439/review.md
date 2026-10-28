## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, funding, author contributions, data availability)
- **Assessment boundary** Scientific and technical evaluation of the DeepTGI framework as presented in the provided manuscript text. No supplementary files, figures, or tables were available for inspection.
- **Shared manuscript claim summary** The authors present DeepTGI, a deep learning framework that integrates auto-encoders, 2DCNN-1DCNN, Siamese networks, and multi-head attention to infer transcription factor-gene interactions (TGIs) from bulk and single-cell transcriptomic data, claiming superior performance over existing methods across multiple datasets and species.
- **Visible evidence base** Main text only. Tables 1-3 and Figures 1-5 are referenced but not provided. Supplementary Tables S1-S5 and Figures S1-S4 are referenced but not provided.
- **Missing materials affecting confidence** All figures and tables, all supplementary materials, the specific PCC formula (equation not rendered), the multi-head attention equation (not rendered), dataset preprocessing details, hyperparameter configurations, and full benchmark comparison results.

## Reviewer
- **Overall assessment** The manuscript describes a technically plausible deep learning architecture for TGI inference, combining several established components (auto-encoders, CNNs, Siamese networks, attention mechanisms) in a novel configuration. The core idea of fusing multiple feature extraction pathways with attention-based weighting is reasonable and potentially valuable. However, the current manuscript provides insufficient evidence to substantiate the central claims of superior performance. The absence of all figures, tables, and supplementary materials makes it impossible to evaluate the quantitative results, the statistical analyses, or the biological validations. The methods section lacks critical implementation details that would be necessary for reproducibility. The writing contains several unclear passages and potential technical inaccuracies that need clarification. The claim of novelty is weakened by the lack of a clear comparison to the most recent state-of-the-art methods beyond those mentioned.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on gene regulatory network inference, particularly those interested in applying deep learning to single-cell transcriptomic data. Researchers developing supervised methods for TF-target prediction would find the architectural design of interest. Biologists studying stem cell pluripotency and differentiation may find the predicted GRNs for mESCs, miPSCs, and related systems useful as hypothesis-generating resources.

- **Major strengths**
  1. The architectural design is thoughtful, combining multiple complementary feature extraction strategies (auto-encoder for representation learning, CNNs for spatial features, Siamese networks for similarity learning) with attention mechanisms for feature weighting.
  2. The use of PCC-based similarity matrices to reduce sparsity in single-cell data is a reasonable preprocessing strategy.
  3. The evaluation across multiple datasets from different species and cell lineages is a commendable approach to demonstrating generalizability.
  4. The inclusion of ablation studies (Table 2) to assess component contributions is good practice.
  5. The application to construct biologically interpretable GRNs with functional enrichment analysis adds practical value.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims DeepTGI "exhibits its superiority to identify more potential TGIs and to reconstruct the GRNs" and achieves "the highest levels of all six metrices with significant differences" compared to other methods.
- **Evidence pointer** Tables 1-3, Figures 2-4, Supplementary Tables S1-S5, Supplementary Figures S1-S4 (none provided)
- **Concern** All quantitative results supporting the central performance claims are contained in tables and figures that were not provided for review. Without access to the actual performance metrics, statistical test results, and comparative analyses, the core claims of superiority cannot be verified. The text alone is insufficient to establish that DeepTGI outperforms existing methods.
- **Why it matters** The primary contribution of this manuscript is the claimed improvement in prediction accuracy over existing approaches. Without the underlying data, the scientific case is not established.
- **Resolution test** Provide all tables and figures with full numerical results, including confidence intervals, statistical test values, and effect sizes. The performance comparisons must be presented in a format that allows independent verification.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The methods section describes the DeepTGI architecture and training procedure.
- **Evidence pointer** Data collection, DeepTGI overview, Feature representation, Feature extraction, Feature fusion, Multihead attention mechanism, Training and validation of models (location not provided)
- **Concern** Critical implementation details are missing. The specific PCC formula and the multi-head attention equation are not rendered in the text. The architecture does not specify layer sizes, number of attention heads, embedding dimensions, or the structure of the transformer encoder. The training procedure lacks details on batch size, number of epochs, learning rate scheduling, early stopping criteria, and regularization strategies. The data preprocessing for each dataset is not described beyond a brief mention of normalization for one dataset. The construction of positive and negative samples is described but the ratio and selection criteria beyond "balanced" are unclear.
- **Why it matters** Reproducibility is a fundamental requirement for computational methods. Without complete architectural and training specifications, other researchers cannot implement or validate DeepTGI.
- **Resolution test** Provide complete architectural specifications, all hyperparameters, training details, and data preprocessing steps. Ensure all equations are properly rendered and defined.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological rigor
- **Claim pointer** The manuscript states "the negative samples, the regulatory relationship is not in the standard network and gives label '0'" and that "all the datasets are constructed as balanced."
- **Evidence pointer** Training and validation of models (location not provided)
- **Concern** The construction of negative samples is a critical methodological choice in supervised TGI prediction. Simply treating all TF-gene pairs not present in the gold standard as negatives is problematic because the gold standard is incomplete, and many "negative" pairs may actually be true interactions that have not been experimentally verified. The manuscript does not address this issue or describe any filtering criteria (e.g., removing pairs with conflicting evidence, using only high-confidence negatives). The claim that datasets are "balanced" is stated without describing how this balance was achieved.
- **Why it matters** The quality and construction of training labels directly determine the validity of the supervised learning approach. Biased or noisy negative samples can lead to inflated performance metrics and biologically misleading predictions.
- **Resolution test** Describe the negative sample selection strategy in detail, including any filtering steps, and discuss how potential false negatives in the gold standard are handled. Provide justification for the balanced dataset construction.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparative evaluation
- **Claim pointer** The manuscript compares DeepTGI with GENIE3, ARACNE, WGCNA, PPCOR, PIDC, SCENIC, and DGRNS, claiming DeepTGI achieves the best performance.
- **Evidence pointer** Evaluating performance of DeepTGI by using bulk/single-cell transcriptomics data, Performance in different biological systems (location not provided)
- **Concern** The comparison methodology is not fully described. It is unclear whether all methods were evaluated under identical conditions, with the same train/test splits, the same hyperparameter tuning procedures, and the same evaluation metrics. The manuscript mentions that DGRNS is a supervised method but does not clarify whether the unsupervised methods were used with their default parameters or were optimized for each dataset. The choice of comparison methods may also be limited, as several recent deep learning-based TGI inference methods are not included.
- **Why it matters** Fair and comprehensive benchmarking is essential to support claims of superiority. Inconsistent evaluation protocols or incomplete method coverage can undermine the validity of comparative conclusions.
- **Resolution test** Describe the full benchmarking protocol, including hyperparameter optimization for all methods, statistical significance testing procedures, and justify the selection of comparison methods. Consider including additional recent deep learning-based approaches.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Biological validation
- **Claim pointer** The manuscript claims DeepTGI can "recover known regulations" and that predicted GRNs are associated with relevant biological processes and pathways.
- **Evidence pointer** Application of DeepTGI to construct gene regulatory networks (location not provided)
- **Concern** The biological validation appears limited to overlap with existing gold standards and functional enrichment analysis. The manuscript does not describe any experimental validation of novel predictions, comparison with independent ChIP-seq datasets not used in training, or assessment of cell-type specificity of the predicted interactions. The enrichment analysis is mentioned but the specific results are not shown.
- **Why it matters** For a method intended to discover novel biological interactions, demonstrating biological relevance beyond recovery of known interactions is crucial. Without independent validation, the practical utility of the predictions remains uncertain.
- **Resolution test** Provide details of the enrichment analysis results, include validation against independent experimental datasets, and discuss the biological significance of novel predictions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract (location not provided)
- **Issue** The abstract states DeepTGI "could transform multihead attention modules to define representative features" which is unclear. The phrase "transform" is ambiguous in this context.
- **Required correction** Rephrase to clearly describe the role of multi-head attention in the architecture, e.g., "uses multi-head attention modules to learn representative features."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical accuracy
- **Affected element** Introduction
- **Evidence pointer** Introduction (location not provided)
- **Issue** The description of existing methods states "these correlation-based methods cannot distinguish the direction of regulatory relationships because of the symmetry of the correlation information." This is an oversimplification. Some correlation-based methods do attempt to address directionality, and the statement does not acknowledge the diversity of approaches in this category.
- **Required correction** Provide a more nuanced description of the limitations of correlation-based methods, acknowledging that some approaches attempt to infer directionality.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Statistical analysis
- **Evidence pointer** Statistical analysis (location not provided)
- **Issue** The statistical analysis section mentions ANOVA and t-tests but does not specify which comparisons were made with which test, how multiple testing was handled, or whether assumptions for these tests were verified.
- **Required correction** Specify the statistical tests used for each comparison, describe multiple testing correction procedures, and justify the choice of tests.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Code and data availability
- **Evidence pointer** Code and data availability (location not provided)
- **Issue** The data availability statement indicates that data will be shared "following a review of the request's purpose and scope," which is restrictive and may not meet community standards for reproducibility.
- **Required correction** Provide a more permissive data sharing statement, ideally with data deposited in a public repository.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Feature representation
- **Evidence pointer** Feature representation (location not provided)
- **Issue** The term "sell-attention" appears in the Multihead attention mechanism section, which is a typographical error for "self-attention."
- **Required correction** Correct the typo.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results
- **Evidence pointer** Evaluating performance of DeepTGI by using bulk/single-cell transcriptomics data (location not provided)
- **Issue** The results section describes performance metrics but does not provide concrete numerical values in the text. Statements like "the highest levels of all six metrices" are made without reporting the actual values.
- **Required correction** Include key numerical results in the text to support the qualitative descriptions.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Computational analysis
- **Affected element** Training and validation of models
- **Evidence pointer** Training and validation of models (location not provided)
- **Issue** The manuscript reports a total of 124,840,395 floating point operations and 108,284,328 parameters but does not provide context for these numbers, such as comparison to other models or implications for practical usability.
- **Required correction** Discuss the computational requirements in the context of practical applications and compare with other methods.

- **Concern ID** R1-m8
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion (location not provided)
- **Issue** The statement "DeepTGI performs better than DGRNS in predicting TGIs" is presented as a conclusion but the reasons for this improvement are only vaguely attributed to "optimization of its overall architecture design."
- **Required correction** Provide a more specific analysis of which architectural components contribute to the performance improvement over DGRNS.

## Risk / unsupported claims
- The claim that DeepTGI achieves "the highest levels of all six metrices with significant differences" is unsupported without access to the actual results in Tables 1-3 and Figures 2-4.
- The claim that DeepTGI "could provide broader perspectives for discovery of more biological meaningful TGIs" is not substantiated without the biological validation results in the supplementary materials.
- The statement that DeepTGI "exhibits its superiority" over other methods cannot be evaluated without the full comparative benchmarking data.
- The claim that predicted GRNs are associated with specific biological processes and pathways (e.g., Wnt, MAPK, Bmp) is unverifiable without the enrichment analysis results.
- The assertion that DeepTGI "recovers known regulations" is not quantifiable without the specific overlap statistics.
- The claim that "DeepTGI shows its power for prediction of TGIs and reconstruction of GRNs" is a general statement that requires the missing quantitative evidence to be assessed.
- The statement that "DeepTGI holds higher sensitivity than other methods" is unsupported without the sensitivity values.
- The claim that the model "can be applied to predict TGIs and infer GRNs" in different biological systems is not fully verifiable without the results in Figure 4 and Supplementary Tables S4-S5.
- The statement that "many predictions that are not confirmed by the biological experimental means yet" is acknowledged, but the proportion of novel versus confirmed predictions is not quantified.
- The claim that the multi-head attention mechanism "further optimizes the feature fusion" is a design assertion that requires ablation results to support.