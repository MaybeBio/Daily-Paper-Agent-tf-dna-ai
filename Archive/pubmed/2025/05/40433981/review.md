## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability)
- **Assessment boundary** Scientific validity, methodological soundness, claims versus evidence, reproducibility, and fit for a high-impact generalist journal
- **Shared manuscript claim summary** The authors present SCIG, a machine learning method that integrates genetic sequence features with single-cell RNA expression data to identify cell identity genes (CIGs) without comparison to other cell types. They further present SCIGNet, a companion model to identify master transcription factors (TFs) from CIG network features. Claims include: (1) CIGs have distinctive genetic sequence signatures; (2) SCIG accurately recovers known CIGs across human and mouse; (3) CIG scores outperform expression values in network and trajectory analyses; (4) tissue microenvironment refines EC identity beyond master TFs.
- **Visible evidence base** Full text with methods, results, figures referenced (Fig 1–6, Supplementary Figs S1–S10), supplementary tables referenced (S1–S6), data availability statement, code repository link
- **Missing materials affecting confidence** Figures and supplementary tables not provided; no access to code or data; no benchmark comparisons to existing tools (e.g., SCENIC, CellTypist, garnett) beyond CellNet; no statistical details for several comparisons; no details on hyperparameter tuning or reproducibility of the machine learning pipeline

## Reviewer

- **Overall assessment** The manuscript addresses a timely and important problem: identifying cell identity genes from single-cell data without requiring cross-cell-type comparisons. The core idea, combining genetic sequence features with expression data, is conceptually interesting and potentially useful. However, the evidence provided in the text is insufficient to fully evaluate the method's performance, robustness, and novelty relative to existing approaches. Several claims are supported only by descriptive statements without quantitative backing. The manuscript would benefit from clearer benchmarking, more rigorous statistical reporting, and a more critical discussion of limitations. The work is potentially publishable in a specialized bioinformatics journal, but the current evidence does not establish the case for a high-impact generalist audience.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians developing tools for single-cell analysis would be the primary audience. Researchers studying cell differentiation, developmental biology, and regenerative medicine may also find the CIG and master TF predictions useful for hypothesis generation. The claim that CIG scores improve trajectory analysis could interest researchers using scRNA-seq for lineage tracing. However, the lack of direct comparison to widely used tools (e.g., SCENIC, CellTypist) limits the immediate practical value for these groups.

- **Major strengths**
  1. The conceptual framing is clear: using genetic sequence features as a proxy for epigenetic regulation is a novel angle that could circumvent the difficulty of profiling epigenomes at single-cell resolution.
  2. The method is designed to work without cross-cell-type comparisons, which is a practical advantage for analyzing heterogeneous or rare cell populations.
  3. The application to multiple datasets (endothelial cells, heart, neurogenesis, mouse) demonstrates generalizability.
  4. The authors provide a public code repository and data availability statement, supporting reproducibility in principle.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / validation
