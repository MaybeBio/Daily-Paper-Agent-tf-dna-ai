## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, supplementary material references)
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as presented in the provided text
- **Shared manuscript claim summary** The authors present a deep learning framework that simultaneously infers gene regulatory network (GRN) structure and estimates RNA kinetic parameters (transcription and decay rates) from single-cell RNA-sequencing (scRNA-seq) data. They introduce a continuous sampling method for yeast, apply the model to rapamycin response data, and validate predictions through in silico perturbations.
- **Visible evidence base** Abstract, introduction, results sections (including figure references), methods, and supplementary material descriptions
- **Missing materials affecting confidence** Full figures and supplementary data are not provided; specific numerical results, statistical analyses, and model performance metrics are referenced but not detailed in the text

## Reviewer
- **Overall assessment** This manuscript addresses a significant challenge in systems biology by proposing a unified framework for GRN inference and RNA kinetic estimation. The continuous sampling approach for yeast is innovative and could enable high-resolution temporal studies. However, the current text lacks sufficient quantitative detail to fully evaluate model performance, validation rigor, and biological insights. The claims of superiority over existing methods require more comprehensive benchmarking evidence.
- **Who would be interested in the results, and why** Researchers in gene regulatory network inference, single-cell transcriptomics, and computational biology would find this work relevant. The framework's ability to predict gene expression dynamics and simulate perturbations could interest those studying cellular responses to environmental stimuli. The continuous sampling method may also appeal to yeast biologists and those developing time-resolved single-cell protocols.
- **Major strengths**
  1. Novel integration of GRN inference with RNA kinetic estimation in a single deep learning framework
  2. Innovative experimental design for continuous single-cell sampling, enabling high temporal resolution
  3. Biophysical interpretability through explicit modeling of transcription and decay components
  4. Demonstration of in silico perturbation capabilities with potential for hypothesis generation
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The model "shows superior performance to existing models on the basis of recovery of known regulatory relationships" (Abstract)
  - **Evidence pointer** Results section, Figure 3B; location not provided
  - **Concern** The claim of superior performance is not substantiated with quantitative comparisons. The text mentions AUPR scores but does not provide specific values, statistical significance tests, or details on which existing models were compared. Without this information, the superiority claim cannot be evaluated.
  - **Why it matters** Establishing clear performance benchmarks is critical for the community to assess the practical utility of the proposed method over existing approaches.
  - **Resolution test** Provide AUPR values for the proposed model and at least 2-3 baseline methods (e.g., GENIE3, GRNBoost2, PIDC) on the same held-out test sets, with confidence intervals and statistical tests.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** "We validated the predictive power of the model by perturbing transcription factors in silico and comparing transcriptome-wide effects with experimental data" (Abstract)
  - **Evidence pointer** Results section, Figure 6; location not provided
  - **Concern** The validation of in silico perturbations is described qualitatively. The text mentions comparisons to an independent dataset with 12 genotypes but does not report quantitative metrics (e.g., correlation coefficients, effect sizes, or error rates) for the match between predicted and observed transcriptome changes.
  - **Why it matters** Without quantitative validation metrics, the predictive power of the model for perturbation responses remains unsubstantiated, which is a central claim of the work.
  - **Resolution test** Report correlation coefficients or normalized root mean square error between predicted and observed expression changes for each of the 11 TF deletion strains, with confidence intervals.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** "The resulting in silico model predicts future gene expression states" (Abstract)
  - **Evidence pointer** Results section, Figure 5F-G; location not provided
  - **Concern** The accuracy of future state predictions is not quantified. The text states predictions "match the observed transcriptome well" but does not provide error metrics or comparison to baseline prediction methods (e.g., simple extrapolation or ODE-based models).
  - **Why it matters** Predictive accuracy is a key differentiator of this approach. Without quantitative assessment, the practical value of the model for forecasting gene expression dynamics is unclear.
  - **Resolution test** Provide prediction error metrics (e.g., mean absolute error, R²) for predicted vs. observed expression at multiple future time points, compared to at least one baseline method.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** "By separating RNA velocity into transcription and decay rates, we show that rapamycin treatment causes existing ribosomal protein transcripts to be rapidly destabilized, while production of new transcripts gradually slows" (Abstract)
  - **Evidence pointer** Results section, Figure 5E-I; location not provided
  - **Concern** The biological insight regarding RP transcript destabilization is presented as a key finding, but the text does not provide quantitative measures (e.g., half-life estimates with confidence intervals, statistical comparison between time points) or validation against independent experimental measurements of mRNA stability.
  - **Why it matters** The biological conclusions depend on the accuracy of the estimated kinetic parameters. Without validation or error quantification, the reliability of these insights is uncertain.
  - **Resolution test** Compare estimated half-lives to published measurements (e.g., from metabolic labeling experiments) and report correlation or agreement metrics.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Readability
  - **Affected element** Methods section, "Time Assignment to Cells"
  - **Evidence pointer** Methods section; location not provided
  - **Issue** The description of time assignment is dense and difficult to follow, particularly the projection-based method in Equation 9.
  - **Required correction** Provide a clearer step-by-step explanation with a schematic or pseudocode to improve accessibility.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Technical soundness
  - **Affected element** Methods section, "Decay Rate Bounded Estimate"
  - **Evidence pointer** Methods section; location not provided
  - **Issue** The method for estimating decay rate bounds using the 0.05 quantile is described but the rationale for this choice and its sensitivity to the quantile threshold are not discussed.
  - **Required correction** Add a sensitivity analysis or justification for the quantile choice.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods section, "Hyperparameter Tuning"
  - **Evidence pointer** Methods section; location not provided
  - **Issue** The hyperparameter search space is not fully specified (e.g., ranges for learning rate and weight decay are given, but other parameters like network architecture are fixed without justification).
  - **Required correction** Provide complete hyperparameter ranges and final selected values for all tunable parameters.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Scientific importance
  - **Affected element** Results section, "In silico Perturbation of RNA Transcription Model"
  - **Evidence pointer** Results section, Figure 6; location not provided
  - **Issue** The interpretation of TF activity changes (e.g., GCN4, MSN2, PDR1) is speculative without experimental validation or literature support for the predicted compensatory mechanisms.
  - **Required correction** Add references or experimental evidence to support the proposed regulatory interactions, or temper the claims.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Lack of quantitative benchmarking against existing GRN inference methods
  - R1-M2: Absence of quantitative validation metrics for in silico perturbation predictions
  - R1-M3: No quantitative assessment of future state prediction accuracy
  - R1-M4: Insufficient validation of estimated kinetic parameters against independent measurements

