## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, data availability, code availability)
- **Assessment boundary** Scientific claims, methodological soundness, evidence quality, and reproducibility as presented in the provided manuscript text. No external data or code was accessed.
- **Shared manuscript claim summary** The authors present Chromnitron, a multimodal foundation model integrating DNA sequence, chromatin accessibility, and protein amino acid sequence embeddings to predict genome-wide binding landscapes of chromatin-associated proteins (CAPs) across cell types, including unseen cell types. The model is claimed to achieve high prediction accuracy, learn interpretable binding principles via in silico perturbation experiments, enable discovery of novel regulators of T cell exhaustion (ZNF865, ZNF766), and map dynamic CAP binding during neurodevelopment.
- **Visible evidence base** Abstract, full introduction, full results section, full discussion, full methods section, data availability statement, code availability statement. No figures, tables, or supplementary materials were provided.
- **Missing materials affecting confidence** All figures, tables, supplementary figures, supplementary tables, and supplementary files are absent. This includes the main results figures (Fig. 1–6), all performance metrics plots, clustering results, perturbation heatmaps, CRISPR screen results, and RNA-seq analyses. Without these, quantitative claims cannot be independently verified.

## Reviewer
- **Overall assessment** The manuscript presents an ambitious and potentially impactful computational framework for predicting CAP binding across cell types. The multimodal architecture is conceptually novel and the application to T cell exhaustion and neurodevelopment is timely. However, the provided text alone is insufficient to evaluate the core claims. Key quantitative results, model performance comparisons, and validation experiments are described only in text without supporting figures or tables. The methods section is detailed but several critical implementation choices (e.g., data splitting, baseline comparisons, statistical significance testing) are not fully specified. The biological validations, particularly the CRISPR screen and RNA-seq experiments, are described with minimal detail and no results are shown. The manuscript would benefit from clearer articulation of novelty relative to existing models and more rigorous statistical evaluation.
- **Who would be interested in the results, and why** Computational biologists and machine learning researchers working on regulatory genomics, transcription factor binding prediction, and foundation models for genomics. Also, experimental biologists studying gene regulation, chromatin biology, T cell exhaustion, and neurodevelopment, who could use the model for hypothesis generation and prioritization of candidate regulators.
- **Major strengths** 1) The multimodal integration of DNA sequence, chromatin accessibility, and protein sequence is a conceptually strong and timely approach. 2) The model is designed for generalization to unseen cell types, addressing a key limitation of existing methods. 3) The application to T cell exhaustion and neurodevelopment demonstrates potential biological utility. 4) The methods section provides substantial technical detail, including data preprocessing, model architecture, and perturbation strategies.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (missing quantitative results), R1-M2 (insufficient baseline comparisons), R1-M3 (incomplete validation details), R1-M4 (computational cost not reported), R1-M5 (data leakage risk not addressed).
- **Assessment against Nature-style criteria**  
  *Originality*: The multimodal approach combining three distinct data modalities for CAP binding prediction is original and extends beyond existing unimodal or dual-modality models. However, the novelty relative to recent foundation models in genomics (e.g., Enformer, Borzoi) needs clearer articulation.  
  *Scientific importance*: If validated, the model could significantly advance the field by enabling genome-wide CAP binding prediction in primary cells and rare cell types, with implications for understanding gene regulation and disease. The T cell exhaustion findings are potentially important but require stronger experimental support.  
  *Interdisciplinary readership*: The work bridges machine learning, genomics, and cell biology, and would appeal to a broad readership. However, the presentation assumes significant familiarity with both deep learning and chromatin biology, which may limit accessibility.  
  *Technical soundness*: The methods are described in detail, but the absence of quantitative results and figures prevents assessment of technical soundness. Several methodological choices (e.g., data splitting, baseline selection) are not fully justified.  
  *Readability for nonspecialists*: The abstract and introduction are accessible, but the results and methods sections are dense and would be challenging for nonspecialists. The manuscript would benefit from clearer explanations of key concepts and more intuitive figure descriptions.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential, but the absence of figures, tables, and quantitative results makes it impossible to assess whether the core claims are supported. Major revisions and resubmission with full results are required.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Evidence sufficiency  
