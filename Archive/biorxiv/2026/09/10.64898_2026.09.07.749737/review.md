## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, discussion, conclusions, data availability)
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and suitability for a high-impact general audience
- **Shared manuscript claim summary** The authors present PRIS, a unified structure-based deep learning framework combining two components, PRISeq and PRIScore, for inferring protein-RNA binding preferences and improving selection of native-like protein-RNA complex structures. They claim state-of-the-art performance on PWM inference, docking re-ranking, and virtual screening benchmarks, with substantial computational speedups over empirical scoring functions.
- **Visible evidence base** Abstract, full methods narrative, results narrative, three tables referenced (Tables 1-4), four figures referenced (Figures 1-5), dataset descriptions, benchmark descriptions
- **Missing materials affecting confidence** Actual figures and tables are not provided; model architecture diagrams, performance tables, and benchmark result plots are referenced but absent. Training hyperparameters, exact data splits, and statistical significance tests are not fully described. Code and data are available at external repositories but were not inspected.

## Reviewer
- **Overall assessment** The manuscript addresses an important and timely problem, namely the integration of structure prediction and binding preference inference for protein-RNA interactions. The proposed framework is conceptually appealing and the reported results, if accurate, would represent a meaningful advance. However, the current manuscript has several technical gaps that prevent full evaluation of the claims. The absence of actual figures and tables, incomplete methodological details, and limited benchmark scope reduce confidence in the reported performance. The work is potentially significant but requires substantial revision and additional validation before the claims can be considered established.

- **Who would be interested in the results, and why** Computational biologists working on protein-RNA interactions, RNA aptamer design, and structure-based drug discovery would be the primary audience. Researchers developing deep learning methods for biomolecular structure prediction and sequence design would also find the framework relevant. The claimed computational efficiency and accuracy improvements over empirical scoring functions could have practical implications for high-throughput screening applications.