- **Assessment against Nature-style criteria**
  - **Originality** The integration of GRN inference with RNA kinetic estimation in a single deep learning framework is novel. The continuous sampling method for yeast is also innovative. However, the individual components (deep learning for GRN, RNA velocity estimation) have been explored separately, and the novelty lies primarily in their combination.
  - **Scientific importance** The work addresses a fundamental challenge in understanding gene expression regulation. The ability to simultaneously infer regulatory relationships and kinetic parameters could have broad implications for systems biology. However, the biological insights presented are limited to a single condition (rapamycin response), and the broader applicability is not demonstrated.
  - **Interdisciplinary readership** The work bridges computational biology, genomics, and yeast molecular biology. The methods could interest researchers in machine learning applied to biology, but the technical complexity may limit accessibility to a broader audience.
  - **Technical soundness** The experimental design and computational framework are generally sound, but the lack of quantitative validation and benchmarking undermines confidence in the central claims. The methods are described in sufficient detail for replication, but the evaluation is incomplete.
  - **Readability for nonspecialists** The abstract and introduction are accessible, but the results and methods sections are dense and assume significant background in both deep learning and single-cell genomics. The biological significance of the findings could be better contextualized for a general audience.

- **Recommendation posture** Currently not established from the provided evidence. The manuscript presents a promising framework with innovative elements, but the central claims of superior performance and predictive power are not quantitatively substantiated. The authors must address the major concerns regarding benchmarking, validation, and error quantification before the case for the method's utility is convincing.