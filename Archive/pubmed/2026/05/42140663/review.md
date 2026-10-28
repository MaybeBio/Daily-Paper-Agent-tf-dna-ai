## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors propose that TF binding profiles at promoters, encoded as "TF sequence," constitute a "TF regulatory code" that complements the cis-regulatory code. They introduce a deep learning model, DeepTF, which predicts gene expression from TF sequence with high accuracy (AUROC = 0.97) and cross-cell-line transferability (AUROC > 0.90). Model interpretation is claimed to reveal TF regulatory grammar linked to gene expression.
- **Visible evidence base** Abstract text only; no quantitative details beyond AUROC values, no dataset descriptions, no model architecture, no baseline comparisons, no interpretation methodology
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, supplementary data, model code, dataset specifications, baseline definitions, statistical analyses, and cross-validation details

## Reviewer
- **Overall assessment** The abstract presents a potentially interesting concept, namely a TF-centric regulatory code for gene expression prediction, and reports strong predictive performance. However, the evidence provided is insufficient to evaluate the validity, novelty, or robustness of the claims. Key methodological details, baseline comparisons, and biological validation are absent. The concept of a "TF regulatory code" is not clearly distinguished from existing cis-regulatory models, and the claim that it is "better suited" for linking TF binding to expression is unsupported by the supplied material.
- **Who would be interested in the results, and why** Computational biologists and machine learning researchers working on gene expression prediction, regulatory genomics, and transcription factor biology would be interested. The promise of a simplified, interpretable model for expression prediction from TF binding profiles could appeal to those studying promoter architecture and transcriptional regulation. Clinicians or researchers using expression prediction for disease modeling might also find relevance, though this is not stated in the abstract.
- **Major strengths** The abstract addresses a recognized gap, namely the underemphasis on TF regulatory features relative to cis-regulatory elements. The reported AUROC values suggest high predictive performance, and the cross-cell-line validation indicates potential generalizability. The focus on model interpretability is commendable, as it aims to provide biological insights rather than purely predictive output.
- **Major Concerns**  
  - R1-M1  
  - R1-M2  
  - R1-M3  
  - R1-M4  
  - R1-M5
- **Minor Comments**  
  - R1-m1  
  - R1-m2  
  - R1-m3  
  - R1-m4
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5
- **Assessment against Nature-style criteria**  
  - Originality: The concept of a "TF regulatory code" is presented as novel, but the abstract does not sufficiently differentiate it from existing cis-regulatory code frameworks. The idea of encoding TF binding as sequence is not clearly original, as similar approaches exist in the literature. Originality is therefore not established from the supplied material.  
  - Scientific importance: If validated, the work could have broad implications for understanding transcriptional regulation and improving expression prediction. However, the abstract does not demonstrate biological or clinical impact beyond performance metrics. Importance is plausible but unproven.  
  - Interdisciplinary readership: The topic bridges machine learning and molecular biology, which could attract a broad audience. However, the abstract lacks sufficient context for nonspecialists to grasp the significance of the "TF regulatory code" or the technical novelty of DeepTF.  
  - Technical soundness: Cannot be assessed. No methods, data, or statistical details are provided. The AUROC values are reported without confidence intervals, baseline comparisons, or external validation beyond one cross-cell-line test.  
  - Readability for nonspecialists: The abstract is generally clear but uses jargon such as "TF sequence" and "regulatory grammar" without definition. The distinction between cis-regulatory and TF regulatory codes is not explained sufficiently for a general reader.
- **Recommendation posture** Currently not established from the provided evidence. The abstract is intriguing but lacks the technical and biological detail required to assess the validity of the claims. A supportive posture would require access to the full manuscript and resolution of the major concerns.

### Major Concerns

- **Concern ID** R1-M1  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** "DeepTF is able to predict gene expression with high accuracy (AUROC = 0.97)"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract reports an AUROC of 0.97 for gene expression prediction but provides no details on the dataset, the definition of the prediction task (e.g., binary classification of high versus low expression, regression, or multi-class), the number of samples, the train-test split, or the evaluation protocol. Without this information, the performance claim cannot be interpreted or reproduced.  
- **Why it matters** AUROC is a threshold-independent metric for binary classification, but its meaning depends entirely on the task definition and class balance. A high AUROC on an easy or imbalanced task would not indicate genuine predictive power. The absence of task specification undermines the core claim of the study.  
- **Resolution test** Provide a clear description of the prediction task, dataset size and composition, class definitions, and evaluation protocol. Report AUROC with confidence intervals and compare against appropriate baselines (e.g., sequence-based models, random features, or cis-regulatory code models).

- **Concern ID** R1-M2  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness  
- **Claim pointer** "Cross-cell-line validation (AUROC > 0.90) further confirms the model's transferability"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract states that cross-cell-line validation yields AUROC > 0.90, but it does not specify which cell lines were used for training and testing, how many cell lines were included, or whether the validation was performed in a strictly held-out setting. Transferability claims require careful control for confounding factors such as shared genomic features or technical batch effects.  
- **Why it matters** Transferability is a key strength claimed by the authors, but without details on the validation design, the result could reflect trivial similarities between cell lines rather than genuine generalization of the learned regulatory code.  
- **Resolution test** Describe the cross-cell-line validation protocol, including the number of cell lines, the training and testing splits, and any measures taken to avoid data leakage. Report performance per cell line and discuss potential confounders.

