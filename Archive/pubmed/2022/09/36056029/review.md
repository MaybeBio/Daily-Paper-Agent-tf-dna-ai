## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary information descriptions.
- **Assessment boundary** Scientific validity, methodological rigor, reproducibility, and claims as supported by the provided evidence. No assessment of editorial fit or publication decision.
- **Shared manuscript claim summary** The authors present a 346-parameter statistical thermodynamic model, trained on in vitro massively parallel reporter assays of 14,206 designed σ70 promoter variants, that predicts site-specific transcription initiation rates for any σ70 promoter sequence. The model is validated on 22,132 diverse bacterial promoters across multiple independent datasets, and applied to design synthetic promoters with targeted transcription rates and to identify cryptic promoters in engineered genetic circuits.
- **Visible evidence base** Main text figures (Figs. 1–6), methods section, supplementary figure and table references, and supplementary data file descriptions. Raw sequencing data, complete model parameters, and full supplementary datasets are referenced but not provided in the submitted material.
- **Missing materials affecting confidence** Supplementary Data files 1–5 (containing all promoter sequences, measured transcription rates, model predictions, and benchmark calculations) are not accessible. The complete list of 472 initial features and the final 346 retained features is only partially described. Code for model training and the Promoter Calculator is not provided. Full details of the Borujeni et al. circuit dataset used for validation are not included.

## Reviewer

- **Overall assessment** This manuscript presents a substantial advance in quantitative modeling of bacterial transcription initiation. The hybrid biophysical-machine learning approach is conceptually sound, and the scale of experimental validation across 22,132 promoters is impressive. The model's ability to recover known canonical motifs without supervision serves as a strong positive control. However, several technical concerns regarding dataset composition, model selection, and validation methodology must be addressed before the predictive claims are fully established. The application demonstrations are compelling but would benefit from more rigorous quantitative assessment.

- **Who would be interested in the results, and why** Synthetic biologists designing genetic circuits and expression systems would find the promoter design capability immediately useful. Researchers studying bacterial gene regulation would value the comprehensive interaction energy parameters. Computational biologists developing sequence-to-function models would be interested in the methodological framework combining biophysics with machine learning. Metabolic engineers seeking predictable expression control would benefit from the design algorithms.

- **Major strengths**
  1. Large-scale systematic perturbation of promoter elements (14,206 variants) with careful design to isolate individual interaction contributions.
  2. In vitro transcription system eliminates confounding factors such as mRNA degradation and alternative sigma factors, enabling direct measurement of initiation kinetics.
  3. Model architecture grounded in statistical thermodynamics with interpretable parameters, rather than a black-box approach.
  4. Extensive external validation across multiple independent datasets with diverse promoter sequences and measurement methods.
  5. Practical applications demonstrated for both forward engineering and circuit debugging.
  6. Model parameters are transparent and provided in supplementary materials, enabling community use.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Data quality and representativeness
