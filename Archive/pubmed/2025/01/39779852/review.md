## Review setup
- **Input scope** Full manuscript text including abstract, main text, methods, and supplementary information descriptions
- **Assessment boundary** Scientific validity, technical soundness, novelty, and significance of the claims as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present GET (general expression transformer), a foundation model that predicts gene expression from chromatin accessibility and TF motif information across 213 human cell types. The model is claimed to achieve experimental-level accuracy in unseen cell types, generalize across platforms and assays, and enable discovery of regulatory elements, TF–TF interactions, and disease-relevant mechanisms.
- **Visible evidence base** Abstract, main text sections on modelling, generalizability, zero-shot prediction, cis-regulatory element identification, TF interaction discovery, and case studies; methods sections on data processing, model architecture, training, interpretation, and structural analysis; figure legends for Figs. 1–5 and Extended Data Figs. 1–11
- **Missing materials affecting confidence** Actual figures and data plots are not visible; supplementary information content is only partially described; code and model weights are referenced but not accessible; detailed benchmark statistics and confidence intervals for many comparisons are not fully reported in the text

## Reviewer

- **Overall assessment** This manuscript presents a potentially significant advance in computational modelling of transcriptional regulation. The core idea of a foundation model pretrained on chromatin accessibility data across many cell types, with interpretability built in, is timely and could be of broad interest. The reported performance in unseen cell types and the ability to identify long-range regulatory elements are impressive if the underlying evaluations are as robust as described. However, several technical aspects require clarification and additional validation before the claims can be fully assessed. The novelty relative to existing models such as Enformer needs sharper delineation, and the biological case studies, while intriguing, would benefit from more direct experimental validation or at least stronger orthogonal support.

- **Who would be interested in the results, and why** Computational biologists and machine learning researchers working on regulatory genomics would be the primary audience. The model's ability to predict expression in unseen cell types and its interpretability features could be valuable for studying gene regulation across development and disease. Researchers studying transcriptional regulation, particularly those focused on cis-regulatory elements, TF cooperativity, and non-coding variant interpretation, would find the model and its catalogues useful. The demonstrated applications to fetal haemoglobin regulation and leukaemia-associated variants could attract interest from the haematology and cancer biology communities.

- **Major strengths**
  1. The conceptual advance of a foundation model for transcriptional regulation trained across a large number of cell types is significant and timely.
  2. The two-stage design (pretraining on accessibility alone, then fine-tuning with paired expression) is elegant and leverages the abundance of ATAC-seq data.
  3. The demonstrated zero-shot prediction of lentiMPRA readouts, outperforming Enformer, is a strong result if the evaluation is fair and complete.
  4. The interpretability features (motif and region importance scores) enable biological discovery, as shown in the fetal haemoglobin and PAX5 case studies.
  5. The computational efficiency advantage over Enformer is practically important for the community.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of evaluation
