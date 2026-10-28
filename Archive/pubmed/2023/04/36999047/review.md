## Review setup
- **Input scope** Full manuscript text, including abstract, introduction, methods, results, and discussion sections, as provided.
- **Assessment boundary** Evaluation is limited to the content of the provided manuscript. No external data, code, or supplementary materials were accessed or verified.
- **Shared manuscript claim summary** The authors present CRMnet, a deep learning model combining convolutional and transformer architectures with a U-Net-style encoder-decoder structure, to predict gene expression from yeast promoter sequences. They report superior predictive performance compared to existing models, demonstrate biological interpretability via saliency maps that align with known transcription factor motifs, and provide training time comparisons between TPUs and GPUs.
- **Visible evidence base** The manuscript includes performance metrics (Pearson correlation, MSE, R2, MAE) for random and native promoter sequences in two media conditions, ablation study results, saliency map visualizations compared to known motifs, and a hardware training time comparison table. Figures and supplementary tables are referenced but not fully visible in the provided text.
- **Missing materials affecting confidence** The actual figures, supplementary tables, and supplementary figures are not included in the provided material. Code and data availability statements are present, but the repositories were not accessed. Detailed hyperparameter settings, model architecture diagrams, and exact training configurations are only partially described.

## Reviewer
- **Overall assessment** The manuscript presents a technically sound deep learning architecture for a relevant problem in regulatory genomics. The reported performance improvements over existing models are modest but consistent. The interpretability analysis using saliency maps is a valuable contribution, though the biological validation is somewhat superficial. The hardware comparison is useful for practitioners but is not a central scientific contribution. The writing is generally clear, though some methodological details are lacking. The work is likely of interest to researchers in computational genomics and deep learning applied to biology, but the scientific novelty is incremental given the existing literature on similar architectures.
- **Who would be interested in the results, and why** Researchers working on sequence-to-expression prediction, regulatory genomics, and interpretable deep learning for biology would find this work relevant. The practical training time comparisons may also interest those deploying such models on large-scale hardware. The interpretability approach could inform similar efforts in other organisms or regulatory contexts.
- **Major strengths** The manuscript addresses a well-motivated problem with a large, publicly available dataset. The architecture combines established components (CNN, transformer, U-Net) in a sensible way. The evaluation includes multiple metrics and both random and native sequences. The interpretability analysis is a positive step toward biological relevance. The hardware comparison provides practical guidance.
- **Major Concerns** The performance gains over the benchmark transformer model are small (e.g., 0.971 vs. 0.963 for native sequences), and the statistical significance of these differences is not assessed. The biological interpretability analysis is limited to visual comparison of saliency logos with known motifs, without quantitative enrichment or functional validation. The ablation study is described but the results are only partially presented in the text. The training time comparison lacks details on software versions, compiler optimizations, and potential bottlenecks beyond raw hardware. The manuscript does not discuss limitations of the approach or potential failure modes.
- **Minor Comments** The introduction could better contextualize the novelty relative to the transformer model of Vaishnav et al. (2022). The description of the U-Net architecture could be more precise regarding the number of layers and feature map dimensions. The choice of 112 bp input length and the padding strategy could be justified more thoroughly. The saliency map filtering criteria (thresholds for low weights) are not fully specified. The hardware comparison would benefit from including energy consumption or cost metrics.
- **Technical failings that need to be addressed before the case is established** The lack of statistical significance testing for performance differences is a notable gap. The interpretability analysis needs quantitative support, such as enrichment scores or comparison against randomized controls. The ablation study results should be presented with error bars or confidence intervals to assess variability.
- **Assessment against Nature-style criteria** Originality: The architecture is a combination of known components, and the specific application to yeast promoter sequences is novel but incremental. Scientific importance: The problem is important, and the interpretability angle adds value, but the advances are modest. Interdisciplinary readership: The work bridges deep learning and genomics, which has broad appeal, but the technical depth may limit accessibility. Technical soundness: The methods are generally sound, but the lack of statistical rigor and quantitative interpretability analysis weakens the case. Readability for nonspecialists: The manuscript is reasonably clear, but some sections assume familiarity with deep learning terminology.
- **Recommendation posture** Supportive if technical concerns are resolved, particularly regarding statistical significance, quantitative interpretability validation, and more detailed methodological reporting.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The manuscript claims that CRMnet outperforms the benchmark transformer model, citing Pearson correlation coefficients of 0.971 vs. 0.963 for native sequences and 0.987 vs. 0.979 for random sequences.
- **Evidence pointer** Section 3.1, Figure 3, Supplementary Tables 2 and 3
- **Concern** The reported performance differences are small, and no statistical significance testing is provided. It is unclear whether these differences are reproducible across multiple training runs or are within the range of random variation.
- **Why it matters** Without significance testing or confidence intervals, the claim of improved performance cannot be reliably distinguished from noise, which is critical for a central claim of the manuscript.
- **Resolution test** Provide confidence intervals or significance tests (e.g., bootstrap or repeated training runs) for the performance metrics, and report the number of independent runs used.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretability validation
- **Claim pointer** The manuscript states that saliency maps match known yeast motifs and that this supports the model learning biologically meaningful features.
- **Evidence pointer** Section 3.3, Figures 5A–E and 5F, Supplementary Figure 2
- **Concern** The comparison between saliency logos and known motifs is visual and qualitative. No quantitative measure of overlap or enrichment is provided, and there is no control comparison against random sequences or shuffled motifs.
- **Why it matters** The biological interpretability claim is a key contribution, but without quantitative validation, the evidence is anecdotal and could be coincidental.
- **Resolution test** Compute a quantitative overlap score (e.g., Pearson correlation between saliency and motif position weight matrices, or enrichment of high-saliency positions within known motif sites) and compare against a null distribution from randomized controls.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Methodological detail
- **Claim pointer** The ablation study is described as demonstrating the contribution of transformer and squeeze-excitation blocks to performance.
- **Evidence pointer** Section 3.2, Figure 4
- **Concern** The ablation results are only partially described in the text, and the figure is not visible in the provided material. It is unclear whether the ablations were run with the same training setup, how many replicates were performed, and whether the differences are statistically meaningful.
- **Why it matters** Ablation studies are important for justifying architectural choices, but incomplete reporting prevents the reader from assessing the robustness of the conclusions.
- **Resolution test** Provide full ablation results with error bars or confidence intervals, specify the number of runs, and describe the training setup for each ablation.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Hardware comparison completeness
- **Claim pointer** The manuscript claims that training time can be reduced from 70 hours to 4 hours using distributed training and mixed precision.
- **Evidence pointer** Section 3.4, Table 1
- **Concern** The comparison is limited to raw training time and does not account for factors such as software versions, communication overhead, or energy consumption. The claim of a 17.5x speedup may be misleading without these details.
- **Why it matters** The hardware comparison is presented as a practical contribution, but incomplete context limits its usefulness and could mislead practitioners.
- **Resolution test** Report software versions, communication overhead, and consider including energy or cost metrics. Clarify whether the 70-hour baseline was run under the same conditions as the optimized setup.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Introduction
- **Evidence pointer** Section 1
- **Issue** The introduction could better distinguish the novelty of CRMnet from the transformer model of Vaishnav et al. (2022), beyond the architectural changes.
- **Required correction** Add a brief paragraph explicitly stating the expected benefits of the U-Net and CNN components over the prior transformer approach.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model architecture description
- **Evidence pointer** Section 2
- **Issue** The number of layers, filter sizes, and feature map dimensions for the CNN and transformer components are not fully specified.
- **Required correction** Provide a table or detailed text listing the exact architecture parameters, including layer counts, hidden dimensions, and attention heads.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data processing
- **Affected element** Section 4.3
- **Evidence pointer** Section 4.3
- **Issue** The padding strategy for sequences shorter than 112 bp is described, but the impact of padding on model performance is not discussed.
- **Required correction** Add a sentence or short paragraph addressing whether padding affects predictions and how the model handles the padding token.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Presentation
- **Affected element** Figure 5
- **Evidence pointer** Section 3.3, Figure 5
- **Issue** The saliency logo plots are described as matching known motifs, but the figure is not visible in the provided material, making it difficult to assess the claim.
- **Required correction** Ensure the figure is clearly labeled and include a supplementary table with quantitative overlap scores for each motif.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Section 3
- **Issue** The discussion does not address potential limitations of the model, such as sensitivity to input length, generalizability to other organisms, or failure cases.
- **Required correction** Add a limitations paragraph acknowledging these issues and suggesting future work.

## Risk / unsupported claims
- The claim that CRMnet "outperforms" benchmark models is not statistically substantiated.
- The claim that saliency maps "support that our model can successfully locate the binding sites of transcription factors" is based on qualitative visual comparison only.
- The claim of a 17.5x training time reduction is presented without sufficient context on hardware, software, and communication overhead.
- The ablation study claims are not fully supported by the visible evidence, as the figure is not provided and no statistical measures are reported.
- The statement that the model "can be used predictively to design new regulatory sequences" is speculative and not demonstrated in the manuscript.