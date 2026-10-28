## Review setup
- **Input scope** Full manuscript text (Abstract, Introduction, Materials and Methods, Results, Validation, Comparison with Other Algorithms, Conclusion, Supplementary Information description)
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims, and clarity of the presented evidence. No assessment of code functionality or data availability beyond what is described.
- **Shared manuscript claim summary** The authors present WTKO-CNN, a two-layer convolutional neural network with an attention mechanism, to classify 600 bp ATAC-seq peak sequences as wild-type (WT) or knockout (KO) for two datasets (RelA, LSD1). They report 68-84% accuracy, use saliency maps to extract 20-bp k-mers, cluster these k-mers, and perform de novo motif discovery with MEME, validating against known TF motifs via TOMTOM and HOMER. They claim the identified motifs are biologically meaningful and that their approach outperforms other architectures (CNN, CNN+LSTM, CNN+Transformer, vanilla Transformer).
- **Visible evidence base** Main text, Tables 1, 4, 5, 6, 7, 8, 9, 10, 11, 13, Figures 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 (as referenced). Supplementary files S1-S4 are mentioned but not provided.
- **Missing materials affecting confidence** Supplementary files (S1-S4) containing peak data, HOMER enrichment results, and TOMTOM results are not provided. The manuscript text contains several incomplete sentences and placeholders (e.g., "achieving, demonstrating robust predictive performance" in Section 4.1). No hyperparameters for the CNN, LSTM, or Transformer baselines are given. No details on the attention mechanism implementation are provided. The exact number of test sequences per dataset is not stated.

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful application of CNN interpretability to ATAC-seq data, but the current form is not suitable for publication. The core claims are either unsupported by the provided evidence or are undermined by methodological ambiguities and apparent inconsistencies. The most significant issue is the lack of a clear, quantitative demonstration that the identified motifs are discriminative between WT and KO conditions beyond anecdotal examples. The comparison with other algorithms is incomplete and lacks statistical rigor. The writing contains multiple incomplete sentences and internal contradictions (e.g., the description of the model's performance and overfitting in Section 4.1). The work is of interest to a niche computational biology audience, but the scientific importance and novelty are not clearly established from the provided material.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on deep learning interpretability for genomics, specifically those interested in motif discovery from chromatin accessibility data. The methodological pipeline (CNN + saliency + clustering + MEME) could be of interest as a template for similar analyses. Researchers studying transcriptional regulation by RelA or LSD1 might find the candidate motifs of interest, but the lack of experimental validation limits this appeal.
- **Major Strengths**
    1.  The combination of saliency mapping with k-mer clustering and de novo motif discovery is a coherent and potentially powerful interpretability pipeline.
    2.  The use of two independent datasets (RelA, LSD1) provides some evidence of generalizability.
    3.  The inclusion of a comparison with other architectures (CNN, CNN+LSTM, Transformer) is a positive step, although the execution is flawed.
    4.  The authors make their code and commands available via GitHub, which is commendable for reproducibility.
- **Major Concerns**

    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Evidence quality and support for claims
    - **Claim pointer** The manuscript claims that the CNN-guided saliency approach identifies "biologically meaningful patterns" and "discriminative motifs" that distinguish WT from KO sequences.
    - **Evidence pointer** Section 4.3, Tables 5-8, Section 5, Tables 11-12, Figures 8-9
    - **Concern** The central claim of biological discovery is not supported by quantitative evidence. The manuscript lists consensus motifs and their best TOMTOM matches (e.g., FOS, JUN, ASCL1), but it does not provide any statistical measure of whether these motifs are significantly enriched or depleted in WT versus KO sequences. The HOMER validation (Section 5) is presented descriptively ("higher enrichment in KO peaks") without reporting the actual enrichment values, p-values, or effect sizes for the comparison between conditions. The claim that the CNN identifies "non-canonical motifs" is not substantiated with any specific examples or comparison to known motifs. The analysis is purely anecdotal.
    - **Why it matters** Without a quantitative comparison of motif enrichment between WT and KO, the core claim that the model reveals sequence motifs that *distinguish* the two conditions is unsubstantiated. The reader cannot assess whether the identified motifs are truly discriminative or merely common regulatory elements present in both conditions.
    - **Resolution test** The authors must provide a statistical comparison of motif enrichment (e.g., differential motif analysis with appropriate background models) between WT and KO sequences for both datasets. This should include effect sizes and confidence intervals. The HOMER results should be presented as a table with enrichment scores, p-values, and the number of target and background sequences for each motif, for both WT and KO separately.

    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Methodological rigor and reproducibility
    - **Claim pointer** The manuscript claims that the WTKO-CNN model achieves high predictive performance (68-84% accuracy) and that the model architecture is designed to prioritize interpretability.
    - **Evidence pointer** Section 3.2, Section 4.1, Table 4, Figure 5, Figure 6
    - **Concern** The description of the model and its evaluation is critically incomplete. The text in Section 4.1 contains an incomplete sentence: "achieving, demonstrating robust predictive performance across the genome." The description of the training process is contradictory: it states that "test accuracy decreases, indicating overfitting" but then Figure 6 is described as showing that "Both curves gradually increased and stabilized, with the test accuracy." The model architecture is described in text and pseudocode, but key hyperparameters (number of epochs, batch size, learning rate, optimizer settings, kernel sizes for the second layer, pooling sizes, dropout rates) are not fully specified. The attention mechanism is mentioned but its exact implementation is not described. The baseline models (CNN with 4 layers, CNN+LSTM, Transformer) are described only in general terms, with no architecture details or hyperparameters, making the comparison in Table 13 impossible to interpret or reproduce.
    - **Why it matters** The lack of architectural and training details prevents replication of the experiments, which is a fundamental requirement for a computational methods paper. The contradictory statements about overfitting and the incomplete sentence undermine confidence in the reported results. The comparison with baselines is meaningless without a full specification of those baselines.
    - **Resolution test** The authors must provide a complete and unambiguous description of the WTKO-CNN architecture, including all hyperparameters, the attention mechanism implementation, and the training procedure. The description of the results must be corrected to remove contradictions and incomplete sentences. Full architectural and training details for all baseline models must be provided, and the comparison should include multiple random seeds with reported variance (e.g., mean and standard deviation of accuracy across runs).

    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Data handling and potential for data leakage
    - **Claim pointer** The manuscript claims that the model was evaluated on held-out chromosomes 6 and 7 to ensure generalization to unseen genomic regions.
    - **Evidence pointer** Section 3.2, Section 4.1
    - **Concern** The manuscript states that the test set is chromosomes 6 and 7, and the training set is the remaining chromosomes. However, it is not clear if the balancing of the dataset (mentioned in Section 3.2) was performed *before* or *after* the train-test split. If balancing is performed on the entire dataset before splitting, it could lead to data leakage, where information from the test chromosomes influences the training set composition. Furthermore, the number of sequences in the training and test sets is not reported. The manuscript also does not specify whether the peak sequences from the two biological replicates per condition were combined or treated separately.
    - **Why it matters** Data leakage is a critical flaw that can lead to overly optimistic performance estimates. The lack of clarity on the balancing procedure and the number of sequences makes it impossible to assess the validity of the reported accuracy. The treatment of biological replicates is also important for assessing the generalizability of the model.
    - **Resolution test** The authors must clarify the exact sequence of steps in the data preparation pipeline, specifically whether balancing was performed before or after the train-test split. They must report the number of sequences in the training and test sets for each dataset. They should also clarify how biological replicates were handled.

    - **Concern ID** R1-M4
    - **Severity** Major
    - **Blocking** No
    - **Axis** Comparison with existing methods and novelty
    - **Claim pointer** The manuscript claims that the proposed WTKO-CNN approach is novel and that relatively few studies integrate saliency-driven k-mer extraction with clustering to compare WT and KO sequences.
    - **Evidence pointer** Section 2, Section 6, Table 13
    - **Concern** The introduction reviews several interpretability methods (DeepSEA, DeMo Dashboard, CAE-CNN, ExplaiNN, DeepLIFT) but does not provide a clear, quantitative comparison of the proposed method against these established tools on the same datasets. The comparison in Section 6 is limited to generic deep learning architectures (CNN, CNN+LSTM, Transformer) and does not include state-of-the-art interpretable genomic models like DeepSEA or ExplaiNN. The claim of novelty is therefore not adequately supported.
    - **Why it matters** For a methods paper, demonstrating a clear advantage over existing state-of-the-art tools is essential. Without a direct comparison to established interpretability methods, the novelty and utility of the proposed approach are not established.
    - **Resolution test** The authors should benchmark WTKO-CNN against at least one or two established interpretable deep learning models for genomics (e.g., DeepSEA, ExplaiNN) on the same datasets and report comparable metrics (accuracy, AUROC, motif discovery performance). This would provide a stronger case for the novelty and utility of the proposed method.

- **Minor Comments**

    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and completeness of writing
    - **Affected element** Section 4.1, first paragraph
    - **Evidence pointer** Section 4.1
    - **Issue** The sentence "The CNN was trained to classify WT- and KO-specific ATAC-seq peaks based on 600 bp one-hot encoded sequences. Training was performed for 100 epochs with gradient accumulation and mixed precision. Early epochs showed a steady increase in both training and test accuracy. Beyond this point, the training accuracy continued to increases, while test accuracy decreases, indicating overfitting ." contains a grammatical error ("continued to increases") and is immediately followed by a description of Figure 6 that contradicts the overfitting statement.
    - **Required correction** Rewrite this section to clearly describe the training dynamics. If overfitting occurred, state it clearly and describe how it was addressed (e.g., early stopping, regularization). If the final model was selected based on test accuracy, state that explicitly. Correct the grammatical error.

    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Clarity of figures
    - **Affected element** Figures 1, 3, 4, 7
    - **Evidence pointer** Figure captions in Sections 3.2, 3.4, 3.5, 4.2
    - **Issue** The figure captions are descriptive but do not provide enough detail for the reader to understand the specific elements of the pipeline or the data being shown. For example, Figure 7 is described as showing "sample saliency maps" but it is unclear how these maps are aggregated or what the color scale represents.
    - **Required correction** Expand the figure captions to include a clear description of all panels, the color scales, and the specific data or model outputs being visualized.

    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Consistency of terminology
    - **Affected element** Section 3.2, Section 4.1
    - **Evidence pointer** Section 3.2, Section 4.1
    - **Issue** The manuscript uses "saliency map" and "salience map" interchangeably. The term "k-mer" is used for both 20-bp sequences extracted from saliency peaks and 10-bp sequences from CNN filters, which could be confusing.
    - **Required correction** Use a single term for the saliency map. Clearly distinguish between the 20-bp "saliency k-mers" and the 10-bp "filter k-mers" throughout the text.

    - **Concern ID** R1-m4
    - **Severity** Minor
    - **Axis** Statistical reporting
    - **Affected element** Table 4, Table 13
    - **Evidence pointer** Section 4.1, Section 6
    - **Issue** The performance metrics in Tables 4 and 13 are reported as single values. No confidence intervals or standard deviations are provided, despite the acknowledged variability due to stochastic initialization.
    - **Required correction** Report the mean and standard deviation of the metrics across the multiple runs (the manuscript states the model was trained multiple times). This is essential for assessing the reliability of the reported performance.

## Risk / unsupported claims
- The claim that the identified motifs are "biologically meaningful" and "discriminative" is unsupported by quantitative differential analysis between WT and KO conditions.
- The claim that the model "outperforms" other architectures is unsupported due to the lack of detail on baseline architectures and the absence of statistical significance testing.
- The claim that the approach can find "non-canonical motifs" is not substantiated with specific examples or comparison to known motifs.
- The claim that the 600 bp window was "empirically determined using saliency map analysis" is not supported by any data or description of this analysis.
- The generalizability of the model to other cell types or conditions is claimed but not tested.
- The performance of the model on the LSD1 dataset is described as having a "smaller" test set, but the exact number of sequences is not provided, making the reliability of the 84% accuracy claim unassessable.