## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and figure legends
- **Assessment boundary** Scientific validity, technical soundness, reproducibility, and support of claims based solely on the provided manuscript content
- **Shared manuscript claim summary** The authors present a multi-label deep learning model trained on A. thaliana DAP-seq data to predict transcription factor family binding across 46 families. They claim the model captures sequence context and syntax beyond isolated motifs, enables annotation of untargeted assays like MOA-seq, transfers across species to Z. mays under heat stress, and identifies regulatory variants associated with phenotypic traits, validated via STARR-seq.
- **Visible evidence base** Main text figures 1-7 with legends, methods section, supplementary figure and table references, source data statements
- **Missing materials affecting confidence** Supplementary figures, supplementary data files, supplementary methods, and source data files were not provided. These are referenced extensively and are essential for evaluating key claims.

## Reviewer
- **Overall assessment** This manuscript presents a potentially valuable computational resource for plant regulatory genomics. The multi-label classification approach across TF families is a sensible advance over per-TF binary models, and the application to MOA-seq annotation and cross-species transfer is timely. However, the manuscript as provided has several critical gaps. The most significant concern is that the central validation claims, particularly the STARR-seq experiments and the GWAS variant analysis, are presented with insufficient quantitative detail in the main text. The reliance on supplementary materials that were not available for review substantially limits the ability to assess technical rigor. The model performance metrics, while reasonable, are not contextualised against simpler baselines beyond shuffled controls. The biological insights, while interesting, are largely descriptive. The manuscript would benefit from clearer articulation of the novelty relative to existing plant regulatory deep learning models and a more rigorous demonstration that the multi-label formulation provides tangible benefits over ensembles of single-label models.

- **Who would be interested in the results, and why** Plant molecular biologists and regulatory genomicists studying transcription factor binding and cis-regulatory element function. Researchers working on crop improvement and variant-to-function analysis would find the GWAS variant prioritisation approach useful. Computational biologists developing deep learning methods for regulatory genomics would be interested in the multi-label architecture and the explainability framework. The cross-species transfer demonstration in maize under heat stress broadens the appeal to crop stress biology communities.

- **Major strengths**
  1. The multi-label classification framework across 46 TF families is a practical and scalable advance over per-TF binary classifiers, addressing a real bottleneck in plant regulatory genomics.
  2. The integration of multiple explainability metrics (SHAP, TF-MoDISco, IPM context importance) provides a comprehensive framework for model interpretation that goes beyond typical attention-based analyses.
  3. The demonstration of cross-species transfer from A. thaliana to Z. mays, a distantly related monocot, is a significant and non-trivial result with clear practical implications.
  4. The application to MOA-seq annotation addresses a genuine need, as untargeted footprinting assays lack TF identity information.
  5. The experimental validation via STARR-seq, while needing more detail, represents a commendable effort to connect predictions to functional outcomes.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that the model "predicts differential TF-binding and identifies regulatory gene variants within quantitative trait loci" and that STARR-seq validation demonstrates "the link between cis-regulatory variation, gene expression, and phenotypic outcomes."
