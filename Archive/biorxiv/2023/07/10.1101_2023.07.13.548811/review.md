## Review setup

- **Input scope** Full manuscript text including abstract, introduction, methods, results, application, limitation, and conclusion sections. No figures, tables, or supplementary materials were provided.
- **Assessment boundary** Assessment is limited to the claims and evidence presented in the supplied text. Claims referencing figures, external datasets, or prior publications are evaluated based on the textual description only.
- **Shared manuscript claim summary** The authors propose Peptriever, a bi-encoder transformer-based approach for large-scale protein-peptide binding search. The method uses two BERT-like models jointly fine-tuned with a contrastive loss to embed proteins and peptides into a shared space, enabling fast approximate nearest neighbor search over millions of proteins. The authors report a mean AUC-ROC and AUC-PR of 0.73, outperforming existing sequence- and structure-based methods including AlphaFold-Multimer, CAMP, and InterPep2 on a benchmark test set.
- **Visible evidence base** Textual description of methods, training data sources (PDB, PepBDB, Propedia, YAPP-Cd), evaluation protocol (112 positive and 560 negative interactions), and reported performance metrics (AUC-ROC 0.83, AUC-PR 0.63). Reference to Figure 1 for performance comparison. No actual data, code outputs, or statistical analyses are visible.
- **Missing materials affecting confidence** Figure 1 and all other figures are not provided. Supplementary tables, training details (hyperparameters, model sizes, training duration), tokenizer details, and the exact test set composition are not available. The equation for predicted probability is referenced but not shown. Code repository and live demonstration are mentioned but not assessable from the manuscript text alone.

## Reviewer