- **Claim pointer** "SCIG uncovers the identity genes of a cell without a need for comparison to other cells" and "SCIG successfully recaptured the known CIGs with an accuracy of 90.4%, sensitivity of 91.2%, and specificity of 89.6%"
- **Evidence pointer** Results section, Fig 2, Supplementary Fig S2; location not provided
- **Concern** The central claim that SCIG can identify CIGs without cross-cell-type comparison is not convincingly validated. The training data for the model are derived from curated CIG lists from 10 cell types, which were themselves defined by literature review that likely involved cross-cell-type comparisons. The evaluation metrics (accuracy, sensitivity, specificity) are reported for recapturing these same curated CIGs, which is a circular validation. The authors do not provide an independent validation strategy, such as prospective experimental validation or comparison against a held-out set of CIGs defined by orthogonal criteria.
- **Why it matters** If the model is trained and tested on the same curated lists, the reported performance may reflect overfitting to the training set rather than genuine generalizability. The claim that SCIG works "without comparison to other cells" is a key selling point, but the validation does not demonstrate this in a way that distinguishes SCIG from methods that implicitly rely on cross-cell-type information through training data.
- **Resolution test** Provide an independent validation set of CIGs not used in training, ideally from experimental perturbation data (e.g., knockdown/overexpression phenotypes) or from a different curation source. Report performance on this held-out set. Alternatively, demonstrate that SCIG trained on one set of cell types can predict CIGs in a completely new cell type with no overlap in training data, and compare this to a baseline method that uses only expression data.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness / benchmarking
- **Claim pointer** "SCIGNet always showed a better performance in recapturing the known master TFs" compared to CellNet
- **Evidence pointer** Results section, Fig 3I; location not provided
- **Concern** The comparison to CellNet is the only benchmark presented, and it is not described in sufficient detail. The authors do not report the exact metrics, the statistical significance of the difference, or the hyperparameter settings for CellNet. More importantly, no comparison is made to more recent and widely used tools for master TF inference, such as SCENIC, which is the de facto standard in the field. Without benchmarking against current state-of-the-art methods, the claim of superior performance is not established.
- **Why it matters** For a method to be adopted by the community, it must demonstrate clear advantages over existing tools. The absence of comparison to SCENIC or similar tools makes it impossible to assess whether SCIGNet offers a meaningful improvement or merely a comparable alternative.
- **Resolution test** Benchmark SCIGNet against SCENIC, and optionally against other tools (e.g., VIPER, ARACNe-based methods), on the same datasets with identical evaluation criteria. Report precision, recall, F1, and AUROC with confidence intervals. Provide details on parameter settings for all methods.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility / technical soundness
- **Claim pointer** "SCIG is publicly available at https://doi.org/10.5281/zenodo.14726426"
- **Evidence pointer** Data availability section; location not provided
- **Concern** The manuscript does not provide sufficient detail on the implementation of SCIG and SCIGNet to allow independent reproduction. The feature engineering (680 features reduced to 73, then to 19) is described at a high level, but the exact definitions of all features, the preprocessing steps, and the hyperparameter choices for the logistic regression models are not fully specified. The authors state that code is available, but the manuscript should contain enough detail for a skilled researcher to reimplement the method without access to the code.
- **Why it matters** Reproducibility is a core requirement for computational methods. If the method cannot be reimplemented from the manuscript alone, the scientific claims cannot be independently verified.
- **Resolution test** Provide a complete description of all 680 features, the feature selection procedure, and the model training details in the main text or supplementary materials. Include a pseudocode or algorithmic description of the SCIG and SCIGNet pipelines. Ensure the code repository includes a README with instructions for running the method on example data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance / novelty
- **Claim pointer** "CIGs exhibit distinctive genetic sequence signatures, e.g. unique enrichment patterns of cis-regulatory elements"
- **Evidence pointer** Results section, Fig 1; location not provided
- **Concern** The observation that CIGs have distinct sequence features is presented as a novel finding, but the manuscript does not discuss how this relates to prior work on sequence features of cell-type-specific genes. For example, it is well established that tissue-specific genes have distinct promoter architectures, CpG content, and transcription factor binding site densities. The authors should more carefully position their findings in the context of this literature to establish what is genuinely new.
- **Why it matters** If the sequence features are already known to distinguish cell-type-specific genes, the novelty of SCIG is reduced to the specific machine learning implementation rather than the underlying biological insight.
- **Resolution test** Add a discussion section that explicitly compares the sequence features identified in this study with those reported in prior studies of cell-type-specific or tissue-specific genes. Highlight which features are novel and which are confirmatory.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness / statistical rigor
- **Claim pointer** "CIG score is better than the expression level for enriching cell identity pathways" and "CIG-based clustering better reflects differentiation trajectory"
- **Evidence pointer** Results section, Figs 4–6; location not provided
- **Concern** The comparisons between CIG score-based and expression-based analyses are described qualitatively. For example, the statement that CIG scores "more accurately reflected cell types and their differentiation trajectory" is not supported by quantitative metrics. The authors report a Silhouette coefficient comparison for the neurogenesis dataset, but this is a single internal validity metric and does not establish biological relevance. No statistical tests are reported for the pathway enrichment differences.
- **Why it matters** The claim that CIG scores are superior to expression values is a key practical contribution. Without quantitative, statistically rigorous comparisons, this claim is not supported.
- **Resolution test** Provide quantitative metrics for clustering quality (e.g., adjusted Rand index against known labels, normalized mutual information) and trajectory quality (e.g., correlation with known developmental pseudotime). Report effect sizes and confidence intervals for pathway enrichment differences. Use permutation tests or bootstrapping to establish statistical significance.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity / readability
- **Affected element** Abstract
- **Evidence pointer** Abstract; location not provided
- **Issue** The abstract states that SCIG "surpassed expression value in network analysis" but does not specify the comparison metric or the magnitude of improvement.
- **Required correction** Include a specific quantitative result in the abstract, such as the AUROC improvement or the percentage increase in pathway enrichment.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness / completeness
- **Affected element** Methods, feature selection
- **Evidence pointer** Materials and methods, "Features filtering and selection"; location not provided
- **Issue** The description of the forward feature selection is incomplete. The authors state that "the forward selection algorithm" was used but do not specify the stopping criterion beyond "no further enhancement in model performance." It is unclear what metric was used to determine "enhancement" and whether the selection was performed on the training set only or with cross-validation.
- **Required correction** Specify the exact stopping criterion, the metric used, and whether the selection was nested within the cross-validation procedure to avoid selection bias.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity / readability
- **Affected element** Results, Fig 4
- **Evidence pointer** Results section, Fig 4; location not provided
- **Issue** The description of the hdWGCNA analysis is brief. It is unclear how the "CIG score matrix" was used as input, and whether the network construction parameters were optimized for this input type.
- **Required correction** Provide more detail on the hdWGCNA parameters and how the CIG score matrix was formatted for input. Justify the choice of parameters or state that default parameters were used.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness / completeness
- **Affected element** Results, EC tissue analysis
- **Evidence pointer** Results section, Fig 6; location not provided
- **Issue** The analysis of EC identity across 15 tissues is descriptive. The authors list examples of conserved and tissue-specific CIGs but do not provide a systematic quantification of the conservation patterns.
- **Required correction** Provide a quantitative summary, such as the distribution of Tau scores across all CIGs and master TFs, and a statistical test for the difference between CIGs and master TFs.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity / readability
- **Affected element** Discussion
- **Evidence pointer** Discussion; location not provided
- **Issue** The discussion of the tissue microenvironment's role in EC identity refinement is speculative and not directly supported by the data presented. The authors suggest a mechanism involving cell-cell communication but do not provide evidence for this.
- **Required correction** Either soften the speculation or provide additional analysis (e.g., ligand-receptor interaction analysis) to support the claim.

