## Review setup
- **Input scope** Full manuscript (ChemRxiv preprint)
- **Assessment boundary** Claims, methods, results, and conclusions as presented in the provided text
- **Shared manuscript claim summary** The authors present SO3LR-SF, a physics-based scoring function built on a pretrained equivariant machine-learned force field (SO3LR) that was not trained on protein–ligand complexes. They claim it achieves state-of-the-art accuracy in predicting protein–ligand binding energies, with competitive performance against semi-empirical and molecular dynamics-based methods, at a fraction of the computational cost, and with built-in explainability features.
- **Visible evidence base** The provided text includes the title, author list, journal/platform, date, DOI, and the full abstract/manuscript summary. No figures, tables, methods section, or supplementary materials are provided.
- **Missing materials affecting confidence** Full methods, all figures and tables, supplementary information, code and data availability, detailed benchmark descriptions, and the complete results section are not provided. This severely limits the ability to assess the technical soundness and reproducibility of the claims.

## Reviewer
- **Overall assessment** The manuscript presents a potentially significant advance in the field of structure-based drug design by introducing a machine-learned force field-based scoring function that is both fast and interpretable. The core idea of using a pretrained MLFF not exposed to protein–ligand complexes as a foundation is novel and addresses a key concern about overfitting in the field. However, the provided text is insufficient to fully evaluate the technical soundness, reproducibility, and robustness of the claims. The reported performance metrics are promising, but the lack of methodological detail and access to the underlying data and code prevents a definitive assessment.
- **Who would be interested in the results, and why** Computational chemists, medicinal chemists, and researchers in drug discovery and biophysics would be interested. The work offers a fast, accurate, and interpretable alternative to existing scoring functions, potentially accelerating virtual screening and lead optimization. The explainability framework is particularly valuable for understanding binding mechanisms.
- **Major strengths** 1. The use of a pretrained MLFF (SO3LR) that was not trained on protein–ligand complexes is a strong and principled approach to test transferability and avoid overfitting. 2. The reported computational speed (1–10 seconds per complex) is a major practical advantage over MD-based methods. 3. The multi-level explainability framework (energy decomposition, per-atom contributions, 2D/3D maps) is a significant and welcome addition, addressing a key limitation of many black-box ML models. 4. The identification of pocket descriptors (e.g., polar SASA ratio) for applicability domain assessment is a practical and useful feature.
- **Major Concerns**
    - **Concern ID** R1-M1
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Reproducibility and methodological detail
    - **Claim pointer** "SO3LR-SF attains a relative interaction error of 5.8% against DLPNO-CCSD(T) references, the lowest of all tested methods."
    - **Evidence pointer** Location not provided
    - **Concern** The manuscript text does not describe the architecture of the SO3LR MLFF, the training data and procedure, or the specific implementation of the physics-based terms (short-range repulsion, electrostatics, long-range dispersion). The benchmark datasets (PLA15, FEP, Wang) are named but not described in terms of composition, size, or how they were processed. The "restrained geometry optimization" and "8 Å trimming protocol" are mentioned but not defined.
    - **Why it matters** Without these details, the results cannot be reproduced or independently verified. The claim of "lowest of all tested methods" is unverifiable without knowing which methods were compared and under what conditions. The entire scientific contribution hinges on the validity of the method and the benchmarks.
    - **Resolution test** The authors must provide a complete description of the SO3LR architecture, training data, and the functional form of all energy terms. Full details of all benchmark datasets, including their source, preparation, and the exact protocols for all compared methods, must be given. Code and model weights should be made available for independent testing.
    - **Concern ID** R1-M2
    - **Severity** Major
    - **Blocking** Yes
    - **Axis** Statistical rigor and uncertainty quantification
    - **Claim pointer** "SO3LR-SF achieves an average Spearman correlation of 0.51... on par with the best semi-empirical quantum-mechanical method tested (0.47, GFN-FF) and with MMGBSA (0.44), and surpassing Glide (0.27)."
    - **Evidence pointer** Location not provided
    - **Concern** The reported Spearman correlations are presented as point estimates without any measure of uncertainty (e.g., standard deviation, confidence intervals, or error bars). The text states "average Spearman correlation" but does not specify over what (e.g., over targets, over cross-validation folds). The comparison to other methods is qualitative ("on par with", "surpassing") without statistical tests to determine if the differences are significant.
    - **Why it matters** In benchmark comparisons, point estimates can be misleading. Without error bars or statistical tests, it is impossible to know if the observed differences are meaningful or due to random variation. The claim of "on par with" or "surpassing" is not scientifically rigorous.
    - **Resolution test** The authors must report Spearman correlations with appropriate measures of uncertainty (e.g., standard deviation across targets or bootstrapped confidence intervals). They should perform and report statistical significance tests (e.g., paired t-test, Wilcoxon signed-rank test) for the comparison between SO3LR-SF and each other method.
    - **Concern ID** R1-M3
    - **Severity** Major
    - **Blocking** No
    - **Axis** Generalizability and robustness
    - **Claim pointer** "We identified two pocket descriptors that flag applicability before scoring, e.g. polar solvent accessible surface area (SASA) ratio correlating strongly (r = 0.81) with performance."
    - **Evidence pointer** Location not provided
    - **Concern** The text mentions "two pocket descriptors" but only names one (polar SASA ratio). The second descriptor is not identified. The correlation (r = 0.81) is reported without a p-value or confidence interval. It is unclear how this descriptor was derived, on which dataset it was validated, and whether it is predictive or merely correlative.
    - **Why it matters** The applicability domain flag is a key practical feature. If the second descriptor is not specified, the method is incomplete. A single correlation value without statistical context is insufficient to establish the reliability of this flag. Overfitting to the training/validation set is a concern.
    - **Resolution test** The authors must explicitly name and describe the second pocket descriptor. They should report the p-value and confidence interval for the reported correlation. They should demonstrate the predictive power of these descriptors on an independent test set, not just the dataset used to identify them.

