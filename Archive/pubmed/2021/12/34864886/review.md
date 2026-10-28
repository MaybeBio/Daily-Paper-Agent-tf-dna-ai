## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose TFCNN, a convolutional neural network model that uses transcription factor (TF) cobinding signals around target genes to identify gene expression levels in GM12878 and K562 cell lines. They report identification of six TF modules per cell line, high predictive performance (AUC 0.975 and 0.976), superiority over SVM and LDA baselines, and biological interpretations regarding TF combinatorial regulation.
- **Visible evidence base** Abstract text only; no quantitative details, model architecture descriptions, dataset specifications, or validation procedures are available
- **Missing materials affecting confidence** Full methods, model architecture, hyperparameters, training and test data splits, cross-validation strategy, baseline model configurations, feature definitions, statistical significance tests, and all figures and tables

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting application of deep learning to TF cobinding-based gene expression prediction. However, the current evidence base is insufficient to evaluate the technical soundness, reproducibility, or validity of the biological interpretations. The reported AUC values and comparative claims cannot be assessed without methodological details and statistical context. The biological conclusions, while plausible, are stated without supporting quantitative evidence.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on gene regulatory networks, TF binding analysis, and deep learning applications in genomics. Researchers studying combinatorial TF regulation and enhancer-promoter interactions may also find the approach relevant. The potential to infer gene expression from TF binding patterns could interest those developing predictive models for regulatory genomics.
- **Major strengths** The problem is well-motivated and addresses a genuine gap in systematically linking cooperative TF binding to gene expression. The use of deep learning to capture nonlinear combinatorial TF interactions is a reasonable methodological choice. The comparison against classical machine learning baselines (SVM, LDA) is appropriate for demonstrating added value. The focus on two well-characterized cell lines (GM12878, K562) provides a concrete testbed.
- **Major Concerns**  
  - **Concern ID** R1-M1  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness  
  - **Claim pointer** The TFCNN model achieved a good prediction performance for gene expression with average AUC of 0.975 and 0.976 in GM12878 and K562 cell lines, respectively.  
  - **Evidence pointer** Abstract, results section; location not provided  
  - **Concern** The abstract reports AUC values without any information on the prediction task definition (binary classification of high vs. low expression?), the number of genes used, the train/test split strategy, cross-validation scheme, or the variance across folds. Without these details, the reported performance cannot be interpreted or reproduced.  
  - **Why it matters** AUC values are meaningless without knowing the class balance, the threshold used to define expression levels, and whether performance is evaluated on held-out chromosomes or genes. Overlapping training and test sets can inflate AUC substantially in genomic prediction tasks.  
  - **Resolution test** Provide the full experimental setup including task definition, dataset size, split strategy, cross-validation details, and per-fold AUC distributions. Show that performance generalizes to held-out chromosomes or genomic regions not seen during training.

  - **Concern ID** R1-M2  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Technical soundness  
  - **Claim pointer** The TFCNN model outperformed the prediction models based on SVM and LDA.  
  - **Evidence pointer** Abstract, comparison section; location not provided  
  - **Concern** No details are given on how SVM and LDA baselines were configured, what features they used, whether hyperparameters were tuned, or whether the same train/test splits were used. Without this information, the comparison may be unfair or uninformative.  
  - **Why it matters** A deep learning model will typically outperform poorly tuned classical baselines. The claim of superiority is only meaningful if baselines are optimized to a comparable standard and evaluated under identical conditions.  
  - **Resolution test** Describe baseline model configurations, feature representations, hyperparameter tuning procedures, and statistical significance testing (e.g., paired tests across folds) for the performance differences.

  - **Concern ID** R1-M3  
  - **Severity** Major  
  - **Blocking** Yes  
  - **Axis** Biological interpretation  
  - **Claim pointer** The abundant binding of regulatory TFs dominates expression of target genes, while the cooperative interaction between TFs has a subtle regulatory effect. Gene expression could be regulated by different TF combinations in a nonlinear way.  
  - **Evidence pointer** Abstract, further analysis section; location not provided  
  - **Concern** These biological conclusions are stated without any supporting quantitative evidence. No effect sizes, statistical tests, or model interpretation analyses (e.g., feature importance, ablation studies) are described. The link between model performance and these biological claims is not established.  
  - **Why it matters** The abstract implies that the model provides biological insight, but predictive performance alone does not demonstrate mechanistic understanding. Without explicit analyses connecting model behavior to TF binding abundance or interaction patterns, these claims are speculative.  
  - **Resolution test** Provide ablation studies removing individual TF modules, feature importance analyses, or perturbation experiments showing that model predictions depend on specific TF combinations. Include statistical tests for the dominance vs. subtle effect distinction.

  - **Concern ID** R1-M4  
  - **Severity** Major  
  - **Blocking** No  
  - **Axis** Reproducibility  
  - **Claim pointer** We identified six TF modules associated with gene expression in each cell line.  
  - **Evidence pointer** Abstract, results section; location not provided  
  - **Concern** The method for identifying TF modules is not described. It is unclear whether these modules are derived from correlation analysis, clustering, or network inference, and how stability or significance was assessed.  
  - **Why it matters** The TF modules are a central component of the model input. Without a clear definition of how modules are constructed and validated, the entire modeling pipeline is not reproducible.  
  - **Resolution test** Describe the module identification algorithm, criteria for module membership, and any stability or significance testing. Provide the list of TFs in each module for both cell lines.

