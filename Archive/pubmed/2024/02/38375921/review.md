## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and data availability statements. No figures, tables, or supplementary materials were provided.
- **Assessment boundary** Scientific soundness, methodological clarity, validity of claims relative to presented evidence, and suitability for a high-impact generalist or specialized readership. No assessment of code correctness or reproducibility beyond what is described in text.
- **Shared manuscript claim summary** The authors present MIXBend, a self-supervised pre-trained bimodal framework integrating DNA sequence (via DNABERT-6) and physicochemical features (one-hot, NCP, DPP, positional) with a k-mer sequence-physicochemistry matching module and self-attention fusion, to predict DNA bendability from 50 bp sequences. They report superior performance over DNASCycP, DeepBend, and BendNet on Random and Nucleosomal datasets, demonstrate generalizability on independent ChrV and Tiling datasets, and use attention-based motif extraction to identify known and novel bendability-associated motifs, including analysis of super-enhancer regions in the human genome.
- **Visible evidence base** Textual descriptions of results in Sections "Comparison with state-of-the-art methods", "Ablation study", "Evaluation on independent test set", "Analysis of bendability around nucleosome dyads", "MIXBend extracts important motifs influencing bendability", and "Associations between functional elements and bendability in human genome". Figures referenced but not visible: Figures 1–6. Supplementary materials referenced but not provided.
- **Missing materials affecting confidence** All figures, tables, supplementary data, and the actual numerical results (e.g., R² values, correlation coefficients, p-values, confidence intervals) are not available. This substantially limits verification of quantitative claims and visual evidence of motif logos, occupancy plots, and super-enhancer analyses.

## Reviewer
- **Overall assessment** The manuscript addresses a timely and relevant problem: predicting DNA bendability using modern deep learning architectures, specifically leveraging pre-trained language models and multimodal feature integration. The methodological concept is interesting and the application to super-enhancer analysis adds biological relevance. However, the current evidence base is insufficient to fully evaluate the claims. Key quantitative results are only described in text without visible figures or tables, and several methodological details (e.g., exact architecture dimensions, hyperparameter choices, statistical significance testing) are missing or vague. The claim of "first-of-its-kind" application to super-enhancers is strong and requires more careful contextualization against existing literature. The manuscript would benefit from clearer reporting of experimental setup, error bars, and statistical tests.
- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on DNA sequence-function prediction, particularly those interested in applying large language models to genomics. Researchers studying DNA mechanics, nucleosome positioning, chromatin organization, and transcriptional regulation would also find the biological applications relevant. The super-enhancer analysis may attract researchers in gene regulation and epigenomics.
- **Major strengths** 1) Novel integration of bimodal representations (sequence + physicochemical) within a pre-trained language model framework for bendability prediction. 2) Use of contrastive learning for modality alignment at the k-mer level is a thoughtful contribution. 3) The application to identify bendability motifs and link them to super-enhancer regions provides biological interpretability beyond mere prediction. 4) The authors address generalizability through independent test sets, which strengthens the practical utility claim.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** "MIXBend exhibits outstanding performance with the highest average R2 and Pearson correlation values in comparison to other methods" with specific percentage improvements over DNASCycP, DeepBend, and BendNet.
  - **Evidence pointer** Section "Comparison with state-of-the-art methods", Figure 2 (not visible)
  - **Concern** The quantitative performance claims are presented without visible figures or tables. The percentage improvements are stated but no absolute R² or correlation values, standard deviations, or statistical significance tests are reported. Without these, it is impossible to assess whether the improvements are meaningful or within noise.
  - **Why it matters** The central claim of the manuscript is that MIXBend outperforms existing methods. If the numerical evidence is not transparently presented with appropriate statistical rigor, the core contribution cannot be validated.
  - **Resolution test** Provide the actual R² and Pearson correlation values with standard deviations across cross-validation folds, and include statistical significance tests (e.g., paired t-test or Wilcoxon) comparing MIXBend to each baseline.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Methodological clarity
  - **Claim pointer** The description of the modality alignment module and the self-attention fusion layer.
  - **Evidence pointer** Sections "Modality alignment" and "Bendability prediction"
  - **Concern** The mathematical formulations for the contrastive loss and the self-attention fusion are referenced but not fully written out. The text mentions equations but they are not included in the provided material. Additionally, the choice of temperature parameter τ = 0.07 is stated but no sensitivity analysis is provided. The architecture of the physicochemical encoder (CNN layers, kernel sizes, number of filters) is described only vaguely.
  - **Why it matters** Reproducibility is a cornerstone of computational biology research. Without complete architectural details and loss function definitions, other researchers cannot implement or build upon MIXBend.
  - **Resolution test** Include full equations for the contrastive loss and self-attention mechanism, provide a table of all hyperparameters, and describe the CNN architecture in sufficient detail (layer sizes, activations, pooling, etc.).
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Biological interpretation
  - **Claim pointer** "MIXBend discovers significant bendability fluctuations within super-enhancer regions and transcription factors binding sites in the human genome."
  - **Evidence pointer** Section "Associations between functional elements and bendability in human genome", Figure 6 (not visible)
  - **Concern** The biological analysis of super-enhancers is described qualitatively. No statistical framework is described for determining "significant" fluctuations. The comparison between super-enhancer regions and control regions (if any) is not described. The claim that "DNA with TF binding sites exhibited variable bendability, either increased or decreased, specific to certain chromosomes" is vague and lacks quantitative support.
  - **Why it matters** The biological relevance of the model is a key selling point. If the super-enhancer and TF binding site analyses are not rigorously quantified, the biological conclusions are weakened.
  - **Resolution test** Describe the statistical tests used to assess bendability differences, include effect sizes and confidence intervals, and provide appropriate controls (e.g., matched random genomic regions).
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Novelty contextualization
  - **Claim pointer** "This is the first-of-its-kind study to explore DNA bendability and genomic packaging in the context of super-enhancers within the human genome."
  - **Evidence pointer** Section "Discussion"
  - **Concern** The claim of being "first-of-its-kind" is strong and requires a more thorough literature review to substantiate. There may be prior studies examining DNA bendability in regulatory regions, even if not using the same computational approach. The authors should temper this claim or provide a more comprehensive comparison with existing literature.
  - **Why it matters** Overclaiming novelty can undermine credibility. A more nuanced statement acknowledging prior work on DNA mechanics in regulatory regions would be more appropriate.
  - **Resolution test** Revise the claim to be more specific (e.g., "first to apply a bimodal pre-trained language model approach to study bendability in super-enhancers") and cite relevant prior work on DNA bendability in regulatory elements.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Data preprocessing description
  - **Evidence pointer** Section "Data preprocessing"
  - **Issue** The description of how DPP values are computed for each nucleotide using a sliding window is unclear. The equation referenced is not fully explained.
  - **Required correction** Provide a clear step-by-step description of how the DPP embedding is constructed, including how boundary nucleotides are handled.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Ablation study
  - **Evidence pointer** Section "Ablation study"
  - **Issue** The ablation study is described but the specific variants tested (e.g., "Arch. only", "w/LSA") are not fully defined. It is unclear what "Arch. only" means in terms of which components are removed.
  - **Required correction** Clearly define each ablation variant and what component is removed or replaced.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Non-regressive sequence analysis
  - **Evidence pointer** Section "Evaluation on independent test set"
  - **Issue** The identification of "non-regressive sequences" using a threshold of >1 for absolute difference is arbitrary. No justification is provided for this threshold.
  - **Required correction** Justify the threshold choice or use a more principled approach (e.g., percentile-based or model-based outlier detection).
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Discussion section
  - **Evidence pointer** Section "Discussion"
  - **Issue** The statement "Antibody binding to GGCTGT might lead to global repression of gene transcription, subsequently impeding the progression of cancer" is speculative and not supported by any experimental evidence presented in the manuscript.
  - **Required correction** Either remove this speculative statement or clearly label it as a hypothesis requiring experimental validation.