- **Overall assessment** The manuscript addresses a relevant problem in peptide therapeutics, namely the efficient identification of protein binding partners for a given peptide among millions of candidates. The proposed bi-encoder architecture with contrastive learning is a reasonable adaptation of established techniques from information retrieval and protein language modeling. However, the evidence presented in the text is insufficient to fully evaluate the method's performance, generalizability, and practical utility. Key details about the training procedure, evaluation protocol, and statistical significance of the reported improvements are missing. The claim of outperforming AlphaFold-Multimer is based on a single benchmark with a small test set, and the margin of improvement is marginal. The manuscript would benefit from additional validation on diverse datasets, ablation studies, and a more rigorous statistical analysis.
- **Who would be interested in the results, and why** Researchers in computational biology, specifically those working on protein-peptide interactions, peptide therapeutics, and protein language models, would find this work relevant. The promise of fast, scalable binding search could be attractive for translational researchers involved in drug discovery and vaccine design. The application of contrastive learning to protein-peptide embeddings may also interest the broader machine learning for biology community.
- **Major strengths** The problem addressed is practically important and the proposed solution is computationally efficient by design. The use of a bi-encoder architecture with approximate nearest neighbor search is a sensible approach for scaling to millions of proteins. The authors have made training data, scripts, and a live demonstration available, which supports reproducibility and usability. The integration of multiple experimental interaction databases for training is a positive aspect.
- **Major Concerns** The evaluation is limited to a single, small test set with 112 positive and 560 negative interactions, which raises questions about the robustness and generalizability of the reported performance. The comparison with AlphaFold-Multimer, CAMP, and InterPep2 is presented without statistical significance testing or confidence intervals. The reported improvement over AlphaFold-Multimer v9 is marginal (mean 0.73 vs 0.725) and may not be meaningful. The manuscript lacks ablation studies to justify design choices such as the contrastive loss, the MLM auxiliary loss, and the specific tokenizer and model architecture. The truncation of protein sequences to 300 tokens is acknowledged as a limitation, but its impact on performance for longer proteins is not quantified. The application section is brief and does not provide details on the vector database, indexing parameters, or search speed benchmarks.
- **Minor Comments** The abstract states a mean AUC-ROC and AUC-PR of 0.73, but the results section reports specific values of 0.83 and 0.63 for the proposed method. The relationship between these numbers and the mean is not clearly explained. The equation for the predicted probability is referenced but not displayed. The introduction mentions several existing methods but does not provide a systematic comparison of their limitations in the context of large-scale search. The conclusion mentions a planned version II with reverse search functionality, which is interesting but not relevant to the current evaluation. The funding statement is clear, but the author contributions and competing interests are not declared.
- **Technical failings that need to be addressed before the case is established** The lack of statistical analysis (confidence intervals, significance tests) for the performance comparison is a major technical shortcoming. The absence of ablation studies prevents the attribution of performance gains to specific architectural components. The evaluation on a single small test set is insufficient to establish generalizability. The manuscript does not provide details on the computational resources required for training and inference, which is relevant for a method claiming scalability. The exact composition of the training and test sets, including the overlap removal procedure, is not fully described.
- **Assessment against Nature-style criteria** Originality: The application of bi-encoder contrastive learning to protein-peptide binding search is a novel combination of existing techniques, but the individual components are well-established. The originality is moderate. Scientific importance: The problem of large-scale peptide binding search is important for therapeutic development, and a fast, accurate method would be valuable. However, the evidence presented does not yet demonstrate a significant advance over existing methods. Interdisciplinary readership: The work bridges machine learning and structural biology, and the results could interest both communities. The writing is accessible but assumes familiarity with protein language models and interaction prediction. Technical soundness: The proposed architecture is technically plausible, but the evaluation is not rigorous enough to establish its soundness. The lack of statistical tests and ablation studies is a concern. Readability for nonspecialists: The manuscript is generally readable, but the methods section assumes background knowledge in transformer architectures and contrastive learning. The abstract and introduction are clear, but the results section is brief and relies heavily on a single figure.
- **Recommendation posture** Currently not established from the provided evidence. The core claim of outperforming existing methods is supported by a single, small benchmark without statistical validation. The manuscript has potential, but substantial additional evidence is required, including more extensive evaluation, statistical analysis, and ablation studies.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The authors claim that Peptriever outperforms existing sequence- and structure-based methods, including AlphaFold-Multimer, CAMP, and InterPep2, based on a mean AUC-ROC and AUC-PR of 0.73.
- **Evidence pointer** Results section, Figure 1 (not provided)
- **Concern** The performance comparison is based on a single test set comprising 112 positive and 560 negative interactions. The reported differences in AUC-ROC and AUC-PR between Peptriever and AlphaFold-Multimer v9 are marginal (0.83 vs 0.81 for AUC-ROC, 0.63 vs 0.64 for AUC-PR, and mean 0.73 vs 0.725). No confidence intervals, standard deviations, or statistical significance tests are reported. The small test set size and the lack of statistical analysis make it impossible to determine whether the observed differences are meaningful or within the range of random variation.
- **Why it matters** The central claim of the manuscript is that Peptriever outperforms existing methods. Without statistical validation, this claim is not supported. A marginal improvement on a small dataset could be due to chance, and the scientific community requires robust evidence before accepting a new method as superior.
- **Resolution test** Provide confidence intervals or perform statistical significance testing (e.g., bootstrapping or DeLong test for AUC) for the performance metrics. Additionally, evaluate the method on multiple independent test sets or cross-validation folds to demonstrate consistent performance. If the improvement over AlphaFold-Multimer is not statistically significant, the claim should be revised.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The authors state that the training process comprised two stages: unsupervised pre-training and supervised fine-tuning, with details about data sources and loss functions.
- **Evidence pointer** Methods section 2.1 and 2.2
- **Concern** The manuscript lacks critical details required for reproducibility. The model architecture is described as "BERT-like" but the number of layers, hidden dimensions, attention heads, and total parameter count are not specified. The tokenizer is described as byte-pair encoding with a vocabulary size of 1024, but the training data for the tokenizer is not described. Hyperparameters for pre-training and fine-tuning (learning rate, batch size, number of epochs, optimizer, warmup steps) are not provided. The exact composition of the training dataset after merging PepBDB, Propedia, and YAPP-Cd is not described, including how duplicates were removed and how the gene-based splitting was implemented.
- **Why it matters** Reproducibility is a fundamental requirement for scientific publications. Without these details, other researchers cannot replicate the training process or verify the reported results. The availability of code and data is helpful, but the manuscript itself should contain sufficient information for independent implementation.
- **Resolution test** Provide a complete description of the model architecture, training hyperparameters, and data processing pipeline. Include the exact number of training, validation, and test samples, and describe the gene-based splitting procedure in detail. If the code repository contains this information, reference the specific files and sections.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The authors claim that Peptriever can quickly identify and rank millions of interacting proteins, and that the approach outperforms existing methods.
- **Evidence pointer** Abstract, Results section, Application section 3.1
- **Concern** The evaluation is limited to a single benchmark test set derived from a specific source (Johansson-Akhe and Wallner 2022). The manuscript does not demonstrate the method's performance on diverse datasets, different types of peptides, or across different species. The claim of scalability to millions of proteins is not supported by any benchmark or runtime analysis. The application section describes the use of a vector database but does not provide details on the database size, indexing method, or search latency.
- **Why it matters** A method for large-scale binding search must demonstrate both accuracy and scalability. The current evidence only shows performance on a small, curated test set. Without additional validation, it is unclear whether the method generalizes to real-world scenarios with diverse peptide sequences and large protein databases.
- **Resolution test** Evaluate the method on additional benchmark datasets, such as those covering different protein families or peptide types. Provide runtime and memory benchmarks for indexing and searching at the scale of millions of proteins. Compare the search speed with existing methods to substantiate the claim of efficiency.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Design justification
- **Claim pointer** The authors state that the performance improvement is "possibly due to BERT-based architecture combined with a contrastive loss function."
- **Evidence pointer** Results section
- **Concern** The manuscript does not include ablation studies to isolate the contribution of individual components. It is unclear whether the bi-encoder architecture, the contrastive loss, the MLP auxiliary loss, or the pre-training strategy each contribute to the reported performance. The claim that the improvement is "possibly due to" these factors is speculative and not supported by experimental evidence.
- **Why it matters** Understanding which components drive performance is essential for the scientific community to build on this work and for practitioners to make informed decisions about method selection. Without ablations, the design choices appear arbitrary and the method's advantages are not clearly attributed.
- **Resolution test** Perform ablation studies by removing or modifying individual components, such as training without the contrastive loss, without the MLM auxiliary loss, or with a different architecture. Report the performance of each variant on the same test set to demonstrate the contribution of each component.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, Results section
- **Issue** The abstract reports a mean AUC-ROC and AUC-PR of 0.73, while the results section reports specific values of 0.83 for AUC-ROC and 0.63 for AUC-PR for the proposed method. The relationship between these numbers is unclear. The mean of 0.73 appears to be the average of the two metrics, but this is not stated explicitly.
- **Required correction** Clarify in the abstract and results section that the mean is calculated across the two metrics (AUC-ROC and AUC-PR), or report the metrics separately and consistently throughout the manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section 2.2
- **Evidence pointer** Methods section 2.2
- **Issue** The equation for the predicted probability is referenced but not displayed in the text. The sentence states "as shown in the following equation" but the equation is missing.
- **Required correction** Include the equation in the manuscript text or refer to a supplementary file where it is displayed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results section
- **Evidence pointer** Results section
- **Issue** The sentence "It also surpassed the scores of CAMP with 0.41 and InterPep2 with 0.46" is ambiguous. It is unclear whether these values refer to AUC-PR or AUC-ROC for the respective methods.
- **Required correction** Specify which metric is being referenced for each method, or present the full comparison in a table with clear column headers.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Application section 3.1
- **Evidence pointer** Application section 3.1
- **Issue** The application section is very brief and does not provide details on the vector database used, the indexing method, or the search algorithm. The claim of searching "millions of proteins within seconds" is not supported by any benchmark data.
- **Required correction** Provide details on the vector database and indexing approach, and include runtime benchmarks to support the scalability claim.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods section 2.2
- **Evidence pointer** Methods section 2.2
- **Issue** The description of the test set states it was "utilized by Johansson-Akhe et al." but does not describe the composition of this test set, such as the number of proteins, peptides, or the source of the interactions.
- **Required correction** Provide a brief description of the test set composition or reference the original publication for details.

## Risk / unsupported claims

- The claim that Peptriever "outperforms existing sequence- and structure-based methods" is not statistically supported due to the lack of significance testing and the small test set size.
- The claim that the method can "quickly identify and rank millions of interacting proteins" is not supported by any runtime or scalability benchmark in the provided text.
- The statement that the performance improvement is "possibly due to BERT-based architecture combined with a contrastive loss function" is speculative and not supported by ablation studies.
- The claim that the training data was sourced from "experimentally verified interactions with 3D structures" is stated but not verified, and the exact composition of the training set is not described.
- The application section's claim of a "user-friendly web application" and a "live demonstration" cannot be assessed from the manuscript text alone.