- **Minor Comments**  
  - **Concern ID** R1-m1  
  - **Severity** Minor  
  - **Axis** Clarity  
  - **Affected element** Model name and description  
  - **Evidence pointer** Abstract, methods description; location not provided  
  - **Issue** The abstract states that a convolutional neural network model called TFCNN was constructed but does not describe the input representation, network architecture, or how TF cobinding signals are encoded.  
  - **Required correction** Provide a brief description of the input feature representation and network architecture in the abstract or indicate where full details are available.

  - **Concern ID** R1-m2  
  - **Severity** Minor  
  - **Axis** Statistical reporting  
  - **Affected element** Performance metrics  
  - **Evidence pointer** Abstract, results section; location not provided  
  - **Issue** The abstract reports average AUC values but does not provide standard deviations, confidence intervals, or the number of replicates.  
  - **Required correction** Report variance measures and the number of independent evaluations.

  - **Concern ID** R1-m3  
  - **Severity** Minor  
  - **Axis** Generalizability  
  - **Affected element** Cell line scope  
  - **Evidence pointer** Abstract, results section; location not provided  
  - **Issue** The model is evaluated only in GM12878 and K562 cell lines. It is unclear whether the approach generalizes to other cell types or tissues.  
  - **Required correction** Acknowledge this limitation explicitly and discuss potential for cross-cell-type transfer.

  - **Concern ID** R1-m4  
  - **Severity** Minor  
  - **Axis** Terminology  
  - **Affected element** "Cobinding transcription factor signals"  
  - **Evidence pointer** Title and abstract; location not provided  
  - **Issue** The term "cobinding signals" is not defined. It is unclear whether this refers to ChIP-seq peak overlaps, co-occurrence frequencies, or some other quantitative measure.  
  - **Required correction** Define the term precisely in the abstract or introduction.

## Risk / unsupported claims
- The claim that TFCNN outperforms SVM and LDA is unsupported without baseline configuration details and statistical testing.
- The biological interpretation that abundant TF binding dominates expression while cooperative interactions have subtle effects is unsupported by any presented quantitative analysis.
- The claim that gene expression is regulated by different TF combinations in a nonlinear way is presented as a finding but no evidence linking model behavior to this conclusion is provided.
- The identification of six TF modules per cell line is unverifiable without methodological description.
- The reported AUC values cannot be interpreted without task definition, dataset details, and validation strategy.
- The generalizability of the model beyond GM12878 and K562 is not addressed and cannot be assessed from the abstract.