- **Claim pointer** The claim that GET achieves experimental-level accuracy in predicting gene expression in unseen cell types (Pearson r = 0.94, R2 = 0.88 for fetal astrocytes) is central to the paper.
- **Evidence pointer** Main text, Fig. 1c; Extended Data Fig. 2
- **Concern** The evaluation appears to be limited to a single leave-out cell type (fetal astrocytes) in the main figure. The text mentions "a wide range of fetal cell types" in Extended Data Fig. 2c, but the specific numbers and the full distribution of performance across all 153 cell types are not reported in the visible text. The comparison to "experimental accuracy" (r = 0.92–0.99 between biological replicates) is made for one cell type only. It is unclear whether this level of performance holds across all cell types, particularly rare or heterogeneous ones. The choice of evaluation metric (Pearson correlation on log-transformed values) may also be favourable; other metrics such as mean absolute error or performance on highly and lowly expressed genes should be reported.
- **Why it matters** The central claim of the paper rests on the model's ability to generalize to unseen cell types. If performance varies substantially across cell types, or if the reported accuracy is not representative, the significance of the work is diminished. A more comprehensive and transparent evaluation is needed.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness of comparison
- **Claim pointer** The claim that GET outperforms Enformer in zero-shot lentiMPRA prediction (Pearson r = 0.55 vs 0.44) and in enhancer–gene pair prediction.
- **Evidence pointer** Main text, Fig. 2b; Fig. 3d; Extended Data Fig. 5
- **Concern** The comparison to Enformer, while favourable to GET, raises several questions. First, the text states that Enformer was trained on 486 tracks of K562 functional genomics data, including the same type of data used for evaluation. This creates a potential circularity in the comparison. Second, the evaluation for Enformer was limited to 2,000 elements due to computational cost, whereas GET was evaluated on all 226,243 elements. It is unclear whether the 2,000-element subset was randomly selected or chosen to be representative. Third, for the enhancer–gene pair prediction, the text mentions that Enformer incorporates distance information through positional encodings, and GET was extended with a DistanceContactMap module. The comparison may not be apples-to-apples if the models are given different input features. The ablation of GET components (Jacobian, DNase, Powerlaw) is useful, but the contribution of each component to the final performance should be more clearly quantified.
- **Why it matters** The claim of outperforming a state-of-the-art model is a key selling point. If the comparison is not fair or the evaluation protocol is biased, the conclusion may not hold. The computational advantage of GET is also highlighted, but the trade-off between performance and computational cost should be more carefully discussed.