- **Claim pointer** "We combine massively parallel assays, biophysics, and machine learning to develop a 346-parameter model that predicts site-specific transcription initiation rates for any σ70 promoter sequence"
- **Evidence pointer** Methods: Library design; Fig. 1B
- **Concern** The training dataset of 14,206 designed promoters is heavily biased toward consensus or near-consensus background sequences. The library design systematically varies one element at a time while keeping others at consensus or anti-consensus states. This creates a training distribution that may not adequately sample the combinatorial space of promoter sequences, particularly the interactions between multiple non-consensus elements. The claim of predicting "any σ70 promoter sequence" requires demonstration that the model generalizes to sequences with multiple simultaneous deviations from consensus, which is not clearly established.
- **Why it matters** If the model is trained primarily on single-element perturbations, it may not capture the complex epistatic interactions that occur in natural promoters where multiple elements deviate from consensus simultaneously. This could lead to systematic prediction errors for the diverse promoter sequences found in bacterial genomes.
- **Resolution test** Provide analysis of prediction accuracy stratified by the number of non-consensus elements in the test promoters. Demonstrate that accuracy does not degrade as promoters deviate further from the consensus background. Alternatively, include a validation set of promoters with multiple simultaneous element perturbations.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Model selection and overfitting
- **Claim pointer** "We carried out feature reduction to remove extraneous properties, which lowered the number of fitted coefficients" and "a ridge regression model with 346 fitted coefficients yielded a convergent learning curve"
- **Evidence pointer** Methods: Model training using machine learning; Fig. 2A
- **Concern** The feature selection process is not fully described. The manuscript states that 472 initial features were reduced to 346, but the criteria for "appreciably increase model accuracy" are not quantified. The learning curve in Fig. 2A shows convergence, but the gap between training and test performance is not explicitly discussed. With 346 parameters and 4,673 training examples, the ratio of parameters to samples is approximately 1:13.5, which may be adequate but requires demonstration that the model is not overfitting to idiosyncrasies of the training set.
- **Why it matters** If feature selection was performed using the same data subsequently used for model evaluation, the reported accuracy metrics may be optimistically biased. The generalizability claims depend on demonstrating that the model selection process did not overfit to the training data.
- **Resolution test** Provide a detailed description of the feature selection procedure, including whether it was performed within cross-validation folds. Report the standard deviation of test set accuracy across cross-validation folds. Consider reporting performance of the full 472-feature model for comparison.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Validation methodology
- **Claim pointer** "We found that the statistical thermodynamic model retained accuracy (R2 = 0.60, Spearman's ρ = 0.68; R2 = 0.45, Spearman's ρ = 0.68; R2 = 0.65, Spearman's ρ = 0.70; Fig. 3C, D and Supplementary Fig. 3)"
- **Evidence pointer** Fig. 3C, D; Supplementary Fig. 3
- **Concern** The external validation datasets (Urtecho et al., Hossain et al., Yu et al.) were measured in vivo, where transcription rates are confounded by mRNA degradation, DNA copy number variation, and alternative sigma factors. The manuscript acknowledges these factors but does not quantify their potential impact on the reported accuracy. The R2 values of 0.45–0.65 for in vivo datasets represent a substantial drop from the in vitro R2 of 0.79–0.80, and the manuscript does not adequately address whether this drop is expected given the additional biological complexity or whether it indicates model limitations.
- **Why it matters** The claim of predicting transcription rates "in bacteria" requires that the model performs well in the cellular context. If the accuracy drop is primarily due to unmodeled biological factors, the model's utility for in vivo applications is limited. If the drop indicates model misspecification, this needs to be identified and addressed.
- **Resolution test** Provide a more detailed analysis of prediction errors in the in vivo datasets, including whether errors correlate with predicted mRNA stability, plasmid copy number, or the presence of alternative sigma factor binding sites. Consider developing a combined model that accounts for these factors.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Application demonstration rigor
- **Claim pointer** "We then demonstrated that our automated algorithm can also generate no-promoter regions with minimized transcription rates by designing 60 bp and 120 bp regions and measuring their transcription rates using a reporter protein in test genetic circuits"
- **Evidence pointer** Fig. 6C inset; Methods: Automated promoter sequence design
- **Concern** The demonstration of no-promoter region design is based on only two designed sequences (60 bp and 120 bp). This is a very small sample size to establish the reliability of the design algorithm for this application. Additionally, the reported "161-fold lower reporter expression than the commonly used J100 promoter" is a single comparison and does not provide a distribution of expected performance.
- **Why it matters** The claim of automated design capability for minimizing off-target transcription is an important practical application. However, with only two examples, it is not possible to assess the reliability and consistency of the design algorithm for this purpose.
- **Resolution test** Design and characterize a larger set of no-promoter regions (at least 10–20 sequences) to demonstrate consistent performance. Report the distribution of achieved transcription rates and compare to the model predictions.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Benchmarking fairness
- **Claim pointer** "Overall, when carrying out equivalent data analysis (Methods), our model achieves higher accuracy on the LaFleur, Urtecho, and Hossain datasets (Supplementary Table 4)"
- **Evidence pointer** Methods: Model benchmarking; Supplementary Tables 4–6
- **Concern** The benchmarking against Lagator et al. is described only briefly. The manuscript states that "equivalent data analysis" was performed, but the details of how the Lagator model was applied to the new datasets are not fully described. The Lagator model was trained on a different type of data (Flow-seq with random promoters), and it is unclear whether the comparison is fair in terms of data preprocessing, feature representation, and evaluation metrics.
- **Why it matters** The claim of superior performance relative to existing models is an important contribution. If the benchmarking methodology is not transparent and fair, the comparative claims cannot be properly evaluated.
- **Resolution test** Provide a more detailed description of the benchmarking procedure, including any data preprocessing steps, parameter fitting for the Lagator model on new datasets, and the specific evaluation metrics used. Consider including additional benchmark models for comparison.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Model availability
- **Evidence pointer** Discussion; Methods
- **Issue** The manuscript does not state whether the model parameters, training code, and design algorithm are publicly available. The Promoter Calculator is mentioned but no URL or access information is provided.
- **Required correction** Provide a clear statement of code and data availability, including URLs for any public repositories.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Fig. 2B, D
- **Evidence pointer** Fig. 2B, D
- **Issue** The manuscript reports R2 values but does not provide confidence intervals or measures of uncertainty for the model performance metrics. Given the importance of these metrics for the paper's claims, some quantification of uncertainty would strengthen the presentation.
- **Required correction** Report confidence intervals for R2 and other performance metrics, or provide bootstrap estimates.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Data filtering transparency
- **Affected element** Methods: Data filtering
- **Evidence pointer** Methods: Data filtering
- **Issue** The filtering criteria for model training (single predominant TSS, minimum read counts) are clearly stated, but the number of promoters excluded by each criterion is not reported. This information would help assess potential selection bias.
- **Required correction** Report the number of promoters excluded at each filtering step.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Figure clarity
- **Affected element** Fig. 6A
- **Evidence pointer** Fig. 6A
- **Issue** The circuit diagram in Fig. 6A is complex and the annotation of predicted versus measured transcription rates is not immediately clear. The relationship between the model predictions and the RNA-Seq measurements could be presented more clearly.
- **Required correction** Consider simplifying the figure or providing a more detailed legend explaining the visual encoding of predicted and measured values.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout
- **Evidence pointer** Throughout
- **Issue** The terms "transcription rate," "transcription initiation rate," and "TX rate" are used somewhat interchangeably. While the meaning is generally clear, consistent terminology would improve readability.
- **Required correction** Define terms at first use and use consistently throughout.

## Risk / unsupported claims
- The claim that the model predicts transcription rates for "any σ70 promoter sequence" is not fully supported given the training data bias toward consensus backgrounds and the limited testing on sequences with multiple simultaneous non-consensus elements.
- The claim of "automated design" capability is supported by 35 designed promoters, but the generalizability of the design algorithm to more complex design objectives (e.g., multi-promoter systems, dynamic expression patterns) is not demonstrated.
- The claim that the model "provides a biophysical basis for understanding gene regulation in natural genetic systems" is partially supported by the recovery of known motifs, but the manuscript does not demonstrate new biological insights beyond what was previously known.
- The benchmarking claim of superior performance relative to Lagator et al. cannot be fully evaluated without access to the detailed benchmarking methodology and results.
- The application to circuit debugging is demonstrated on a single circuit, and the quantitative accuracy of cryptic promoter identification (55%) is modest; the practical utility of this application requires further validation.