## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, experimental section, figure legends not provided)
- **Assessment boundary** Scientific soundness, methodological rigor, validity of claims, and alignment with Nature-style criteria based solely on the provided manuscript text
- **Shared manuscript claim summary** The authors present CellPolaris, a unified computational framework for TF-centered GRN construction via transfer learning, master TF identification, and TF perturbation simulation. The framework requires only transcriptomic data as input, leverages pre-constructed high-confidence GRNs from diverse contexts, and is benchmarked against existing methods. The authors validate predictions using known reprogramming factor combinations and an Rfx2 knockout mouse model.
- **Visible evidence base** Main text (abstract, introduction, results, experimental section, author contributions, acknowledgements); figure and table references cited but figures/tables themselves not provided; supplementary figure references cited but not provided
- **Missing materials affecting confidence** All figures, tables, and supplementary materials; detailed benchmark datasets and preprocessing steps; hyperparameter settings; code implementation details; statistical test outputs; raw data analysis results

## Reviewer

- **Overall assessment** The manuscript presents a potentially useful computational framework that integrates transfer learning for GRN construction with downstream tasks of master TF identification and perturbation simulation. The conceptual advance of requiring only transcriptomic data while leveraging pre-existing multi-omics-derived GRNs is interesting and could have practical value. However, the current manuscript text provides insufficient detail to fully evaluate the methodological rigor, the validity of the benchmarking approach, and the strength of the biological validations. Several claims appear to exceed what the presented evidence can support, particularly regarding the accuracy of perturbation simulations and the significance of the Rfx2 validation. The manuscript would benefit from clearer articulation of the novelty relative to existing tools, more rigorous statistical reporting, and additional details on the transfer learning architecture and evaluation protocols.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on gene regulatory network inference, particularly those interested in transfer learning approaches and integrating multi-omics data. Researchers studying cell fate determination, reprogramming, and differentiation would also be interested in the master TF identification and perturbation simulation capabilities. The framework's ability to work with transcriptomic data alone could appeal to laboratories without access to extensive epigenomic datasets.

- **Major Strengths**
  1. The conceptual framework of using transfer learning to generalize GRNs across contexts with minimal input requirements is a valuable direction.
  2. The integration of three tasks (GRN construction, master TF identification, perturbation simulation) into one unified framework is practically useful.
  3. The inclusion of cross-species transfer via the Extrapolative Mixup method addresses an important challenge.
  4. The validation using actual Rfx2 knockout experiments provides biological grounding.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that CellPolaris achieves approximately 95% R² correlation with high-confidence GRNs and outperforms existing methods (Figure 3A-F)