- **Concern ID** R1-M3
- **Severity**Major
- **Blocking** Yes
- **Axis** Biological validation
- **Claim pointer** The case studies on fetal haemoglobin regulation and the PAX5–NR2C2 interaction are presented as demonstrations of the model's biological utility.
- **Evidence pointer** Main text, Fig. 3; Fig. 5; Extended Data Figs. 6–11
- **Concern** The fetal haemoglobin case study identifies known regulators (GATA, BCL11A) and a potentially novel SOX family involvement. However, the text states that SOX TFs "have previously been linked to fetal haemoglobin but were not known to function through this specific enhancer." This is a modest increment over existing knowledge. The PAX5–NR2C2 interaction is supported by AlphaFold predictions and co-immunoprecipitation, but the functional significance is inferred from the G183S mutation's effect on binding. The text reports increased interaction with the G183S mutation, but the downstream transcriptional consequences are not directly demonstrated. The analysis of patient samples is correlative. The manuscript would be strengthened by direct functional assays (e.g., reporter assays with mutant vs. wild-type PAX5, or CRISPR perturbation of the predicted interaction interface).
- **Why it matters** The biological case studies are intended to demonstrate that the model's predictions have real-world relevance. If the validation is incomplete or the findings are largely confirmatory, the added value of the model for biological discovery is less clear.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Model interpretability and causal claims
- **Claim pointer** The use of causal discovery (LiNGAM) on the gene-by-motif matrix to infer TF–TF interactions, and the claim that these represent "causal" interactions.
- **Evidence pointer** Main text, Fig. 4; Methods: 'Causal discovery of regulator interaction'
- **Concern** The application of LiNGAM to a gene-by-motif matrix derived from model attributions is methodologically unusual. LiNGAM assumes a linear generative model with non-Gaussian disturbances, which may not hold for this type of data. The text reports precision of 25.2% against STRING, which is better than random (5.6%), but this still means the majority of predictions are not supported by known interactions. The comparison to correlation-based methods shows improvement, but the absolute performance is modest. The causal interpretation of the edges is a strong claim that requires more careful justification. The authors should discuss the assumptions of LiNGAM and whether they are met, and consider alternative causal discovery methods or validation approaches.
- **Why it matters** The causal network is a major output of the paper and is used to generate hypotheses. If the causal claims are not well-founded, the downstream interpretations and the catalogue built on these predictions could be misleading.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and resource availability
- **Claim pointer** The manuscript describes a model and a catalogue, but the availability of code, model weights, and processed data is only mentioned in passing.
- **Evidence pointer** Main text, Discussion; Methods
- **Concern** The text mentions a Hugging Face space for the GET Catalogue, but the availability of the full model, training code, and evaluation scripts is not clearly stated. For a foundation model, reproducibility is critical. The authors should provide a clear statement on data availability, code availability, and model release. The computational resources required for training and inference should also be specified in more detail.
- **Why it matters** The community's ability to use, validate, and build upon this work depends on the availability of the resources. Without clear availability, the impact of the paper will be limited.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of writing
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract; Main text, Introduction
- **Issue** The abstract is dense and uses technical jargon (e.g., "regulatory grammars") without sufficient context for a general reader. The introduction could better motivate the need for a foundation model specifically for transcription, as opposed to other genomic tasks.
- **Required correction** Consider revising the abstract to be more accessible. In the introduction, explicitly state what gap in existing models (e.g., Enformer, Basenji) this work fills.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Performance metrics
- **Evidence pointer** Fig. 1c; Extended Data Fig. 2
- **Issue** The text reports Pearson correlation and R2 but does not consistently report confidence intervals or statistical significance for the comparisons. For the lentiMPRA benchmark, the number of elements used for evaluation and the standard errors are not reported in the main text.
- **Required correction** Add confidence intervals for all reported metrics and specify the number of test elements in each benchmark.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical detail
- **Affected element** Model architecture
- **Evidence pointer** Methods: 'Model architecture'
- **Issue** The description of the model architecture is brief. The number of parameters, the number of attention heads, the embedding dimension, and the number of layers are mentioned, but the total parameter count and the computational cost of training are not fully specified.
- **Required correction** Provide a table with the full model specifications and a more detailed description of the training time and resources.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Data processing
- **Affected element** Pseudobulk aggregation
- **Evidence pointer** Methods: 'ATAC-seq data processing'
- **Issue** The threshold of 600 cells for pseudobulk aggregation is stated, but the rationale for this threshold is not given. The sensitivity of the results to this threshold is not explored.
- **Required correction** Justify the threshold choice and, if possible, show that the results are robust to reasonable variations in this parameter.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Comparison to other methods
- **Affected element** Enhancer–gene pair prediction
- **Evidence pointer** Fig. 3d
- **Issue** The comparison to ABC and Enformer is shown, but the text does not discuss the strengths and weaknesses of each method in detail. The ABC method uses different input data (Hi-C, ATAC), which may not be a fair comparison.
- **Required correction** Add a discussion of the methodological differences and potential biases in the comparison.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Figure quality
- **Affected element** Fig. 4
- **Evidence pointer** Fig. 4a
- **Issue** The causal graph in Fig. 4a is likely to be dense and difficult to interpret in print. The text mentions communities, but the visual clarity of the figure is not assessable from the text alone.
- **Required correction** Ensure that the figure is legible and that the key findings are highlighted, possibly with a simplified schematic.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Terminology
- **Affected element** "Foundation model"
- **Evidence pointer** Title; Abstract
- **Issue** The term "foundation model" is used, but the model is trained on a relatively narrow domain (chromatin accessibility). The authors should clarify what makes this a foundation model as opposed to a large, pretrained model for a specific task.
- **Required correction** Briefly justify the use of the term "foundation model" in the context of this work.

## Risk / unsupported claims
- The claim of "experimental-level accuracy" is based on comparison to biological replicate variability for one cell type; this may not generalize.
- The claim that GET "outperforms current models" in lentiMPRA prediction is based on a comparison where the competing model (Enformer) was evaluated on a much smaller subset of elements.
- The causal interpretation of TF–TF interactions derived from LiNGAM is not fully justified and may be an overinterpretation of correlational structure.
- The functional significance of the PAX5 G183S mutation's effect on NR2C2 binding is inferred but not directly demonstrated at the transcriptional level.
- The generalizability to adult cell types is reported with an average R2 of 0.53, but the range and variability across cell types are not fully reported.
- The claim that the model "uncovers universal and cell-type-specific transcription factor interaction networks" is based on model attributions and causal discovery, which are indirect evidence and require experimental validation.