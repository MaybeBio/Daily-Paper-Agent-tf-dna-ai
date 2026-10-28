## Review setup
- **Input scope** Abstract only
- **Assessment boundary** Claims and evidence as presented in the abstract; no methods, figures, tables, or supplementary materials were provided
- **Shared manuscript claim summary** The authors introduce a convolutional neural network (CNN) trained on sequence and structural features to predict binding affinity changes between SARS-CoV-2 spike RBD variants and ACE2 homologues. They report 83.28% classification accuracy and a Pearson correlation coefficient of 0.85 in five-fold cross-validation, claim improved predicted binding for most circulating variants, and describe exhaustive screening of up to four simultaneous substitutions. They further report that animal ACE2 binding trends mirror human ACE2, with white-tailed deer ACE2 binding nearly as tightly as human ACE2, while cattle, pig, and chicken ACE2s bind weakly.
- **Visible evidence base** Abstract text only; no dataset description, model architecture, training details, validation procedure, or experimental binding measurements are visible
- **Missing materials affecting confidence** Full manuscript, methods section, all figures and tables, training and test data, cross-validation details, definition of classification thresholds, list of circulating variants assessed, and any statistical significance testing

## Reviewer
- **Overall assessment** The abstract presents a potentially useful computational tool for predicting RBD-ACE2 binding affinity changes, which could have public health and zoonotic surveillance value. However, the claims as stated cannot be adequately evaluated from the abstract alone. Key metrics are reported without context on data splitting, class definitions, or comparators, and the biological conclusions about animal ACE2 binding are presented without supporting quantitative evidence. The work is of interest to the virology and computational biology communities, but the current evidence base is insufficient to establish the case.
- **Who would be interested in the results, and why** Researchers in viral evolution, zoonotic spillover surveillance, structural virology, and computational protein engineering would be interested. The model could inform monitoring of SARS-CoV-2 adaptation in animal reservoirs and guide experimental prioritization of RBD variants. Public health agencies tracking emerging variants may also find the predictive screening useful.
- **Major strengths** The reported scale of training data (8,440 variants) is substantial. The combination of sequence and structural features in a CNN is a reasonable approach. The proactive screening of multi-substitution combinations addresses a practical gap in variant surveillance. The comparative analysis across animal ACE2 homologues has direct relevance to spillover risk assessment.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The model achieves a classification accuracy of 83.28% and a Pearson correlation coefficient of 0.85 between predicted and experimentally calculated binding affinities in five-fold cross-validation tests.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract does not specify how classification accuracy was defined, what threshold separated "improved" from "non-improved" binding, how the five-fold split was constructed (e.g., by variant, by protein, or by sequence identity), or whether the Pearson correlation was computed on the full continuous range or on a subset. Without these details, the reported metrics cannot be interpreted or compared with existing methods.
  - **Why it matters** Cross-validation metrics are only meaningful if the data partitioning prevents leakage between training and test sets. If variants sharing similar sequences or structural contexts appear in both training and test folds, the reported accuracy and correlation could be inflated. The classification accuracy also depends entirely on the chosen threshold, which is not stated.
  - **Resolution test** Provide the classification threshold, the data splitting strategy, and the distribution of experimental affinities. Report performance on a held-out test set that is separated by sequence identity or by experimental batch, and include confidence intervals for both metrics.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence quality
  - **Claim pointer** The model predicts improved binding affinity for most circulating variants.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** The abstract does not define which variants are considered "circulating," how many were assessed, or what constitutes "improved" binding. No comparison is made to experimental measurements for these specific variants, so the claim is presented as a prediction without external validation.
  - **Why it matters** A key use case for such a model is to flag variants of concern in real time. If the model systematically overpredicts improved binding for circulating variants, it could generate false alarms. Without validation against independent experimental data for these variants, the claim is unsupported.
  - **Resolution test** List the circulating variants assessed, provide their predicted and experimentally measured affinities where available, and report sensitivity and specificity for identifying experimentally confirmed improved binders.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Support for biological conclusions
  - **Claim pointer** White-tailed deer ACE2 binds to RBD almost as tightly as human ACE2 while cattle, pig, and chicken ACE2s bind weakly. The binding affinity of RBD variants against animal ACE2s follows similar trends as those against human ACE2.
  - **Evidence pointer** Abstract; location not provided
  - **Concern** These are quantitative biological claims, but no numerical values, statistical comparisons, or experimental references are provided. It is unclear whether these conclusions are based on model predictions alone or on a combination of predictions and experimental measurements. The phrase "almost as tightly" is not defined.
  - **Why it matters** The relative binding affinities across species are central to the spillover risk narrative. If these claims rest solely on model predictions, they inherit all model uncertainties and need explicit error analysis. If they are supported by experimental data, that data must be cited or shown.
  - **Resolution test** Provide the predicted and, if available, experimentally measured binding affinities for each ACE2 homologue, with error bars or confidence intervals, and state whether the cross-species trend was statistically tested.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Model description
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The abstract states the model is trained on "protein sequence and structural features" but does not specify which structural features were used or how they were derived.
  - **Required correction** Specify the structural features (e.g., residue contacts, solvent accessibility, or docking poses) and how they were computed or obtained.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Screening description
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The exhaustive screening of combinations of up to four substitutions is mentioned, but the search space size and any filtering criteria are not described.
  - **Required correction** State the total number of combinations screened and any filters applied (e.g., excluding positions with known glycosylation or conserved functional roles).
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Data availability
  - **Evidence pointer** Abstract; location not provided
  - **Issue** The source of the 8,440 experimental binding affinity values is not identified.
  - **Required correction** Cite the experimental dataset(s) used for training and state whether the data are publicly available.
- **Technical failings that need to be addressed before the case is established** R1-M1 (cross-validation and metric definitions), R1-M2 (validation on circulating variants), R1-M3 (quantitative support for cross-species binding claims)
- **Assessment against Nature-style criteria**  
  Originality: The combination of CNN-based prediction with multi-species ACE2 screening is not entirely novel, but the scale and the proactive screening component add some originality.  
  Scientific importance: The topic is timely and relevant to pandemic surveillance, but the importance of the specific claims cannot be assessed without validation data.  
  Interdisciplinary readership: The work bridges computational biology, virology, and ecology, which could attract a broad audience.  
  Technical soundness: Not assessable from the abstract; the reported metrics lack necessary context and validation.  
  Readability for nonspecialists: The abstract is generally clear, but terms such as "Pearson correlation coefficient" and "five-fold cross-validation" are used without explanation, which may limit accessibility.
- **Recommendation posture** Currently not established from the provided evidence. The abstract describes a potentially useful tool, but the key performance claims and biological conclusions require the full manuscript and additional validation details to be evaluated. Supportive if technical concerns are resolved.

## Risk / unsupported claims
- The claim of 83.28% classification accuracy and 0.85 Pearson correlation is unsupported without details on data splitting, threshold definition, and test set independence.
- The claim that the model "predicts improved binding affinity for most circulating variants" is unsupported without a defined variant list and external validation.
- The cross-species binding affinity comparisons (white-tailed deer, cattle, pig, chicken) are unsupported without numerical data or statistical analysis.
- The statement that "binding affinity of RBD variants against animal ACE2s follows similar trends as those against human ACE2" is a broad generalization that is not backed by any visible quantitative evidence.