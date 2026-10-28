## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions) as provided
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, and suitability for a general interdisciplinary audience
- **Shared manuscript claim summary** The authors present FlexENN, a graph neural network that predicts binding free energies for both folded and intrinsically disordered protein complexes by constructing interface-restricted graphs with dynamic structural descriptors, and demonstrate its performance on a benchmark set including microtubule and microtubule-associated protein systems
- **Visible evidence base** Abstract, Introduction, Materials and Methods (partial), Results and Discussion, Conclusions, Author Contributions, Data Availability, Supporting Information list
- **Missing materials affecting confidence** Full methods details (architecture hyperparameters, training/validation splits, exact feature definitions), all figures and tables referenced but not visible, Supporting Information contents, experimental binding affinity measurement details, statistical significance testing, comparison with additional state-of-the-art methods

## Reviewer
- **Overall assessment** The manuscript addresses a timely and important problem: predicting binding energies for intrinsically disordered proteins, which are poorly handled by existing rigid-body methods. The core idea of using interface-restricted graphs with dynamic descriptors is conceptually appealing and the biological test systems are well chosen. However, the provided material does not contain sufficient quantitative evidence to evaluate the central claims. Key performance metrics, benchmark results, and methodological details are referenced but not visible in the supplied text. The claims of superiority over existing methods and physical interpretability cannot be assessed from the current material. The manuscript has potential but the case is not established from the provided evidence.

- **Who would be interested in the results, and why** Computational biophysicists and structural biologists working on protein-protein interactions, particularly those studying IDPs and their roles in signaling and disease. Researchers developing machine learning methods for biomolecular property prediction would also be interested in the architectural innovations. The microtubule community specifically would value improved tools for modeling MAP interactions, given the biological importance of these systems in neuronal function and transport.