- **Technical failings that need to be addressed before the case is established** 1) Missing equations for the contrastive loss and self-attention fusion (R1-M2). 2) Lack of statistical significance testing for performance comparisons (R1-M1). 3) Incomplete description of the physicochemical encoder architecture (R1-M2). 4) No description of hyperparameter tuning or sensitivity analysis (R1-M2). 5) The claim of "significant" bendability fluctuations in super-enhancers lacks statistical backing (R1-M3).
- **Assessment against Nature-style criteria**  
  *Originality*: The combination of pre-trained language models with physicochemical features for bendability prediction is a novel contribution, though the individual components (DNABERT, CNNs, contrastive learning) are established. The application to super-enhancer analysis adds a new dimension.  
  *Scientific importance*: DNA bendability is a fundamental biophysical property with implications for gene regulation and chromatin biology. Improved prediction tools and biological insights could be valuable to the community. However, the incremental improvement over existing methods needs to be clearly demonstrated.  
  *Interdisciplinary readership*: The work bridges machine learning and molecular biology, which could appeal to both computational and experimental researchers. However, the manuscript assumes familiarity with both deep learning architectures and DNA biophysics, which may limit accessibility.  
  *Technical soundness*: The overall approach is reasonable, but the lack of complete methodological details and statistical rigor prevents full assessment. The ablation study is a positive step but needs clearer definitions.  
  *Readability for nonspecialists*: The abstract is accessible, but the methods section is dense and would benefit from clearer explanations of the architecture and training procedure. The biological interpretations are described in a way that is understandable to a biology audience.
- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the application domain is relevant, but the manuscript in its current form does not provide sufficient evidence to fully establish the claims. The authors must provide complete methodological details, transparent quantitative results with statistical tests, and a more rigorous biological analysis. Once these are addressed, the manuscript could be suitable for publication in a specialized journal such as Nucleic Acids Research.

## Risk / unsupported claims
- The claim of "outstanding performance" and specific percentage improvements over baselines cannot be verified without visible figures or tables.
- The claim of "significant bendability fluctuations" in super-enhancer regions is not supported by any statistical analysis described in the text.
- The claim of being "first-of-its-kind" in exploring bendability in super-enhancers is not substantiated with a comprehensive literature review.
- The statement that "MIXBend is unable to predict bendability for sequences of longer or shorter lengths" is presented as a limitation but no analysis is provided to show how performance degrades with sequence length variation.
- The identification of "novel motifs" is claimed but the novelty is not established against existing motif databases beyond the TOMTOM comparison, which is not described in detail.
- The functional significance of the identified motifs (e.g., GGCTGT as a potential cancer drug target) is speculative and not supported by experimental evidence.