- **Technical failings that need to be addressed before the case is established**
  1. Circular validation of CIG prediction (R1-M1)
  2. Insufficient benchmarking against state-of-the-art tools (R1-M2)
  3. Incomplete methodological detail for reproducibility (R1-M3)
  4. Lack of quantitative, statistically rigorous comparisons for CIG score superiority claims (R1-M5)

- **Assessment against Nature-style criteria**
  - **Originality**: Moderate. The combination of sequence features with expression data for CIG identification is a novel angle, but the underlying concept of using regulatory sequence features to predict gene function is not entirely new. The method is an incremental advance over existing approaches.
  - **Scientific importance**: Moderate. The problem of identifying CIGs is important, and a reliable computational method would be valuable. However, the manuscript does not demonstrate a clear advantage over existing tools, which limits its immediate impact.
  - **Interdisciplinary readership**: Limited. The manuscript is written for a specialized bioinformatics audience. The biological insights (e.g., EC tissue-specific CIGs) are presented at a descriptive level and are unlikely to attract broad interdisciplinary interest.
  - **Technical soundness**: Currently insufficient. The validation strategy is circular, the benchmarking is incomplete, and the statistical rigor is lacking. These issues must be addressed before the technical claims can be accepted.
  - **Readability for nonspecialists**: The abstract and introduction are accessible, but the results section assumes familiarity with machine learning and single-cell analysis terminology. The manuscript would benefit from a brief explanation of key concepts (e.g., CIG score, Tau score) for a broader audience.

- **Recommendation posture** Currently not established from the provided evidence. The core idea is promising, but the validation and benchmarking are insufficient to support the claims. The authors should address the major concerns, particularly the circular validation and the lack of comparison to state-of-the-art tools, before the manuscript can be considered for publication. If these issues are resolved, the manuscript could be suitable for a specialized bioinformatics journal, but it is unlikely to meet the bar for a high-impact generalist journal in its current form.

## Risk / unsupported claims
- The claim that SCIG identifies CIGs "without a need for comparison to other cells" is not supported by the validation strategy, which relies on curated CIG lists that may implicitly encode cross-cell-type information.
- The claim that CIG scores "surpassed expression value in network analysis" is not quantitatively supported.
- The claim that "the tissue microenvironment is a critical supplement to master TFs for cell identity refinement" is speculative and not directly tested.
- The claim that SCIGNet "always showed a better performance" than CellNet is not supported by sufficient detail on the comparison.
- The generalizability of SCIG to cell types beyond those used in training is not demonstrated.