- **Claim pointer** The manuscript claims "accurate prediction of CAP binding landscapes across hundreds of proteins in unseen cell types" and "high-fidelity prediction performance" (Abstract, Results).  
- **Evidence pointer** Results section, Figures 2a–i, Supplementary Figures 4–9 (not provided)  
- **Concern** The central quantitative claims of the paper are not verifiable from the provided text. The results section describes performance metrics (e.g., Pearson's correlation, AUROC, AUPR) and comparisons to baselines, but no actual numbers, plots, or statistical tests are shown. The figures and supplementary materials that would contain this evidence are not included.  
- **Why it matters** Without quantitative results, the reader cannot assess whether the model actually achieves the claimed accuracy, how it compares to existing methods, or whether the performance is sufficient for the proposed biological applications. This is the core evidence needed to establish the manuscript's central claim.  
- **Resolution test** Provide all figures and supplementary figures with quantitative performance metrics, including distributions of correlation coefficients across CAPs, comparisons to baselines with statistical significance tests, and performance stratified by cell type and chromatin state.

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Comparative validity  
- **Claim pointer** The manuscript states "Chromnitron substantially outperforms both methods across various metrics" when compared to maxATAC and Enformer (Results).  
- **Evidence pointer** Results section, Figures 2h–i, Supplementary Figures 7–9 (not provided)  
- **Concern** The comparison to existing methods is described only qualitatively. No details are given on how baselines were configured, whether hyperparameters were optimized, whether the same training/validation splits were used, or whether differences are statistically significant. The choice of baselines is also limited; other relevant methods (e.g., BPNet, DeepSEA, Basenji) are not mentioned.  
- **Why it matters** A fair and rigorous comparison to existing methods is essential to establish the added value of the multimodal approach. Without this, the claim of superiority is unsupported.  
- **Resolution test** Provide detailed baseline descriptions, including model versions, hyperparameters, training procedures, and evaluation protocols. Show performance distributions and statistical significance tests (e.g., paired tests across CAPs or cell types). Justify the choice of baselines and consider adding additional state-of-the-art methods.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Validation rigor  
- **Claim pointer** The manuscript claims "discovered ZNF865 and ZNF766 as novel regulators of the T cell exhaustion process" and that "knockout ZNF865 reduced TOX expression level" and "ZNF766 may play an important role in regulating T cell exhaustion."  
- **Evidence pointer** Results section, Figures 4i–j, 5f–i, Supplementary Figures 12–14 (not provided)  
- **Concern** The experimental validation is described only in text. No data are shown for the CRISPR screen, flow cytometry, or RNA-seq experiments. The number of biological replicates, effect sizes, statistical significance, and controls are not reported. The claim that ZNF865 knockout "reduced TOX expression" is presented without quantitative data. The CRISPR screen results are described as identifying ZNF766 as "the most prominent regulator" but no screen statistics or hit criteria are given.  
- **Why it matters** The biological discoveries are a key part of the paper's impact. Without rigorous experimental evidence, these claims cannot be evaluated. The lack of detail on experimental design and statistics raises concerns about reproducibility.  
- **Resolution test** Provide full experimental results, including flow cytometry plots, CRISPR screen rankings with statistical scores, RNA-seq differential expression results, and appropriate statistical tests. Specify the number of replicates, controls, and criteria for hit selection.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** No  
- **Axis** Reproducibility  
- **Claim pointer** The manuscript describes the model architecture and training procedures in the Methods section.  
- **Evidence pointer** Methods section, "Model architecture", "Model pre-training and fine-tuning"  
- **Concern** The computational cost of the model is reported (1,200 GPU hours for pre-training, 6,000 GPU hours for fine-tuning), but the total memory requirements, inference time, and scalability to larger genomes or more cell types are not discussed. The model uses a 3-billion-parameter ESM2 model for protein embedding, which is computationally expensive; the manuscript does not discuss whether this is a practical limitation for broader use.  
- **Why it matters** For a foundation model intended for community use, practical considerations such as inference speed, memory footprint, and hardware requirements are important for reproducibility and adoption.  
- **Resolution test** Report inference time and memory usage for a typical prediction task. Discuss the feasibility of running the model on standard hardware and consider providing a lighter-weight version or precomputed embeddings.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** No  
- **Axis** Data leakage  
- **Claim pointer** The manuscript claims the model "can generalize to unseen cell types" and evaluates on leave-out cell types.  
- **Evidence pointer** Methods section, "Genomic data collection", "Prediction performance evaluation"  
- **Concern** The manuscript does not explicitly describe how cell types were split between training and evaluation. It is unclear whether the five cell types used for training are representative of the diversity of cell types the model is expected to generalize to, and whether any cell type-specific biases in the training data could inflate performance estimates. The leave-out chromosome approach is described, but the cell type splitting strategy is not.  
- **Why it matters** If cell types are not properly separated during training, the model's generalization claims could be overstated. Data leakage between training and evaluation cell types would invalidate the central claim of generalization.  
- **Resolution test** Clearly describe the cell type splitting strategy, including the number of cell types used for training versus evaluation, and whether any cell types were completely held out. Discuss potential biases and how they were addressed.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Abstract  
- **Evidence pointer** Abstract  
- **Issue** The abstract states the model "decodes the global binding landscape" but does not specify the number of CAPs or cell types evaluated, nor the key performance metrics.  
- **Required correction** Include key quantitative results in the abstract, such as median Pearson's correlation across CAPs and the number of cell types tested.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Terminology  
- **Affected element** Introduction  
- **Evidence pointer** Introduction, paragraph 1  
- **Issue** The term "chromatin-associated proteins" is used broadly, but the manuscript focuses primarily on transcription factors. The distinction between CAPs and TFs should be clarified.  
- **Required correction** Define the scope of CAPs covered in this study and clarify whether co-factors and chromatin regulators are included in the training and evaluation.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Statistical rigor  
- **Affected element** Results, "High-quality and cross-modality CAP binding predictions"  
- **Evidence pointer** Results section, Figure 2c (not provided)  
- **Issue** The manuscript reports Pearson's correlation coefficients but does not describe how confidence intervals or significance are calculated.  
- **Required correction** Report confidence intervals or standard errors for performance metrics and describe the statistical methods used.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Reproducibility  
- **Affected element** Methods, "Genomic data preprocessing with Chrom2Vec"  
- **Evidence pointer** Methods section  
- **Issue** The description of Chrom2Vec is detailed but the specific versions of tools and parameters used (e.g., alignment software, peak caller, genome build) are not fully specified.  
- **Required correction** Provide a complete list of software versions, parameters, and genome build used in the preprocessing pipeline.

- **Concern ID** R1-m5  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Results, "Multimodal in silico perturbations reveal principles of CAP binding"  
- **Evidence pointer** Results section, Figure 3 (not provided)  
- **Issue** The in silico mutagenesis results are described but the methodology for defining "impact motifs" and clustering them is not fully explained in the main text.  
- **Required correction** Provide a more detailed description of the impact motif definition and clustering methodology, or refer readers to the methods section with clear cross-references.

- **Concern ID** R1-m6  
- **Severity** Minor  
- **Axis** Interpretation  
- **Affected element** Discussion  
- **Evidence pointer** Discussion  
- **Issue** The discussion claims the model "acts as a prism to transform single chromatin accessibility signal into a spectrum of functional genomics data" but does not discuss limitations of the approach, such as potential biases in training data or failure modes.  
- **Required correction** Add a limitations paragraph discussing potential sources of bias, model failure modes, and areas where experimental validation is still needed.

## Risk / unsupported claims
- The claim of "high-fidelity prediction performance" and "accurate prediction" across hundreds of CAPs is unsupported without quantitative results.
- The claim that Chromnitron "substantially outperforms" maxATAC and Enformer is unsupported without detailed comparisons and statistical tests.
- The biological claims regarding ZNF865 and ZNF766 as regulators of T cell exhaustion are unsupported without experimental data.
- The claim that the model "can predict the global CAP binding landscape" during neurodevelopment is unsupported without results from the developmental analysis.
- The claim that in silico perturbation experiments "reveal principles of CAP binding" is partially supported by text but lacks quantitative evidence.
- The claim that Chromnitron "faithfully captures different CAP binding modes" at low-accessibility regions is unsupported without figures showing these comparisons.