- **Evidence pointer** Results section, Figure 3, Figure S4, Experimental Section "Ground Truth TF-TG regulations and GRN Benchmark"
- **Concern** The benchmarking methodology raises several questions. First, the ground truth is derived from ChIP-Seq data, but the conversion process to binary networks (top 100 genes per TF) is arbitrary and may not reflect true regulatory relationships. Second, the comparison with other methods appears to use the same transcriptomic input for all methods, but methods like PECA2 require paired ATAC-Seq data, creating an unfair comparison. Third, the R² metric for evaluating GRN construction is unusual; most GRN inference methods are evaluated using AUROC or AUPRC on edge prediction, and the choice of R² needs justification. Fourth, the claim of 95% R² seems surprisingly high for GRN inference and may indicate overfitting or evaluation on training data. The details of the cross-validation scheme, the number of domains used for training versus testing, and whether the test domains were truly unseen during training are not provided.
- **Why it matters** The core claim of the manuscript is that CellPolaris constructs accurate GRNs. If the benchmarking methodology is flawed or the evaluation metrics are inappropriate, the central claim is not established. The unusually high performance also raises concerns about potential data leakage or circularity in the evaluation.
- **Resolution test** Provide detailed descriptions of the train/test domain splits, ensure that test domains are completely excluded from training, justify the choice of R² as an evaluation metric, and compare against methods using identical input data. Report AUPRC and precision-recall curves in addition to AUROC. Clarify whether the 95% R² is on training or held-out domains.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The claim that CellPolaris accurately simulates the developmental consequences of Rfx2 knockout during round spermatid differentiation (Figure 6)
- **Evidence pointer** Results section "Simulating and Validating the Effects of Rfx2 Knocking Out on Round Spermatid Development", Figure 6, Figure S7, Experimental Section "Statistical Testing of the Accuracy of TGs Expression Changes"
- **Concern** The validation of the perturbation simulation is based on a single gene (Rfx2) in a single biological context. The statistical test uses a hypergeometric test on 7 out of 26 predicted positively regulated genes that were downregulated with >2-fold change. However, the manuscript does not report the total number of predicted target genes, the false discovery rate, or the expected overlap by chance. The comparison with CellOracle appears to be based on a single comparison without reporting variance or confidence intervals. Additionally, the manuscript states that CellPolaris shows "partial advantages" over CellOracle, which is vague and not quantified. The trajectory analysis (Figure 5D-G) is described qualitatively without statistical support.
- **Why it matters** The perturbation simulation is a key claimed capability of the framework. A single-gene validation with weak statistical reporting is insufficient to establish that the method reliably predicts perturbation outcomes. The vague claim of "partial advantages" over CellOracle is not scientifically rigorous.
- **Resolution test** Provide comprehensive statistical analysis including false discovery rates, confidence intervals, and effect sizes. Validate on multiple TFs across different biological contexts. Quantify the comparison with CellOracle using appropriate statistical tests. Report the full distribution of predicted target gene changes and the expected overlap by chance.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that the Extrapolative Mixup (extra_mixup) method improves cross-species GRN prediction (Figure S3)
- **Evidence pointer** Results section "Utilizing Cross-Species Regulatory Relationships For Enhancing Generalization", Figure S3, Experimental Section
- **Concern** The description of the extra_mixup method is insufficient to understand its implementation. The manuscript states that it "extends our original method for cross-species scenarios" and uses "paired" tissues across species, but the specific mechanism of extrapolation is unclear. The validation appears to be limited to heart-specific regulatory edges, and the claim that "increasing the number of organs sourced from external species further enhances CellPolaris's overall performance without significantly increasing the proportion of false TF-TG relationships" is not supported by quantitative data in the text. The choice of kidney as the paired tissue for heart prediction is not justified.
- **Why it matters** Cross-species transfer is presented as a key advantage of the framework. Without clear methodological details and rigorous validation, this claim cannot be assessed. The potential for overfitting or spurious correlations in cross-species transfer is a significant concern.
- **Resolution test** Provide a detailed algorithmic description of extra_mixup, including pseudocode. Justify the choice of paired tissues. Report quantitative results with statistical significance for the improvement over baseline. Test on multiple cross-species scenarios beyond human-mouse.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The claim that CellPolaris provides a "unified framework" that enables efficient GRN construction, master TF identification, and perturbation simulation with minimal input
- **Evidence pointer** Abstract, Introduction, Results
- **Concern** While the integration of three tasks is presented as a key novelty, the manuscript does not clearly articulate what is fundamentally new compared to existing tools. CellOracle already performs GRN-based perturbation simulation, and several tools exist for master TF identification. The transfer learning approach for GRN construction is the most novel component, but its advantages over existing transcriptomic-only methods (e.g., GENIE3, GRNBoost2) are not clearly demonstrated beyond the reported benchmarks. The manuscript does not discuss the computational cost, scalability, or practical usability of the framework.
- **Why it matters** For a Nature-style publication, the scientific importance and novelty must be clearly established. If the framework is primarily an integration of existing methods with a transfer learning component, the advance may be incremental rather than transformative.
- **Resolution test** Clearly articulate the specific novel contributions of each component. Provide a comprehensive comparison with existing tools, including runtime, scalability, and usability. Discuss the potential impact on the field and the types of biological questions that can now be addressed.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states that CellPolaris "decodes the roles of transcription factors" but does not specify the input data requirements clearly. The phrase "requires only transcriptomic data as input" appears in the introduction but not in the abstract, which may mislead readers about the framework's requirements.
- **Required correction** Clarify in the abstract that the framework requires only transcriptomic data for inference after training, and specify what data are needed for training.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Experimental Section, "Critical Domain Training"
- **Evidence pointer** Experimental Section, Equations 6-8
- **Issue** The hyperparameter σ (top-σ ratio for critical domain selection) and α (Beta distribution parameter for Mixup) are mentioned but their default values are not provided. The manuscript also does not describe how these hyperparameters were tuned.
- **Required correction** Provide default values for all hyperparameters and describe the hyperparameter tuning procedure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results section, "Performance of the GRN Transfer Model"
- **Evidence pointer** Figure 3A
- **Issue** The manuscript reports R² values but does not report confidence intervals or variance across cross-validation folds. The comparison with other methods appears to be based on point estimates without statistical testing.
- **Required correction** Report confidence intervals or standard deviations for all performance metrics and perform statistical significance testing for method comparisons.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results section, "Prediction of Potential Master TFs During Cell Fate Transitions"
- **Evidence pointer** Figure 4, Figure S5
- **Issue** The manuscript states that "majority of combinations of reprogramming factors were included in the list of top-ranked TFs" but does not provide the full lists of predicted TFs or the exact overlap statistics. The claim that "TFs that have not been previously reported are often located in the same gene families with master TFs" is anecdotal and not systematically demonstrated.
- **Required correction** Provide complete lists of predicted TFs for each reprogramming scenario, report exact overlap statistics with known factors, and systematically analyze the family relationships of novel predictions.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical clarity
- **Affected element** Experimental Section, "PGM Method Overview"
- **Evidence pointer** Experimental Section, Equations 11-19
- **Issue** The description of the probabilistic graphical model is brief and lacks details on how the conditional distributions are learned, how the graph structure is incorporated, and how the model handles cycles. The relationship between the PGM and the transfer learning GRN is not fully explained.
- **Required correction** Provide a more detailed description of the PGM, including the learning algorithm, inference procedure, and how it integrates with the transfer learning component.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Data availability
- **Affected element** Data Availability Statement
- **Evidence pointer** Data Availability Statement
- **Issue** The data availability statement mentions deposition in GSA but does not specify which datasets were deposited or provide accession details beyond a reference number. The statement "available from the corresponding authors upon reasonable request" is vague.
- **Required correction** Provide specific accession numbers for all deposited datasets and clarify which data are available upon request.

## Risk / unsupported claims
- The claim of approximately 95% R² correlation for GRN construction is not sufficiently supported without detailed benchmarking methodology and independent validation.
- The claim that CellPolaris "accurately simulates" the consequences of Rfx2 knockout is based on a single gene validation with limited statistical power.
- The claim of "partial advantages" over CellOracle is vague and not quantified.
- The claim that cross-species transfer via extra_mixup improves performance without increasing false positives is not quantitatively supported in the text.
- The claim that the framework "allows us to further elucidate the regulatory mechanisms underlying developmental processes" is a general statement not directly supported by specific biological insights presented.
- The performance comparison with existing methods (GENIE3, GRNBoost2, SCEL, etc.) cannot be fully evaluated without seeing the actual benchmark results and experimental details.
- The statistical significance of the overlap between predicted master TFs and known reprogramming factors is not reported.
- The manuscript claims the framework is "unified" but does not demonstrate seamless integration of the three tasks in a single pipeline with clear user interfaces or documentation.