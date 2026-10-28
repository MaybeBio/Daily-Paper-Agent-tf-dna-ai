## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract
- **Shared manuscript claim summary** The authors propose a transformer-based method, named Transformer DeepLncLoc, to predict mRNA abundance (gene expression levels) from promoter sequences and post-transcriptional information. The method uses a word2vec-based embedding (derived from DeepLncLoc) to avoid sparse one-hot matrices, and integrates mRNA stability and transcription factor data. The reported R² is 0.76 versus 0.74 for Xpresso.
- **Visible evidence base** Abstract text only; no figures, tables, or supplementary materials provided
- **Missing materials affecting confidence** Full manuscript, methodological details, dataset descriptions, hyperparameters, training and validation splits, baseline implementations, statistical significance tests, and any figures or tables

## Reviewer
- **Overall assessment** The abstract presents a plausible incremental improvement over existing gene expression prediction methods, with a modest gain in R² (0.02) over Xpresso. However, the evidence provided is insufficient to evaluate the robustness, generalizability, or methodological soundness of the proposed approach. Several claims, particularly regarding the role of transcription factors and the suitability of multi-headed attention, are not substantiated by the abstract alone.
- **Who would be interested in the results, and why** Researchers in computational biology, genomics, and machine learning applied to gene regulation would be interested. The work addresses a practical problem in predicting gene expression from sequence and regulatory information, which has potential clinical applications. The use of transformer architectures and word2vec embeddings may appeal to those exploring alternatives to one-hot encoding in genomic sequence modeling.
- **Major strengths** The abstract identifies a clear limitation of existing methods (sparse one-hot encoding) and proposes a specific solution (word2vec-based embedding). The integration of post-transcriptional information, including mRNA stability and transcription factors, is a relevant and potentially valuable addition. The reported improvement over Xpresso, though small, is a concrete comparative result.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide sufficient detail on data sources, preprocessing, model architecture, training procedure, or evaluation protocol. The reported R² improvement is not accompanied by any measure of variance or statistical significance. The claim that transcription factor integration leads to "impressive gains" is not quantified.
- **Assessment against Nature-style criteria**  
  - Originality: Moderate. The combination of word2vec embedding and transformer architecture for gene expression prediction is somewhat novel, but the core idea of using transformers for this task is not new.  
  - Scientific importance: Moderate. Gene expression prediction is a relevant problem, but the reported improvement is marginal and the abstract does not demonstrate broad applicability.  
  - Interdisciplinary readership: Limited. The abstract is written for a specialized computational biology audience and does not frame the work for a broader scientific readership.  
  - Technical soundness: Not assessable from the abstract. Key methodological details are missing.  
  - Readability for nonspecialists: Poor. Terms such as "DeepLncLoc," "word2vec," and "Multi-Headed Attention" are used without sufficient context for a general scientific audience.
- **Recommendation posture** Currently not established from the provided evidence. The abstract suggests a potentially useful method, but the lack of methodological detail and statistical validation prevents a supportive recommendation.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** The method "avoids the sparse matrices problem" by using word2vec-based embedding.  
- **Evidence pointer** Abstract, Methods section  
- **Concern** The abstract claims that word2vec-based embedding avoids sparse matrices, but no details are provided on how the embedding is constructed, what the embedding dimension is, or how the resulting dense representation is used in the transformer. The claim is plausible but unverifiable without methodological specifics.  
- **Why it matters** The core novelty of the method rests on this embedding strategy. If the embedding is not properly designed or evaluated, the advantage over one-hot encoding is not established.  
- **Resolution test** Provide a detailed description of the embedding procedure, including training data, vector size, and a comparison of input matrix sparsity before and after embedding.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Statistical validity  
- **Claim pointer** "Transformer DeepLncLoc reached 0.76 of R² compared to 0.74 of Xpresso."  
- **Evidence pointer** Abstract, Results section  
- **Concern** The reported R² values are presented as point estimates without any indication of variance, number of test samples, or statistical significance testing. A difference of 0.02 in R² may not be meaningful, especially if the test set is small or the models are evaluated on different splits.  
- **Why it matters** The main comparative claim of the paper depends on this difference. Without statistical validation, the improvement cannot be considered robust.  
- **Resolution test** Report confidence intervals or standard errors for R², and perform a paired statistical test (e.g., bootstrap or permutation test) comparing the two models on the same test set.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Reproducibility  
- **Claim pointer** The method integrates "post-transcriptional information related to mRNA stability and transcription factors."  
- **Evidence pointer** Abstract, Methods section  
- **Concern** The abstract does not specify which data sources are used for mRNA stability and transcription factor information, how these are encoded, or how they are combined with promoter sequence data. Without this information, the method cannot be reproduced or compared fairly with existing approaches.  
- **Why it matters** The integration of post-transcriptional information is a key claimed contribution. If the data sources or encoding are not described, the contribution is not assessable.  
- **Resolution test** Provide a clear description of the data sources, preprocessing steps, and the exact manner in which these features are incorporated into the model.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Generalizability  
- **Claim pointer** "The Multi-Headed Attention mechanisms which characterizes the transformer methodology is suitable for modeling the interactions between DNA's locations, overcoming the recurrent models."  
- **Evidence pointer** Abstract, Conclusion section  
- **Concern** The abstract claims that multi-headed attention is suitable for modeling DNA interactions and overcomes recurrent models, but no comparison with recurrent architectures is presented in the abstract. The claim is speculative and not supported by the reported results.  
- **Why it matters** This claim is presented as a conclusion, but it is not backed by comparative experiments. Without such evidence, the statement is not justified.  
- **Resolution test** Include a comparison with a recurrent baseline (e.g., LSTM or GRU) on the same dataset and report the corresponding performance metrics.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Title and method name  
- **Evidence pointer** Abstract, title  
- **Issue** The method is named "Transformer DeepLncLoc," which may cause confusion because DeepLncLoc is an existing method for subcellular localization prediction, not for gene expression. The naming suggests a direct adaptation that is not explained.  
- **Required correction** Clarify the relationship between the proposed method and the original DeepLncLoc, or rename the method to avoid ambiguity.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Dataset description  
- **Evidence pointer** Abstract, Methods section  
- **Issue** The abstract does not mention which organism, cell type, or number of genes are used for training and evaluation. This limits the reader's ability to assess the scope of the study.  
- **Required correction** Specify the dataset characteristics, including organism, number of samples, and any filtering criteria.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Abstract language  
- **Evidence pointer** Abstract, Background section  
- **Issue** The phrase "impressively sparse matrices" is informal and not quantified. The abstract would benefit from a more precise description of the sparsity issue.  
- **Required correction** Replace subjective language with a quantitative statement, such as the percentage of non-zero entries in one-hot encoded matrices.

## Risk / unsupported claims
- The claim that word2vec-based embedding "avoids the sparse matrices problem" is unsupported without details on the embedding and input representation.
- The claim that transcription factor integration leads to "impressive gains in predictive power" is unsupported because no quantitative comparison with and without this feature is provided.
- The claim that multi-headed attention "overcomes the recurrent models" is unsupported as no recurrent baseline is described or compared.
- The reported R² improvement over Xpresso is not statistically validated and may not be robust.