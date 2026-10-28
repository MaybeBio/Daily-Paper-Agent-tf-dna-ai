## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Technical soundness, methodological novelty, experimental validation, and claims as supported by the provided evidence
- **Shared manuscript claim summary** The authors propose IAGRN, an interleaved-attention graph neural network for gene regulatory network inference from scRNA-seq data. The method combines topology-constrained local attention with distance-aware global attention and graph Laplacian positional encoding. The authors claim consistent improvements over seven baseline methods across seven BEELINE benchmark datasets, particularly under sparse conditions.
- **Visible evidence base** Full text including abstract, introduction, results (datasets, experimental setup, performance metrics, ablation study, parameter analysis, computational efficiency, case study), discussion, materials and methods, and conclusions. Figures and tables are referenced but not fully visible.
- **Missing materials affecting confidence** Actual figures and tables (numerical results not fully inspectable), code availability, hyperparameter details beyond those mentioned, statistical significance testing details, and comparison with additional recent state-of-the-art methods.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational biology, namely GRN inference from sparse scRNA-seq data. The proposed architecture, which interleaves topology-constrained local attention with global self-attention augmented by graph Laplacian positional encoding, is a reasonable and potentially useful contribution. However, the evidence presented is insufficient to fully establish the claimed advantages. Several technical details require clarification, and the experimental validation would benefit from additional rigor, including statistical significance testing and analysis of failure modes. The case study is promising but limited in scope. Overall, the work is of interest to the computational biology community, but the current manuscript does not fully substantiate its claims.

- **Who would be interested in the results, and why** Researchers in computational biology and bioinformatics working on gene regulatory network inference, single-cell transcriptomics analysis, and graph neural network applications. The method may also interest those developing attention-based architectures for biological graph data. The case study on TFAP2A and JUND provides some biological context that may appeal to experimental biologists studying transcriptional regulation, though this aspect is preliminary.

