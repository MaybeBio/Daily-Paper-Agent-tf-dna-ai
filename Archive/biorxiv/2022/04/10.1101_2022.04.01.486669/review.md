## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence presented in the abstract; no methods, figures, or supplementary data were provided for evaluation
- **Shared manuscript claim summary** The authors present RecGen, a generative deep learning algorithm (Conditional Variational Autoencoders) trained on over two million Cre-like recombinase sequences evolved for 89 target sites, which can predict recombinase sequences with activity on novel target sites, potentially accelerating designer-recombinase development from weeks (directed evolution) to days (prediction and synthesis)
- **Visible evidence base** Abstract text only; no experimental data, model architecture details, training/validation splits, or activity assay results are visible
- **Missing materials affecting confidence** Full manuscript, methods section, all figures (including the teaser figure), supplementary tables, model hyperparameters, dataset composition details, experimental validation protocols, and statistical analyses

## Reviewer
- **Overall assessment** The abstract presents a potentially impactful application of generative deep learning to a challenging protein engineering problem. The core claim, that RecGen can predict active recombinases for novel target sites, is scientifically interesting and would be of broad interest if rigorously validated. However, the abstract alone provides insufficient evidence to assess the validity, generalizability, or robustness of the approach. The scale of the training data (over two million sequences) is notable, but the lack of methodological detail and quantitative results prevents any meaningful evaluation of the central claim. The comparison to directed evolution, while rhetorically compelling, is not supported by any direct experimental comparison in the abstract.
- **Who would be interested in the results, and why** Researchers in genome engineering, synthetic biology, and protein design would be the primary audience. The work also has relevance for the broader deep learning for biology community, particularly those interested in generative models for sequence design. Clinicians and biotechnology companies developing gene therapies might find the potential acceleration of recombinase development attractive, though this would depend on the robustness of the experimental validation.
- **Major strengths** The problem is well-motivated and practically important. The use of a large-scale dataset (over two million sequences) for training is a significant resource. The conceptual shift from directed evolution to generative prediction is timely and aligns with current trends in AI-driven protein design. The stated timeline advantage (days versus weeks) is a clear and compelling value proposition.
- **Major Concerns** 
  - R1-M1
  - R1-M2
  - R1-M3
- **Minor Comments** 
  - R1-m1
  - R1-m2
  - R1-m3
- **Technical failings that need to be addressed before the case is established** The abstract does not provide any quantitative evidence of prediction accuracy, specificity, or off-target activity. The definition of "novel target sites" is unclear, and the relationship between the 89 training target sites and the tested novel sites is not described. The absence of any negative controls or comparison to baseline methods (e.g., random sequence generation, directed evolution outcomes) is a critical gap.
- **Assessment against Nature-style criteria** 
  - Originality: The application of Conditional Variational Autoencoders to recombinase design appears novel, though the general concept of generative models for protein design is established. The specific domain (tyrosine-type recombinases) adds a new dimension.
  - Scientific importance: If validated, the work could significantly streamline genome engineering workflows. The potential therapeutic implications of designer-recombinases elevate the importance.
  - Interdisciplinary readership: The topic bridges machine learning, protein engineering, and genome editing, which would attract a broad readership. However, the abstract currently lacks sufficient detail for nonspecialists in any of these fields to assess the claims.
  - Technical soundness: Cannot be evaluated from the abstract. The lack of methodological detail and quantitative results is a major limitation.
  - Readability for nonspecialists: The abstract is generally clear and accessible, but the term "Conditional Variational Autoencoders" is used without explanation, and the teaser figure description is vague.
- **Recommendation posture** Currently not established from the provided evidence. The abstract presents a promising concept, but the central claim of predictive activity on novel target sites is unsupported by any visible data. A full manuscript with detailed methods, experimental validation, and statistical analysis would be required to assess whether the case can be made.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Experimental validation demonstrated that the algorithm can predict recombinase sequences with activity on novel target-sites"
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract states that experimental validation demonstrated predictive activity, but no data, metrics, or experimental details are provided. It is unclear how many novel target sites were tested, what the success rate was, how activity was measured, and whether the active sequences were truly novel or closely related to training sequences.
- **Why it matters** The central claim of the paper rests entirely on this experimental validation. Without quantitative evidence, the reader cannot assess whether the approach works reliably, how it compares to directed evolution, or whether the results are statistically significant. This is the core of the paper's contribution.
- **Resolution test** Provide the number of tested novel target sites, the success rate (e.g., fraction of sites with active recombinases), activity measurements (e.g., reporter assays, specificity data), and a comparison to appropriate controls (e.g., random sequences, directed evolution outcomes). Statistical significance should be reported.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability
- **Claim pointer** "RecGen is useful to accelerate the development of future designer-recombinases"
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract implies that RecGen can generalize to any novel target site, but the training data covers only 89 target sites. The diversity of these sites, the sequence space they represent, and the criteria for "novelty" are not described. It is possible that the model only works for target sites similar to those in the training set, which would limit its practical utility.
- **Why it matters** The value proposition of the tool depends on its ability to handle a wide range of target sites beyond the training distribution. If the model fails on dissimilar sites, the claim of accelerating development would be overstated.
- **Resolution test** Describe the sequence diversity of the 89 training target sites, define the criteria for "novel" sites, and report performance on a held-out set of target sites that are maximally dissimilar to the training set. If possible, include a systematic analysis of how prediction success varies with sequence similarity to training sites.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We gathered the sequence information of over two million Cre-like recombinase sequences evolved for 89 different target sites with which we trained Conditional Variational Autoencoders"
- **Evidence pointer** Abstract text; location not provided
- **Concern** The abstract does not describe the model architecture, training procedure, data preprocessing, or validation strategy. It is unclear how the Conditional Variational Autoencoder was conditioned on target site information, how overfitting was controlled, and how the model was evaluated during training. The quality and consistency of the training data (e.g., whether all sequences were functionally validated) are also not addressed.
- **Why it matters** Reproducibility and technical rigor are essential for a computational method. Without these details, the reader cannot judge whether the model is well-designed, whether the results are reliable, or whether the approach can be implemented by others.
- **Resolution test** Provide a detailed methods section including model architecture, hyperparameters, training/validation splits, data filtering criteria, and a description of how target site information is encoded. Include an analysis of model performance on training versus held-out data to demonstrate that the model is not merely memorizing sequences.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The term "Conditional Variational Autoencoders" is used without explanation, which may confuse nonspecialist readers.
- **Required correction** Add a brief parenthetical explanation, such as "a type of generative neural network that learns to produce sequences conditioned on a desired target site."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract mentions a "Teaser Figure" but does not describe its content beyond a vague comparison of timelines. The figure is not accessible for review.
- **Required correction** Provide a clear description of the figure in the abstract or ensure the figure is available for review in the full manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Context
- **Affected element** Abstract text
- **Evidence pointer** Abstract text; location not provided
- **Issue** The abstract does not mention any limitations of the approach or potential failure modes, which is unusual for a methods paper.
- **Required correction** Add a sentence acknowledging limitations, such as the dependence on training data diversity or the need for experimental validation of each prediction.

## Risk / unsupported claims
- The claim that RecGen can predict active recombinases for novel target sites is unsupported by any visible data in the abstract.
- The claim that prediction and synthesis can be done in days is not substantiated with any timeline data or protocol description.
- The implicit claim that RecGen outperforms or complements directed evolution is not supported by any comparative analysis.
- The generalizability of the model beyond the 89 training target sites is not assessable from the abstract.
- The quality and functional relevance of the "over two million" training sequences are not described, making the dataset's utility unverifiable.