- **Concern ID** R1-M3  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Originality and conceptual clarity  
- **Claim pointer** "We systematically analyze 13 TF binding profiles associated with transcription initiation and encode them as TF sequence to explore the TF regulatory code"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The concept of a "TF regulatory code" is introduced but not defined in a way that distinguishes it from the cis-regulatory code. The abstract states that CREs alone are insufficient to determine TF binding, but it does not explain how the TF sequence encoding captures information beyond the cis-regulatory sequence. The novelty of this framing is unclear.  
- **Why it matters** If the TF regulatory code is simply a re-encoding of TF binding signals that are themselves determined by cis-regulatory elements, the conceptual advance may be limited. The authors need to clarify what new biological or predictive information the TF code provides.  
- **Resolution test** Provide a formal definition of the TF regulatory code, explain how it differs from cis-regulatory code, and present evidence that TF sequence encoding captures information not already contained in the underlying genomic sequence.

- **Concern ID** R1-M4  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Technical soundness and interpretability  
- **Claim pointer** "Model interpretation reveals DeepTF successfully captures the TF regulatory grammar associated with gene expression"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract claims that model interpretation reveals "TF regulatory grammar," but no details are given on the interpretation method (e.g., saliency maps, attention weights, motif analysis) or the specific patterns identified. Without this information, the claim is unverifiable and the biological insight is vague.  
- **Why it matters** Interpretability is a major selling point of the model, but the abstract does not demonstrate that the identified patterns are biologically meaningful or distinct from known TF binding motifs. The claim of capturing "grammar" implies combinatorial rules, which require explicit demonstration.  
- **Resolution test** Describe the interpretation method, present specific examples of identified patterns (e.g., positional preferences, pairwise or higher-order combinations), and validate these patterns against known TF biology or experimental data.

- **Concern ID** R1-M5  
- **Severity** Major  
- **Blocking** Yes  
- **Axis** Comparative evaluation  
- **Claim pointer** "Compared with the cis-regulatory code, our proposed TF regulatory code is better suited for investigating the relationship between TF binding positions or combinatorial patterns and gene expression"  
- **Evidence pointer** Abstract, location not provided  
- **Concern** The abstract makes a comparative claim that the TF regulatory code is "better suited" than the cis-regulatory code, but no comparison is presented. There is no evidence that DeepTF was benchmarked against cis-regulatory code-based models, nor is there any analysis showing that the TF code provides superior biological insight.  
- **Why it matters** A comparative claim requires direct evidence. Without a baseline comparison, the assertion of superiority is unsupported and could mislead readers about the relative merits of the two approaches.  
- **Resolution test** Include a direct comparison of DeepTF against a cis-regulatory code-based model on the same prediction task, and provide a qualitative or quantitative analysis of the biological insights derived from each approach.

### Minor Comments

- **Concern ID** R1-m1  
- **Severity** Minor  
- **Axis** Clarity  
- **Affected element** Definition of "TF sequence"  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The term "TF sequence" is used without definition. It is unclear whether this refers to a concatenation of TF binding scores, a binary presence-absence matrix, or a sequence of TF identities at each position.  
- **Required correction** Define "TF sequence" explicitly in the abstract or methods, including the encoding scheme and the source of TF binding profiles.

- **Concern ID** R1-m2  
- **Severity** Minor  
- **Axis** Completeness  
- **Affected element** Selection of 13 TFs  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The abstract states that 13 TF binding profiles were analyzed but does not justify why these specific TFs were chosen or whether they are representative of the broader TF repertoire.  
- **Required correction** Provide a rationale for the selection of the 13 TFs and discuss potential limitations of this restricted set.

- **Concern ID** R1-m3  
- **Severity** Minor  
- **Axis** Statistical reporting  
- **Affected element** AUROC values  
- **Evidence pointer** Abstract, location not provided  
- **Issue** AUROC values are reported without variance estimates or statistical significance tests. It is unclear whether the performance differences are robust.  
- **Required correction** Report confidence intervals or standard deviations for AUROC values, and include statistical tests where relevant.

- **Concern ID** R1-m4  
- **Severity** Minor  
- **Axis** Readability  
- **Affected element** Terminology  
- **Evidence pointer** Abstract, location not provided  
- **Issue** The phrase "TF regulatory grammar" is evocative but undefined. Nonspecialist readers may not understand what constitutes "grammar" in this context.  
- **Required correction** Define "regulatory grammar" in plain terms, for example, as positional preferences and combinatorial rules of TF binding that influence expression.

## Risk / unsupported claims
- The claim that DeepTF achieves AUROC = 0.97 is unsupported without task definition, dataset details, and evaluation protocol.
- The claim of cross-cell-line transferability (AUROC > 0.90) is unsupported without specification of cell lines and validation design.
- The claim that model interpretation reveals "TF regulatory grammar" is unsupported without description of the interpretation method or identified patterns.
- The comparative claim that the TF regulatory code is "better suited" than the cis-regulatory code is unsupported without direct benchmarking.
- The conceptual distinction between TF regulatory code and cis-regulatory code is not established from the abstract alone.