- **Major strengths** The conceptual integration of structure selection and binding preference inference into a single framework is a novel and sensible contribution. The use of a unified feature extractor with anti-symmetric graph attention and sparse attention is technically interesting. The reported computational speedups are substantial and practically relevant. The evaluation across three distinct benchmark types (PWM, docking, screening) provides a broad assessment of the framework's capabilities.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The manuscript claims PRISeq outperforms all baselines across four metrics on the PWM dataset (ACC 65.6%, SCC 0.43, MSE 0.43, MAE 0.75), and PRIScore improves top-1 success rate to 81.91% on the docking benchmark.
- **Evidence pointer** Tables 1-4, Figures 1-5; location not provided
- **Concern** The actual tables and figures containing the performance data are not included in the provided manuscript text. Without these, the numerical claims cannot be verified against the described methodology. The reader cannot assess whether the reported improvements are statistically significant, whether error bars are present, or whether the comparisons are fair.
- **Why it matters** The central claims of the manuscript rest entirely on these numerical results. Without access to the actual data presentation, the validity of the performance claims cannot be evaluated. This is a fundamental barrier to assessing the manuscript's contribution.
- **Resolution test** Provide the actual tables and figures with full numerical data, including error estimates and statistical significance tests where applicable.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The manuscript states that the structure dataset of 9,110 complexes was used for training, with 328 complexes labeled with affinity data for fine-tuning. It also describes a two-step training procedure with normal training and fine-tuning.
- **Evidence pointer** Materials and Methods, Model training section; location not provided
- **Concern** The description of the training procedure is incomplete. Key hyperparameters (learning rate, batch size, number of epochs, optimizer, regularization) are not specified. The exact split between training, validation, and test sets is not described beyond the exclusion of test-set homologous chains. The fine-tuning procedure with the affinity data is described only briefly, and the role of the correlation loss L_affi in the total loss is not fully explained.
- **Why it matters** Reproducibility is a core requirement for computational methods. Without complete training details, other researchers cannot replicate the results or apply the method to their own data. The lack of hyperparameter information also prevents assessment of whether the reported performance is robust or overfitted.
- **Resolution test** Provide complete training details, including all hyperparameters, data split procedures, and a clear description of the loss function components and their weights.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Benchmark validity
- **Claim pointer** The manuscript claims PRISeq achieves an EF 0.5% of 14.40 on the MS2 library, approximately double the best baseline, and an AUROC of 0.63. For the aptamer screening, PRIS achieves EF 0.5% of 8.19 (NELF-E) and 11.57 (GFP).
- **Evidence pointer** Tables 2 and 4, Figure 3 and 5; location not provided
- **Concern** The screening benchmarks are described with limited detail. The definition of "active" ligands (top 1% by experimental binding data) is provided, but the distribution of experimental binding affinities is not described. The manuscript does not report whether the baselines were optimized for the screening task or used with default parameters. The choice of EF 0.5%, 1%, and 5% cutoffs is not justified. For the aptamer screening, the manuscript reports an AUROC of 0.48 for GFP, which is below random chance, yet the authors interpret this favorably due to high EF at stringent cutoffs. This inconsistency requires explanation.
- **Why it matters** The screening results are a key claimed advantage of the method. If the benchmark setup is not fully described or the baselines are not fairly compared, the reported improvements may be artifacts of the evaluation protocol. The sub-random AUROC for GFP raises questions about the method's generalizability.
- **Resolution test** Provide detailed descriptions of the screening benchmark setup, including baseline parameter choices, the distribution of experimental affinities, and a discussion of the GFP AUROC result.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The manuscript states that PRISeq learned intrinsic protein-RNA binding preferences rather than overfitting on family-specific patterns, based on the observation that the average MAE for families with the fewest structures (0.77) is close to the overall average (0.75).
- **Evidence pointer** Results, PWM inference section, Figure 2C; location not provided
- **Concern** The evidence for generalizability is indirect and based on a single comparison. The manuscript does not report performance on held-out protein families that were entirely excluded from training. The claim that the model learned intrinsic preferences rather than family-specific patterns requires more direct testing, such as cross-family validation or analysis of learned representations.
- **Why it matters** The stated goal of the method is to provide generalizable binding preference inference. If the model only performs well on families represented in the training set, its practical utility is limited. The current evidence is insufficient to support the generalizability claim.
- **Resolution test** Perform cross-family validation experiments where entire protein families are held out from training, and report performance on these held-out families.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Comparison fairness
- **Claim pointer** The manuscript compares PRISeq against FoldX, Rosetta-based scoring functions, and NA-MPNN on the PWM benchmark, and against FoldX, Rosetta-based functions, and AlphaFold3 on the docking benchmark.
- **Evidence pointer** Results sections; location not provided
- **Concern** The manuscript does not describe how the baseline methods were configured or whether their parameters were optimized for the respective tasks. For NA-MPNN, the original method was designed for DNA, and its adaptation to RNA is not described. For the docking benchmark, the comparison is between re-ranking methods applied to AlphaFold3 outputs, but the manuscript does not clarify whether the baselines were given the same input features or computational budget.
- **Why it matters** Fair comparison is essential for establishing the claimed improvements. If baselines are not optimally configured, the reported advantages may be overstated. The adaptation of NA-MPNN to RNA requires explicit description.
- **Resolution test** Describe baseline configurations in detail, including any parameter optimization, and ensure all methods receive equivalent input information.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states PRISeq screens 129,248 RNA hairpins within 11.95 seconds, but the hardware specifications are not provided. This makes the computational claim difficult to contextualize.
- **Required correction** Specify the hardware (GPU model, CPU, memory) used for the timing measurement.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results, PWM inference
- **Evidence pointer** Table 1; location not provided
- **Issue** The manuscript reports improvements in ACC, SCC, MSE, and MAE but does not report confidence intervals or statistical significance tests for the differences between methods.
- **Required correction** Provide confidence intervals or statistical tests (e.g., bootstrap or paired tests) for the reported metrics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Methodological detail
- **Affected element** Materials and Methods, Graph representations
- **Evidence pointer** Materials and Methods section; location not provided
- **Issue** The description of the protein graph construction is incomplete. The sentence "The the binding pocket. Each pocket was then represented as a graph" appears to be a typographical error, and the exact definition of the pocket (e.g., residues within 10.0 Å of RNA) is stated but the selection criteria for the pocket center are unclear.
- **Required correction** Correct the typographical error and provide a clear, complete description of the pocket definition and graph construction.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data description
- **Affected element** Dataset preparation
- **Evidence pointer** Materials and Methods, Dataset preparation; location not provided
- **Concern** The manuscript states that 328 protein-RNA complexes were labeled with affinity data from PDBbind or PRA310, but the overlap between these two sources and the criteria for inclusion are not described.
- **Required correction** Describe the data collection and filtering criteria for the affinity-labeled complexes.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, Aptamer screening
- **Evidence pointer** Table 4, Figure 5; location not provided
- **Issue** The manuscript reports an AUROC of 0.48 for GFP aptamer screening, which is below 0.5. The authors interpret this as acceptable due to high EF at stringent cutoffs, but this interpretation is not standard and requires justification.
- **Required correction** Provide a more detailed analysis of the GFP screening results, including the distribution of scores and a discussion of why AUROC is not the appropriate metric in this case.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Literature context
- **Affected element** Introduction
- **Evidence pointer** Introduction; location not provided
- **Issue** The introduction cites several existing methods but does not provide a systematic comparison of their limitations in the context of the proposed unified framework.
- **Required correction** Expand the introduction to more clearly position the proposed method relative to existing approaches and articulate the specific gaps addressed.

## Risk / unsupported claims
- The claim that PRISeq "learned intrinsic protein-RNA binding preferences rather than overfitting on family-specific patterns" is not directly supported by the provided evidence. The comparison of average MAE between family groups is indirect and does not constitute a rigorous test of generalizability.
- The claim of "approximately three orders of magnitude acceleration" compared to FoldX is based on timing measurements without specified hardware, making the comparison potentially misleading.
- The interpretation of the GFP aptamer screening results (AUROC 0.48) as favorable is not supported by standard evaluation practices and requires additional analysis.
- The claim that PRIS "provides an efficient framework for large-scale RNA library screening and aptamer design" is based on benchmarks with only three target proteins, which may not be representative of the broader applicability.
- The manuscript states that PRIScore improves secondary structure accuracy for NELF-E aptamer, but the quantitative comparison with AlphaFold3 is only described narratively without actual data in the provided text.