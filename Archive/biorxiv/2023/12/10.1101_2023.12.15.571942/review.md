## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) as provided
- **Assessment boundary** Scientific content, methodological soundness, claims versus evidence, interpretability of results, and reproducibility based solely on the supplied material
- **Shared manuscript claim summary** The authors present DeepPBS, a geometric deep-learning model that predicts protein-DNA binding specificity from protein-DNA complex structures. The model is claimed to be generalizable across protein families, interpretable via heavy atom-level importance scores, applicable to computationally predicted structures, and fast enough for molecular dynamics trajectory analysis. The authors further claim that residue-level importance scores correlate with alanine scanning mutagenesis data.
- **Visible evidence base** Main text figures referenced (Figs. 1-5), supplementary figures and tables referenced (Fig. S1-S9, Table S1, Movie S1), methods section, data and code availability statements
- **Missing materials affecting confidence** Supplementary sections 1-9, all figures and tables, Movie S1, detailed architecture specifications, hyperparameter settings, training curves, and full benchmark results are not provided in the supplied material. These are essential for verifying the claims.

## Reviewer
- **Overall assessment** The manuscript addresses a significant and timely problem in computational biology: predicting protein-DNA binding specificity from structural data in a generalizable and interpretable manner. The proposed framework, DeepPBS, is conceptually novel in its use of geometric deep learning on protein-DNA complexes with a symmetrized DNA representation. The authors demonstrate applications across multiple families, on predicted structures, and on MD trajectories, which collectively suggest broad utility. However, the provided material lacks the detailed evidence needed to fully assess the validity of the central claims. Key performance metrics, benchmark details, and interpretability validations are referenced but not shown. The correlation with alanine scanning data is promising but the strength of the evidence cannot be evaluated without the actual regression plot and statistical details. The manuscript is well written and the conceptual framing is strong, but the current submission does not provide sufficient evidence to establish the case.

- **Who would be interested in the results, and why** Computational biologists studying protein-DNA interactions, developers of deep learning methods for structural biology, experimentalists studying transcription factor binding specificity, and researchers interested in interpretable AI for molecular systems. The potential to guide mutagenesis experiments and to work with predicted structures would appeal to a broad audience in genomics and structural biology.

- **Major strengths** The problem is important and the proposed approach is conceptually novel. The use of a symmetrized DNA representation to remove sequence identity while preserving shape is an elegant design choice. The model is designed to be family-agnostic, which is a significant advance over family-specific methods. The interpretability mechanism via edge perturbation is a thoughtful addition that could provide biological insight. The demonstrated applications to predicted structures and MD trajectories suggest practical utility beyond static experimental structures.

- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that DeepPBS achieves strong performance across protein families, with quantitative metrics shown in Fig. 2a-d.
  - **Evidence pointer** Fig. 2a-d, Fig. S5a-c, Methods section
  - **Concern** The actual performance numbers, benchmark construction details, and comparison baselines are not provided in the supplied material. The text states that DeepPBS outperforms its components in isolation and that adding DNA sequence information improves performance, but the magnitude of these effects and the statistical significance are not reported.
  - **Why it matters** Without quantitative results, the central claim of predictive accuracy cannot be assessed. The reader cannot determine whether the model performs adequately for real-world use.
  - **Resolution test** Provide the full benchmark results, including performance values, error bars, and statistical tests comparing DeepPBS to baselines and to existing methods where applicable.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The authors claim that residue-level importance scores from DeepPBS correlate with alanine scanning mutagenesis data, with a Pearson correlation coefficient of 0.564 (Fig. 4i).
  - **Evidence pointer** Fig. 4i, Table S1, Methods section
  - **Concern** The regression plot and the full set of data points are not shown in the supplied material. The number of residues, the diversity of proteins, and the statistical significance of the correlation are not reported. The choice of log-sum aggregation is not justified.
  - **Why it matters** This correlation is a key validation of the interpretability claim. Without seeing the data distribution and the statistical context, the reader cannot judge whether the correlation is meaningful or driven by a few outliers.
  - **Resolution test** Show the full regression plot with all data points, report the number of residues and proteins, provide a confidence interval for the correlation, and justify the aggregation method.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Reproducibility
  - **Claim pointer** The authors state that DeepPBS can be applied to computationally predicted structures from RFNA and MELD-DNA, and that the pipeline is competitive with the family-specific method rCLAMP.
  - **Evidence pointer** Fig. 3a-i, Fig. S9, Supplementary Section 7
  - **Concern** The details of the structure prediction pipeline, the selection of initial DNA sequences, the number of proteins tested, and the comparison with rCLAMP are not provided. The claim of competitiveness is made without showing the actual comparison data.
  - **Why it matters** The utility of DeepPBS depends on its ability to work with predicted structures, which are increasingly common. Without a clear description of the pipeline and the comparison, the claim cannot be verified.
  - **Resolution test** Provide the full details of the structure prediction pipeline, the dataset used, and the quantitative comparison with rCLAMP, including the number of cases where each method performs better.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that the symmetrized DNA representation preserves the shape of the DNA helix while removing sequence identity.
  - **Evidence pointer** Fig. 1c, Fig. S2, Supplementary Section 3
  - **Concern** The description of the symmetrization scheme is incomplete. The seven atomic interaction positions in the major and minor grooves and the four positions for sugar and phosphate are mentioned, but the exact definition of these positions and how they are derived from the base-pair frame is not provided.
  - **Why it matters** The symmetrized representation is a key innovation of the method. Without a full description, the method cannot be reproduced or fully understood.
  - **Resolution test** Provide a complete description of the symmetrization scheme, including the definition of the atomic positions and the mathematical transformation.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract
  - **Issue** The abstract states that DeepPBS can "aid in the modeling of protein-DNA complexes" but does not explain how this is achieved.
  - **Required correction** Clarify the mechanism by which DeepPBS aids in modeling, or remove this claim if it is not a central contribution.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Methods
  - **Evidence pointer** Methods section
  - **Issue** The performance metrics section defines negative MAE and negative RMSE but does not explain why these are preferred over standard MAE and RMSE.
  - **Required correction** Provide a brief justification for using negative values.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Discussion
  - **Evidence pointer** Discussion section
  - **Issue** The discussion mentions the potential for DeepPBS to predict mismatched binding specificity but does not elaborate on how the architecture would be adapted for this.
  - **Required correction** Either expand on this point or remove it to avoid speculation.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Data availability
  - **Evidence pointer** Data Availability section
  - **Issue** The data and code are available at a GitHub repository and Zenodo archive, but the specific contents of these resources are not described.
  - **Required correction** Provide a brief description of what is included in the repository, such as training scripts, preprocessed data, and model weights.

- **Technical failings that need to be addressed before the case is established** The lack of quantitative performance data in the main text is a critical gap. The benchmark results, cross-validation metrics, and comparisons with baselines are referenced but not shown. The correlation with alanine scanning data is presented as a single number without the underlying data. The structure prediction pipeline and comparison with rCLAMP are described qualitatively. These issues must be resolved by providing the actual data and analysis.

## Risk / unsupported claims
- The claim that DeepPBS outperforms its components in isolation (Fig. 2a) is unsupported without the actual performance numbers.
- The claim that DeepPBS is competitive with rCLAMP (Fig. 3h-i) is unsupported without the comparison data.
- The claim that residue-level importance scores correlate with alanine scanning data (Fig. 4i) is only partially supported by the reported correlation coefficient, but the full data and statistical context are missing.
- The claim that DeepPBS can be applied to predicted structures and improve modeling is plausible but not fully demonstrated in the provided material.
- The claim that DeepPBS is robust to small dynamical fluctuations in MD trajectories is not quantitatively supported.