- **Major strengths**
  1. The problem addressed is significant and timely: IDP binding energy prediction is a recognized gap in the field, and the authors correctly identify the limitations of rigid-body methods
  2. The conceptual approach of restricting graph construction to the interface and incorporating dynamic descriptors (B-factors, secondary structure propensities) is well motivated and physically sensible
  3. The choice of benchmark systems is thoughtful, particularly the use of MT interdimer versus lateral interfaces as a physical plausibility test and the inclusion of multiple IDP-partner complexes with distinct interface architectures
  4. The authors demonstrate awareness of dataset limitations, including PDBbind redundancy issues and the under-representation of large interfaces, and take steps to address these
  5. The ablation studies, as described, are well designed to probe feature importance and reveal interpretable differences between folded and disordered systems

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims that FlexENN "accurately predicts" binding energies and "outperforms all baselines" on the benchmark set
- **Evidence pointer** Results and Discussion, Tables 1-4, Figure 6
- **Concern** The central quantitative results are not visible in the provided material. All performance metrics, benchmark comparisons, and error analyses are contained in tables and figures that were not supplied. Without these data, the core claims of predictive accuracy and superiority over baselines cannot be evaluated.
- **Why it matters** The entire case for FlexENN rests on its quantitative performance relative to existing methods. The manuscript text describes outcomes but provides no numbers, confidence intervals, or statistical tests. This is the central evidence required to establish the method's utility.
- **Resolution test** Provide the full results tables and figures with all performance metrics, including RMSE, Pearson correlation, and comparisons across all baselines for every benchmark system. Include confidence intervals or error bars and statistical significance testing where appropriate.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The manuscript describes a graph neural network architecture with specific design choices
- **Evidence pointer** Materials and Methods, Message Passing section
- **Concern** The methods section is incomplete. The hidden dimension is stated as "Each layer l takes the node embeddings h(l) and 3D coordinate positions h(l) as input" with the dimension value missing. The message function and update function equations are referenced but not fully specified. Training details such as the train/validation/test split, hyperparameter tuning procedure, and early stopping criteria are not described. The exact composition of the 28-dimensional feature vector is only partially specified.
- **Why it matters** Reproducibility is a fundamental requirement for computational methods. Without complete architectural and training details, other researchers cannot implement or validate the method. The missing information also prevents assessment of potential overfitting or data leakage issues.
- **Resolution test** Provide complete architectural specifications, all feature definitions, training procedures, hyperparameter values, and data splitting methodology. Include the full equations for message passing and update functions.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Experimental validation
- **Claim pointer** The manuscript states that "reference binding affinity values extracted from our experiments" were used for the MT-MAPs benchmark
- **Evidence pointer** Benchmark Set section, Author Contributions
- **Concern** The experimental methods used to obtain binding affinities for the benchmark systems are not described. The authors mention "MT co-sedimentation assays" and "TIRF-M" but provide no experimental details, no error estimates on the measured values, and no information on how many replicates were performed. The statement that Kd values were "derived" from these assays is insufficient.
- **Why it matters** The benchmark values serve as ground truth for evaluating model performance. If these values have large uncertainties or systematic errors, the model evaluation is compromised. The experimental validation is a claimed contribution of this work and must be described with sufficient rigor.
- **Resolution test** Provide full experimental methods for the binding affinity measurements, including sample preparation, assay conditions, data analysis procedures, replicate numbers, and error estimates on all reported Kd values.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Comparison fairness
- **Claim pointer** The manuscript claims FlexENN outperforms "all baselines" including PBEE, XGBoost, Decision Trees, and Extra Trees
- **Evidence pointer** Results and Discussion, Tables 2-4
- **Concern** The comparison with PBEE is potentially confounded. The authors retrain PBEE on their expanded datasets, but it is unclear whether the hyperparameters were re-tuned for the new data or whether the original settings were used. Additionally, the comparison with tree-based methods uses the same Rosetta features, which may disadvantage these methods if the features are not well suited to the expanded dataset. The manuscript does not describe how baselines were optimized.
- **Why it matters** Unfair comparisons undermine the claim of superiority. If baselines are not given the same opportunity for hyperparameter optimization, the performance gap may reflect tuning effort rather than architectural advantage.
- **Resolution test** Describe the hyperparameter optimization procedure for all baselines. If possible, include comparisons with additional state-of-the-art deep learning methods for binding affinity prediction to establish the method's position in the current landscape.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** The manuscript claims the method works "across the full structural spectrum, from folded domains to complexes with one disordered partner"
- **Evidence pointer** Results and Discussion, Benchmark Set
- **Concern** The benchmark set is limited to MT-related systems and three additional IDP complexes. While the authors argue this spans diverse interface architectures, the total number of test systems is small (approximately 7-8 distinct complexes). The claim of generalizability across the "full structural spectrum" is not supported by this limited evaluation.
- **Why it matters** A method that works on a handful of carefully selected systems may not generalize to the diversity of IDP-mediated interactions in biology. The claim of broad applicability requires evaluation on a larger and more diverse test set.
- **Resolution test** Expand the benchmark to include a larger number of IDP complexes from diverse biological contexts, or clearly limit the claims of generalizability to the systems tested.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states the method "predicts binding energies across the full structural spectrum" but does not provide any quantitative performance summary. A single headline metric would help readers assess the method's utility.
- **Required correction** Include one or two key performance numbers in the abstract, such as overall RMSE or correlation on the benchmark set.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Introduction
- **Evidence pointer** Introduction, paragraph 1
- **Issue** The term "sequence-ensemble-function relationship" is used but not defined. This is a key concept for understanding the IDP framework.
- **Required correction** Provide a brief definition or explanation of this term when first introduced.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Materials and Methods, Datasets Preparation
- **Evidence pointer** Datasets Preparation section
- **Issue** The filtering criteria for the IDP dataset are described as "the same criteria applied to the folded proteins," but the criteria for folded proteins are not fully enumerated in the visible text.
- **Required correction** List all filtering criteria explicitly for both datasets.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Results and Discussion, Predictive Performance
- **Evidence pointer** Results and Discussion, Tables 1-4
- **Issue** No confidence intervals, standard deviations, or statistical significance tests are mentioned for the performance comparisons.
- **Required correction** Report uncertainty estimates for all metrics and perform statistical tests where comparisons are made.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results and Discussion, Ablation Studies
- **Evidence pointer** Ablation Studies section
- **Issue** The ablation studies are described as removing "node features" one at a time, but it is unclear whether the model was retrained for each ablation or whether features were masked at inference time.
- **Required correction** Clarify whether retraining was performed for each ablation condition.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Conclusions
- **Evidence pointer** Conclusions section
- **Issue** The conclusions mention future work on "explicit modeling of the thermodynamic underpinnings" but do not discuss potential limitations of the current approach beyond dataset bias.
- **Required correction** Add a brief discussion of other limitations, such as the reliance on static structures and the treatment of conformational ensembles.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Data and Software Availability
- **Evidence pointer** Data and Software Availability section
- **Issue** The GitHub repository is mentioned but no version, commit hash, or license information is provided.
- **Required correction** Provide a specific version identifier and license for the code repository.

## Risk / unsupported claims
- The claim that FlexENN "accurately predicts" binding energies is unsupported in the provided material, as no quantitative results are visible
- The claim that FlexENN "outperforms all baselines" is unsupported without the full comparison tables
- The claim that the model "infers conformational fuzziness from a single structure" is a strong interpretive claim that requires additional validation evidence
- The claim that the model "dynamically prioritizes different geometric and physicochemical features based on the inherent structural nature of the complex" is based on ablation studies whose results are not visible
- The statement that the benchmark includes "reference binding affinity values extracted from our experiments" cannot be evaluated without experimental methods and data
- The claim of working "across the full structural spectrum" is not supported by the limited number of test systems described
- The assertion that PBEE exhibits "systematic failure" on IDP complexes is based on results not visible in the provided material
- The claim that the model "successfully adapts to the distinct thermodynamic realities" of ordered and disordered proteins is interpretive and requires more direct evidence