- **Major strengths** The problem is well-motivated and relevant. The proposed architecture is clearly described and builds on established components (attention mechanisms, positional encoding) in a sensible way. The evaluation across multiple benchmark datasets and baseline methods is commendable. The ablation study is a good practice that helps isolate the contribution of individual components. The authors also address computational efficiency, which is often overlooked.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** "IAGRN consistently improves GRN reconstruction under highly sparse conditions and achieves competitive performance compared with existing approaches" (Abstract) and "IAGRN achieves the highest or joint-highest performance on 39 of the 42 evaluation settings" (Section 2.4)
- **Evidence pointer** Section 2.4, Figures 2 and 3 (not fully visible)
- **Concern** The claim of consistent improvement is based on aggregate counts of "highest or joint-highest" performance. However, no statistical significance testing is reported. It is unclear whether the observed differences between IAGRN and the second-best methods are statistically meaningful, especially given that only mean values over 20 runs are reported. The magnitude of improvement (e.g., 4.5% average relative AUROC improvement) may be modest, and without confidence intervals or significance tests, the robustness of this claim is not established.
- **Why it matters** In benchmark comparisons, small performance differences can arise from stochasticity or minor implementation details. Without statistical rigor, readers cannot assess whether the proposed method genuinely outperforms baselines or whether the differences are within noise. This is critical for establishing the practical value of the method.
- **Resolution test** Provide confidence intervals or standard deviations for all reported metrics, and perform pairwise statistical significance tests (e.g., Wilcoxon signed-rank test) between IAGRN and each baseline across the 20 runs. Report the number of settings where IAGRN is significantly better, and discuss cases where it is not.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "The interleaved attention encoder is composed of topology-masked attention and global self-attention" and "the default configuration is topology-masked attention→global self-attention→topology-masked attention" (Section 4.3)
- **Evidence pointer** Section 4.3, Figure 8 (not fully visible)
- **Concern** The manuscript does not provide sufficient detail on how the interleaved architecture is implemented. Specifically, it is unclear whether the topology-masked attention and global self-attention operate on the same node representations sequentially, whether residual connections are applied across the interleaved blocks, and how the attention bias matrices are computed and normalized. The distinction between the "hard mask" in topology-masked attention and the "soft bias" in global self-attention is described, but the exact formulation of the soft bias (e.g., how shortest-path distances are converted to bias values) is not fully specified. Additionally, the authors state that the same structural bias matrix is shared across heads within a layer, but it is unclear whether this sharing is across the two attention types or only within each type.
- **Why it matters** Reproducibility is a core requirement for computational methods. Without precise implementation details, other researchers cannot reimplement or build upon the proposed architecture. The novelty claim rests on the specific interleaving design, so the design must be fully specified.
- **Resolution test** Provide a detailed algorithmic description or pseudocode of the interleaved encoder, including the exact computation of attention bias matrices, the ordering of operations, and how residual connections and layer normalization are applied across the interleaved blocks. Clarify whether the same bias matrix is used for both attention types or whether they are computed separately.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Experimental validation
- **Claim pointer** "IAGRN mitigates this dimensionality curse through its adaptive attention modules, which effectively filter out background noise to focus on informative regulatory signals" (Section 2.4)
- **Evidence pointer** Section 2.4, Figure 2 (not fully visible)
- **Concern** The claim that IAGRN "mitigates the dimensionality curse" is based on a single comparison on the mDC dataset where DeepSEM suffers a 5.0% AUROC drop when moving from TFs+500 to TFs+1000. It is unclear whether this pattern is consistent across other datasets and baselines. The authors do not provide a systematic analysis of how performance changes with feature scale across all methods and datasets.
- **Why it matters** The scalability claim is presented as a key advantage of the method, but the evidence is anecdotal. A more systematic analysis would strengthen the claim and help readers understand the conditions under which IAGRN is most beneficial.
- **Resolution test** Provide a systematic comparison of performance changes between TFs+500 and TFs+1000 settings for all methods across all datasets. Report the average performance drop or gain for each method, and discuss whether IAGRN consistently shows smaller degradation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "The eigenvectors of the graph Laplacian matrix are adopted as positional encoding" and "we select the eigenvectors corresponding to the K smallest non-trivial eigenvalues" (Section 4.1)
- **Evidence pointer** Section 4.1, Equation 5
- **Concern** The choice of K (the number of eigenvectors used for positional encoding) is not discussed. It is unclear how K is determined and whether the results are sensitive to this hyperparameter. Additionally, the manuscript does not specify whether the Laplacian is computed on the training graph only or on the full graph, and how the positional encoding is normalized or scaled before concatenation with expression features.
- **Why it matters** Positional encoding is a critical component of the proposed method. If the results are sensitive to K, the authors should provide guidance on how to select it. Without this information, the method is not fully reproducible and the robustness of the approach is unclear.
- **Resolution test** Provide a sensitivity analysis for K, or state the value used and justify the choice. Clarify how the Laplacian is computed and how the positional encoding is normalized.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Experimental validation
- **Claim pointer** "The validation confirmed 16 of the 20 predicted targets for TFAP2A, while all 20 targets for JUND were fully supported by experimental evidence" (Section 2.8)
- **Evidence pointer** Section 2.8, Table 4, Figure 7 (not fully visible)
- **Concern** The case study is presented as evidence of biological utility, but the selection of TFAP2A and JUND is not justified. It is unclear whether these TFs were chosen because they are well-studied (which would bias the validation toward positive results) or based on some other criterion. Additionally, the validation against hTFtarget is limited to a single database, and the completeness of this database for the specific cell type (hESC) is not discussed.
- **Why it matters** A case study that is not representative or is biased toward well-characterized TFs does not provide strong evidence of the method's general utility. The authors should clarify the selection criteria and discuss potential limitations of the validation approach.
- **Resolution test** Justify the selection of TFAP2A and JUND, or provide a more systematic evaluation across multiple TFs. Discuss the coverage and potential biases of the hTFtarget database for hESC.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, Equation 1
- **Evidence pointer** Section 2.2
- **Issue** The equation for the positive-to-negative ratio in the test set is presented without derivation or explanation. It is unclear how this ratio is used in practice and whether it applies to all datasets uniformly.
- **Required correction** Provide a brief explanation of how this ratio is derived and used, and clarify whether it is applied consistently across all datasets and reference networks.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 4.4, Equations 21-24
- **Evidence pointer** Section 4.4
- **Issue** The activation function σ(·) is not specified for the MLP branches. It is also unclear whether dropout is applied to the hidden layers and at what rate.
- **Required correction** Specify the activation function and dropout configuration for the MLP branches.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.7, Table 3
- **Evidence pointer** Section 2.7
- **Issue** The runtime comparison includes only six methods, while seven baselines are mentioned in Section 2.4. It is unclear which method is excluded and why.
- **Required correction** Clarify which method is excluded from the runtime comparison and provide a justification.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 4.3.3, Equation 20
- **Evidence pointer** Section 4.3.3
- **Issue** The shortest-path distance bias is described as a "soft structural bias," but the exact form of the bias (e.g., linear, exponential) is not specified. The parameter γ is mentioned but its role is not fully explained.
- **Required correction** Provide the exact functional form of the bias and explain how γ affects the attention distribution.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 2.5, Table 2
- **Evidence pointer** Section 2.5
- **Issue** The ablation study is described, but the table is not visible. It is unclear which datasets were used for the ablation and whether the results are consistent across datasets.
- **Required correction** Ensure the table is fully visible and provide a brief summary of the ablation results in the text.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 4.1, Equation 2
- **Evidence pointer** Section 4.1
- **Issue** The Z-score normalization is applied per gene across all cells. It is unclear whether this is done before or after filtering, and whether any scaling is applied to the final input features.
- **Required correction** Clarify the preprocessing pipeline, including any filtering steps and the order of operations.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4
- **Issue** The authors mention "42 evaluation scenarios" but do not clearly enumerate them. It is unclear how the 42 scenarios are derived from 7 datasets, 2 gene-scale settings, and 3 reference network types.
- **Required correction** Provide a clear enumeration of the evaluation scenarios or a table summarizing them.

## Risk / unsupported claims
- The claim of "consistent improvement" over baselines is not supported by statistical significance testing.
- The claim that IAGRN "mitigates the dimensionality curse" is based on a single dataset comparison and is not systematically validated.
- The biological utility claim based on the case study is limited by the lack of justification for TF selection and the use of a single validation database.
- The novelty of the interleaved attention mechanism is not fully established, as the manuscript does not provide a detailed comparison with other attention-based GRN inference methods that may use similar components.
- The scalability of the method to larger gene sets is discussed theoretically but not empirically demonstrated beyond the TFs+1000 setting.