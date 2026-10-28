## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary figure/table references
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and significance of the claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors introduce QTFPred, a quantum-classical hybrid deep learning framework that integrates quantum convolutional layers into neural networks for transcription factor binding prediction at base resolution. They claim state-of-the-art performance on 92% of binary classification tasks and 96% of signal prediction tasks across 49 ENCODE ChIP-seq datasets, with particular robustness in low-data scenarios. They further claim that the method learns known TF motifs and can identify cooperative TF binding relationships, including a previously underappreciated E2F6-MAX interaction in HeLa cells.
- **Visible evidence base** Main text figures referenced (Figs 1-7), supplementary figures and tables referenced (Figs S1-S33, Tables S1-S2), performance metrics (IOU, Pearson correlation), statistical tests (Welch's t-test, p-values), computational resource measurements
- **Missing materials affecting confidence** Actual figure images and supplementary materials not provided; detailed hyperparameter configurations not fully specified; exact dataset accession numbers for all 49 datasets not listed in main text; code repository not inspected; baseline model training details not fully described

## Reviewer
- **Overall assessment** The manuscript presents a technically interesting application of quantum machine learning to a well-established problem in regulatory genomics. The core idea of replacing the first convolutional layer of a proven architecture (FCNA/FCNsignal) with a quantum convolutional layer is clean and the kernel division strategy for computational tractability is pragmatic. The performance claims are substantial and, if reproducible, would represent a meaningful advance for low-data TF binding prediction. However, several concerns temper my enthusiasm. The computational cost increase (8-22x slower training) is significant and the practical benefit over simpler classical alternatives is not fully established. The biological claims regarding cooperative TF binding, while intriguing, rest on a chain of inference that is not fully validated. The manuscript would benefit from clearer exposition of the quantum advantage mechanism and more rigorous statistical comparisons that account for multiple testing across 49 datasets.
- **Who would be interested in the results, and why** Computational biologists working on TF binding prediction and regulatory genomics would be the primary audience. The demonstrated robustness in low-data scenarios addresses a real bottleneck in the field. Researchers exploring quantum machine learning applications in biology would also find this relevant as a concrete, well-benchmarked example. The cooperative TF binding analysis could interest experimental biologists studying transcriptional regulation, particularly the E2F6-MAX interaction. The broader machine learning community interested in hybrid quantum-classical architectures may also find the kernel division strategy and ablation study informative.
- **Major strengths** The manuscript addresses a genuine problem (limited training data for many TFs) with a novel approach that is well-motivated. The benchmarking is extensive, covering 49 datasets across three cell lines and two task types. The kernel division strategy is a thoughtful engineering solution to the computational constraints of quantum simulation. The ablation study directly tests whether the quantum component contributes to performance. The cooperative TF binding analysis adds biological insight beyond pure prediction. The authors are transparent about computational costs and limitations.
- **Major Concerns** The mechanism by which quantum convolution provides advantage in low-data regimes is not rigorously explained or isolated from other architectural changes. The statistical analysis does not appear to correct for multiple comparisons across 49 datasets. The biological validation of the E2F6-MAX cooperative binding claim is indirect, relying on motif co-occurrence rather than direct experimental evidence. The computational cost increase is substantial and the practical trade-off is not fully contextualized. The comparison to transformer-based models is mentioned in the introduction but these are not included in the benchmarks.
- **Minor Comments** The abstract states 92% and 96% but the results section states 45/49 and 48/49, which should be reconciled for clarity. The description of the quantum advantage in the introduction is somewhat hand-wavy and would benefit from a more precise statement of what "exponential feature space" means in this context. The methods section has incomplete sentences in the data preprocessing description. The choice of 4 qubits is justified by computational constraints but the ablation study only explores up to 4 qubits, leaving open whether more qubits would help. The authors should clarify whether the 13 bp classical kernel in the kernel division strategy is a standard convolution or has any special properties.
- **Technical failings that need to be addressed before the case is established** The statistical framework for comparing methods across many datasets needs to be strengthened, either through multiple testing correction or through a paired analysis framework that accounts for dataset-level variability. The claim of "state-of-the-art" performance requires comparison against a broader set of modern baselines, including at least one transformer-based model. The E2F6-MAX cooperative binding claim needs either direct experimental validation or a more cautious framing as a computational prediction requiring experimental follow-up. The computational cost analysis should include end-to-end wall-clock time including hyperparameter tuning, not just training time per epoch.
- **Assessment against Nature-style criteria** Originality: The application of quantum convolutional layers to TF binding prediction is novel and the kernel division strategy is an original contribution. However, the underlying architecture is a modification of existing classical models rather than a fundamentally new approach. Scientific importance: The problem of low-data TF binding prediction is important and the demonstrated robustness is valuable. The cooperative TF binding analysis adds biological relevance. However, the importance is incremental rather than transformative, as the performance gains are modest in absolute terms and the quantum advantage mechanism is not fully characterized. Interdisciplinary readership: The manuscript bridges quantum computing and genomics, which could attract readers from both communities. However, the technical depth in both areas may limit accessibility. Technical soundness: The experimental design is generally sound with appropriate controls and ablations. The main weaknesses are statistical (multiple testing) and the lack of comparison to modern transformer baselines. Readability for nonspecialists: The manuscript is clearly written but assumes familiarity with both deep learning architectures and genomics terminology. The quantum computing concepts are introduced adequately but the practical significance of the quantum advantage could be explained more intuitively.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is interesting and the results are promising, but the statistical rigor, baseline comparisons, and biological validation need strengthening before the claims can be fully accepted.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The authors claim QTFPred achieves state-of-the-art performance in 92% of binary classification and 96% of signal prediction tasks across 49 datasets.
- **Evidence pointer** Results sections on binary classification and signal regression; Figures 2a-d; Supplementary Figures S5-S6
- **Concern** The performance comparisons across 49 datasets involve many independent statistical tests (Welch's t-tests for each dataset). The manuscript does not report any correction for multiple testing (e.g., Benjamini-Hochberg FDR). With 49 datasets, one would expect several false positives by chance alone. Additionally, the claim of "state-of-the-art" is based on comparison to only two classical baselines (FCN and FCNA for binary; FCNsignal for regression). Modern deep learning approaches for TF binding, particularly transformer-based models like Enformer or DNABERT, are mentioned in the introduction but not included in the benchmarks.
- **Why it matters** Without multiple testing correction, the significance of the performance improvements may be overstated. Without comparison to modern baselines, the "state-of-the-art" claim is not fully supported. Both issues affect the central claim of the manuscript.
- **Resolution test** Apply FDR correction to all p-values across the 49 datasets and report adjusted values. Include at least one transformer-based baseline (e.g., fine-tuned DNABERT or a simpler attention-based model) in the benchmark comparisons. If computational constraints prevent full benchmarking, provide a clear justification and at least a subset comparison.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Biological claim validation
- **Claim pointer** The authors claim to have revealed a previously underappreciated E2F6-MAX functional relationship in HeLa cells with specific spatial constraints (36 bp and 99 bp distances) governing their cooperative binding.
- **Evidence pointer** Results section on cooperative TF binding; Figure 7b; Supplementary Figure S33
- **Concern** The E2F6-MAX cooperative binding claim is based entirely on computational analysis of motif co-occurrence patterns within the learned representations of QTFPred. While the authors cite a prior biochemical study supporting E2F6-MAX interaction, the specific spatial constraints (36 bp and 99 bp) are derived from computational predictions without direct experimental validation. The manuscript does not provide orthogonal computational validation (e.g., using independent ChIP-seq datasets, chromatin conformation data, or existing interaction databases) beyond the single orthogonal ENCSR000EZF dataset used for the distance analysis.
- **Why it matters** The cooperative TF binding analysis is presented as a key biological insight of the manuscript. If the specific distance constraints are not validated, the biological significance of this finding is substantially weakened. Overclaiming biological insights from computational predictions without adequate validation is a common issue that undermines confidence in the overall work.
- **Resolution test** Provide additional validation of the E2F6-MAX interaction using independent computational approaches (e.g., analysis of publicly available ChIP-seq data for both factors, examination of chromatin interaction data, or comparison with known protein-protein interaction databases). Alternatively, temper the claim to clearly state this is a computational prediction requiring experimental validation, and remove the word "revealed" in favor of "predicted."

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Computational cost justification
- **Claim pointer** The authors acknowledge QTFPred is 8-22.5 times slower than baseline models and requires 1.9x more GPU memory, but argue this cost is justified by performance advantages.
- **Evidence pointer** Results section on computational resources; Figure 5a-c; Supplementary Figures S8-S9
- **Concern** The computational cost analysis reports training time per epoch and memory usage, but does not provide end-to-end wall-clock time including hyperparameter tuning, which is a substantial component of the total computational budget. The manuscript does not discuss whether the performance gains justify the computational cost in practical terms, particularly for users with limited GPU resources. The 8-22x slowdown is significant and the manuscript does not provide a cost-benefit analysis or discuss scenarios where the trade-off is clearly favorable.
- **Why it matters** For a method to be adopted by the community, the computational cost must be justified relative to the performance gain. If the performance improvement is marginal for high-data TFs but the cost is consistently 8-22x higher, many users may prefer the simpler classical baselines. The manuscript should provide clearer guidance on when QTFPred is the preferred choice.
- **Resolution test** Provide end-to-end training time including hyperparameter tuning for at least one representative dataset. Include a discussion of the practical trade-off, identifying specific scenarios (e.g., low-data TFs, high-accuracy requirements) where QTFPred's cost is clearly justified. Consider reporting performance per unit of computational cost as a complementary metric.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Mechanism of quantum advantage
- **Claim pointer** The authors attribute QTFPred's performance gains to the quantum convolutional layer's ability to explore higher-dimensional feature spaces and capture nonlocal dependencies between nucleotides through entanglement.
- **Evidence pointer** Introduction; Architecture of quantum convolutional layer; Ablation study; Figure 5d-e; Supplementary Figure S10
- **Concern** The ablation study demonstrates that adding quantum layers improves performance, but does not isolate the mechanism. The improvement could be due to the increased model capacity, the specific nonlinear transformations introduced by the quantum circuit, or the particular architectural choices (e.g., kernel division strategy) rather than a uniquely "quantum" advantage. The manuscript does not compare against a classical model with similar capacity or architectural complexity, which would help distinguish quantum-specific benefits from general model improvements.
- **Why it matters** The claim that quantum computing provides a unique advantage is central to the manuscript's significance. If the same performance could be achieved with a classical model of comparable complexity, the quantum aspect would be less compelling. Understanding the mechanism is also important for guiding future improvements.
- **Resolution test** Include a classical baseline with matched capacity (e.g., a wider or deeper classical CNN with similar parameter count) in the ablation study. Discuss whether the performance gains are attributable to quantum-specific properties (entanglement, superposition) or simply to increased model expressiveness. If possible, test with different numbers of qubits and classical analog to show a scaling difference.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and consistency
- **Affected element** Abstract and Results
- **Evidence pointer** Abstract; Results sections on binary and signal prediction
- **Issue** The abstract states "92% of binary classification datasets and 96% of signal prediction datasets" while the results section states "45 cases (92%)" and "48 datasets (98%)" for signal prediction. The discrepancy between 96% and 98% for signal prediction should be reconciled.
- **Required correction** Ensure consistent reporting of percentages across abstract and main text. If the 96% in the abstract is correct, update the results section accordingly.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section on data preprocessing
- **Evidence pointer** Materials and methods, Data and preprocessing
- **Issue** The data preprocessing section contains incomplete sentences and lacks specific details on negative sample generation for the signal prediction task. The sentence "The preprocessing steps included:" is followed by no enumerated steps in the provided text.
- **Required correction** Complete the data preprocessing description with specific steps for signal prediction data preparation, including how negative samples were generated and any filtering or normalization steps applied.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results sections
- **Evidence pointer** Results sections on binary and signal prediction; Figures 2-3
- **Issue** The manuscript reports p-values from Welch's t-tests but does not report effect sizes or confidence intervals. Given the large number of datasets, effect sizes would help readers assess the practical significance of the improvements.
- **Required correction** Report effect sizes (e.g., Cohen's d) or confidence intervals for the key comparisons, at least for the representative examples shown in the main figures.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction; Discussion
- **Issue** The introduction mentions transformer-based models (DNABERT, Enformer, Nucleotide Transformer) but does not discuss how QTFPred relates to or differs from these approaches beyond noting their computational cost. The discussion does not address whether QTFPred could be combined with transformer architectures.
- **Required correction** Add a brief discussion of how QTFPred compares conceptually to transformer-based approaches and whether the quantum enhancement strategy could be applied to transformer architectures, as hinted in the final paragraph of the discussion.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Figure accessibility
- **Affected element** All figures
- **Evidence pointer** Figures 1-7
- **Issue** The figure descriptions in the text are referenced but the actual figure content is not available for review. The text descriptions suggest complex multi-panel figures, but without seeing them, it is difficult to assess whether the visualizations effectively support the claims.
- **Required correction** Ensure all figures are self-contained with clear labels, legends, and annotations. Consider adding a schematic of the QTFPred architecture in Figure 1 that clearly shows the quantum and classical components and their interaction.

## Risk / unsupported claims
- The claim of "state-of-the-art" performance is not fully supported without comparison to modern transformer-based baselines.
- The specific spatial constraints (36 bp and 99 bp) for E2F6-MAX cooperative binding are computational predictions without direct experimental validation.
- The attribution of performance gains to quantum-specific properties (entanglement, superposition) is not rigorously established, as the ablation study does not control for model capacity.
- The claim that QTFPred "reveals" cooperative TF binding mechanisms overstates what can be concluded from computational motif co-occurrence analysis alone.
- The statement that quantum circuits "explore exponentially large Hilbert space" as a source of advantage is not empirically demonstrated in this context.
- The generalizability of QTFPred's advantage to other genomic prediction tasks beyond TF binding is speculative and not tested.