- **Minor Comments**
    - **Concern ID** R1-m1
    - **Severity** Minor
    - **Axis** Clarity and completeness
    - **Affected element** Abstract
    - **Evidence pointer** Location not provided
    - **Issue** The abstract states "Each complex is scored in 1–10 seconds on 12 CPU cores, an 80- to 300-fold speedup over comparable MLFFs." The term "comparable MLFFs" is vague. It is unclear which specific MLFFs are being compared and under what hardware/software conditions.
    - **Required correction** Specify the names of the MLFFs used for the speed comparison and provide the exact hardware and software configuration for all timing benchmarks.
    - **Concern ID** R1-m2
    - **Severity** Minor
    - **Axis** Data availability
    - **Affected element** Entire manuscript
    - **Evidence pointer** Location not provided
    - **Issue** The manuscript does not state whether the code, model weights, or benchmark datasets will be made publicly available.
    - **Required correction** Add a "Data and code availability" statement as per standard practice, specifying what will be released and under what license.
    - **Concern ID** R1-m3
    - **Severity** Minor
    - **Axis** Terminology
    - **Affected element** Title and abstract
    - **Evidence pointer** Location not provided
    - **Issue** The title uses "Explainable ML force-field" but the abstract describes a "multi-level explainability framework." The term "explainable" is often used loosely. It would be more precise to use "interpretable" or to clearly define what is meant by "explainable" in this context.
    - **Required correction** Clarify the terminology. If the framework provides energy decomposition and per-atom contributions, it is more accurately described as "interpretable" or "physics-informed" rather than "explainable" in the XAI sense.

- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of methodological detail and reproducibility), R1-M2 (lack of statistical rigor in benchmark comparisons).

## Risk / unsupported claims
- The claim that SO3LR-SF is "the lowest of all tested methods" on PLA15 is unsupported without a full list of compared methods and their results.
- The claim of "on par with" or "surpassing" other methods on the FEP and Wang datasets is unsupported without statistical significance testing.
- The claim of an "80- to 300-fold speedup over comparable MLFFs" is unsupported without specifying the compared MLFFs and hardware.
- The claim of a "multi-level explainability framework" is unsupported without a detailed description of the framework and examples of its output.
- The claim of "two pocket descriptors that flag applicability" is unsupported as only one is named and its predictive power is not demonstrated.

## Assessment against Nature-style criteria
- **Originality:** High. The use of a pretrained, non-protein–ligand MLFF as a foundation for a scoring function is a novel and principled approach that directly addresses a key limitation in the field (overfitting). The integration of a multi-level explainability framework is also a significant and timely contribution.
- **Scientific importance:** Potentially high. If the claims are robust, this work could provide a fast, accurate, and interpretable tool for drug discovery, potentially replacing or augmenting existing scoring functions and reducing the reliance on expensive MD simulations.
- **Interdisciplinary readership:** Moderate to high. The work bridges machine learning, computational chemistry, and drug discovery. The results would be of interest to a broad audience in these fields.
- **Technical soundness:** Cannot be assessed from the provided text. The lack of methodological detail, statistical rigor, and access to data/code prevents a proper evaluation. The core claims are promising but unverified.
- **Readability for nonspecialists:** The abstract is well-written and accessible. However, the full manuscript would need to be reviewed for clarity.

## Recommendation posture
**Currently not established from the provided evidence.** The manuscript presents a highly promising and novel approach, but the provided text is insufficient to verify the core claims. The technical soundness, reproducibility, and statistical rigor of the results are not assessable. A full review of the complete manuscript, including methods, figures, tables, and supplementary information, is required. The authors must address the major concerns regarding methodological detail and statistical analysis before the case for publication can be established.