- **Evidence pointer** Figure 6, Results section "Genetic variation affects TF-binding potential in loci associated with phenotypic traits", Methods section "Model validation"
- **Concern** The STARR-seq validation is described with insufficient quantitative detail. The manuscript states that 340 control and variant enhancer constructs were tested, and reports a significant increase in reporter expression for variants predicting loss of bHLH or bZIP and a significant decrease for WRKY loss, but does not provide effect sizes, confidence intervals, or the number of constructs per TF family. The claim that "variants that cause a gain or loss of TF binding sites impact gene expression" is presented as a general conclusion, but the data shown in Figure 6f appear to be aggregated across all TF families. It is unclear whether the observed effects are driven by a small number of strong outliers. Additionally, the manuscript does not specify how many of the 351 tested pairs showed predicted binding changes, which is critical for understanding the statistical power. The two biological replicates per construct are minimal for a noisy assay like STARR-seq, and no information is provided on technical replication or assay quality controls.
- **Why it matters** The STARR-seq experiment is the primary functional validation of the model's variant effect predictions. Without adequate quantitative reporting, the central claim that the model captures regulatory variants with phenotypic consequences cannot be properly evaluated. This is the key translational claim of the manuscript.
- **Resolution test** Provide per-construct results, effect size distributions, confidence intervals, and a clear statement of how many variants were predicted to change binding and how many showed significant expression changes. Include information on assay reproducibility and quality metrics. If possible, show that the direction of expression change correlates with the predicted gain versus loss of specific TF families.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "20.72% of variants led to a gain or loss of predicted binding sites" among 7364 AraGWAS SNPs, and that this represents a meaningful enrichment of regulatory variants.
- **Evidence pointer** Figure 6a-b, Results section "Genetic variation affects TF-binding potential in loci associated with phenotypic traits", Methods section "Model validation"
- **Concern** The analysis of GWAS variants lacks a proper null model. The authors generated 30 in silico SNPs per site as controls, but the comparison shown in Figure 6b appears to compare the distribution of binding changes between natural SNPs and these random mutations. However, the manuscript does not report whether the 20.72% figure is significantly different from the rate expected under the in silico mutation model. The statement that "more than half of the in silico SNPs resulted in no perturbation" suggests a baseline rate of perturbation, but the statistical comparison between the natural and in silico distributions is not clearly described. Furthermore, the selection of 7364 SNPs from the AraGWAS catalogue is not justified. Were these all SNPs in promoter/terminator regions? How many were in LD with the lead GWAS variant? The manuscript does not address whether the predicted binding changes are enriched in SNPs with stronger GWAS associations.
- **Why it matters** The claim that the model "captures regulatory variants associated with phenotypic traits" depends on demonstrating that predicted binding changes are enriched in trait-associated variants beyond what would be expected by chance. Without a rigorous statistical framework, the 20.72% figure is difficult to interpret.
- **Resolution test** Provide a clear statistical test comparing the rate of predicted binding changes in natural GWAS SNPs versus matched control SNPs, ideally stratified by linkage disequilibrium and distance to the lead variant. Report whether the enrichment is significant and quantify the effect size.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Originality and context
- **Claim pointer** The authors state that "current classification approaches to model TF-DNA binding have developed independent binary classification models per TF" and imply that their multi-label approach is a novel contribution.
- **Evidence pointer** Introduction, Results section "Modelling protein–DNA interactions in A. thaliana"
- **Concern** The manuscript does not adequately position the multi-label approach relative to existing plant regulatory deep learning models. Several recent models, including those for plant cis-regulatory element prediction, have used multi-task or multi-label formulations. The authors should clarify what is specifically novel about their architecture or training strategy. Additionally, the claim that grouping by TF family improves data balance and training efficiency is plausible but not rigorously demonstrated. The comparison in Figure 2d-e between full models and top-k/bottom-k subsets is informative but does not directly show that the multi-label formulation outperforms an ensemble of single-label models.
- **Why it matters** For a Nature Communications submission, the novelty of the computational approach needs to be clearly articulated and demonstrated. If the multi-label formulation is not shown to provide tangible benefits over simpler alternatives, the contribution is incremental.
- **Resolution test** Add a benchmark comparison against single-label models or a per-TF binary classification approach, demonstrating improved performance or efficiency. Clearly state what architectural or training innovations are introduced relative to prior plant regulatory deep learning models.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "the model annotates cistrome-wide TF-binding sites" and that it can be applied to "untargeted DNA binding assays, such as MOA-seq."
- **Evidence pointer** Figure 7a-b, Results section "Model-based peak annotation enables genome-scale annotation from untargeted DNA binding assays"
- **Concern** The MOA-seq annotation results are presented with limited validation. The authors report that the model assigned about 90% of peaks to at least one TF family and correctly assigned about 74% when compared to DAP-seq overlap. However, the comparison is circular to some degree, as the model was trained on DAP-seq data. The manuscript does not report what fraction of MOA-seq peaks had no DAP-seq overlap, and how the model performed on those. Additionally, the Z. mays heat stress analysis is described only briefly. The claim that the model "demonstrates its potential to characterize condition-responsive TF binding" is supported by the binary classifier results in Figure 7d, but the feature importance analysis in Figure 7e is not clearly explained. How were importance scores calculated? What do they represent biologically?
- **Why it matters** The MOA-seq annotation and cross-species transfer are presented as key applications of the model. Without rigorous validation, particularly on peaks without DAP-seq overlap, the utility of the approach for novel annotation is unclear.
- **Resolution test** Provide a more detailed analysis of MOA-seq peaks without DAP-seq overlap, including manual inspection of predicted motifs. For the Z. mays analysis, clarify the feature importance methodology and provide biological interpretation of the top contributing TF families.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors claim that "the model effectively recognised broader TFBS syntax that may represent cis-regulatory modules" based on co-occurrence and perturbation analyses.
- **Evidence pointer** Figure 4, Results section "Sequence context and motif syntax contribute to predicting the binding specificity of different TF families"
- **Concern** The analysis of sequence context and syntax is interesting but the causal claims are not fully supported. The correlation between co-occurrence and MCC (Figure 4d) does not establish that the model is learning syntax. The perturbation analysis of G-box flanking regions is described in Supplementary Methods, which were not available for review. The claim that "BZR is exceptionally difficult to predict by IPM occurrence alone but surprisingly features a high MCC" suggests the model is using context, but the manuscript does not provide a clear mechanistic explanation for why this is the case. The network analysis in Figure 4g is descriptive and the biological significance of the identified co-occurrence patterns is not validated.
- **Why it matters** The claim that the model captures regulatory syntax beyond isolated motifs is a central biological finding. If this is not rigorously demonstrated, the manuscript's contribution to understanding cis-regulatory logic is weakened.
- **Resolution test** Provide experimental or orthogonal validation of at least one predicted co-occurrence or syntax effect. Alternatively, demonstrate that the model's predictions on synthetic sequences with controlled syntax features are consistent with the claimed learning.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity and reproducibility
- **Affected element** Model training details
- **Evidence pointer** Methods section "Model architecture and training strategy"
- **Issue** The manuscript states the model uses "four convolutional blocks, followed by two blocks of fully connected layers" but does not specify kernel sizes, number of filters, pooling strategies, dropout rates, or the total number of parameters. The learning rate is given as 0.002 but no learning rate schedule or batch size is mentioned.
- **Required correction** Provide a complete architecture table or a reference to a public repository with the full model definition. Include all hyperparameters needed for reproduction.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Performance metrics
- **Evidence pointer** Figure 1b, Results section "Modelling protein–DNA interactions in A. thaliana"
- **Issue** The performance metrics (auPR, auROC) are reported as means across 5 models with standard deviations, but the manuscript does not state how many test samples were used for evaluation. The comparison against shuffled controls is described as significant, but the specific p-values are only shown for the Mann-Whitney U test in the figure legend.
- **Required correction** Report the number of test windows, the total number of positive and negative examples, and provide confidence intervals for the performance metrics.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 5
- **Evidence pointer** Figure 5 legend
- **Issue** The UMAP projection and HDBSCAN clustering are described but the parameters used for these algorithms are not provided. The number of clusters (14) is stated but the stability of this clustering solution is not assessed.
- **Required correction** Provide UMAP and HDBSCAN parameters, and include a cluster stability analysis or silhouette scores.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data availability
- **Evidence pointer** Methods section "Data source"
- **Issue** The manuscript states that DAP-seq data were downloaded from PlantCistromeDB, but does not provide accession numbers or version information for the specific datasets used. The Z. mays datasets are mentioned but not described in detail.
- **Required correction** Provide a supplementary table listing all datasets used with accession numbers, and clarify the processing steps for Z. mays data.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Figure 6g
- **Evidence pointer** Figure 6g legend
- **Issue** The figure shows changes in relative promoter strength for GWAS variant constructs associated with days to flowering, but the number of variants tested and the specific loci are not described in the main text. The claim that these are "natural SNPs" is made, but the linkage disequilibrium structure is not discussed.
- **Required correction** Provide a table of the specific variants tested, their genomic locations, and their LD relationships to the reported GWAS lead variants.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The discussion mentions that the model detects only ~8.5% of BZR1 targets in A. thaliana from DAP-seq data, but this statistic is not clearly contextualised. It is unclear whether this is a limitation of the training data or a reflection of the model's performance.
- **Required correction** Clarify whether this 8.5% figure refers to the proportion of known BZR1 targets that are captured by the model, and discuss the implications for the model's utility.

## Risk / unsupported claims
- The claim that the model "captures regulatory variants associated with phenotypic traits" is not fully supported by the data presented in the main text. The STARR-seq validation is described with insufficient quantitative detail, and the statistical framework for the GWAS variant analysis is not clearly described.
- The claim that the model "effectively recognised broader TFBS syntax" is based on correlational analyses and perturbation studies described in unavailable supplementary methods. The causal interpretation is not fully established.
- The claim that the model can be applied to "untargeted DNA binding assays" across species is supported by the Z. mays analysis, but the validation is limited and the feature importance methodology is not clearly explained.
- The performance comparison against shuffled controls demonstrates that the model captures sequence information, but the manuscript does not benchmark against simpler motif-scanning approaches or single-label models, making it difficult to assess the added value of the multi-label deep learning approach.
- The biological significance of the 14 regulatory clusters is asserted but not experimentally validated. The claim that these clusters represent "a data-driven regulatory gene ontology" is premature without functional validation.