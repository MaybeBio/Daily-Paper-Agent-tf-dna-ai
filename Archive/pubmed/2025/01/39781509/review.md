## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, conclusions, data availability)
- **Assessment boundary** Scientific and technical evaluation of the ProPr54 model, its validation, performance comparisons, and the associated web server
- **Shared manuscript claim summary** The authors present ProPr54, a hybrid CNN-BiLSTM model for predicting σ54 promoter binding sites and regulon members in bacterial genomes. They claim it outperforms existing tools (Liu et al., iProm-Sigma54, FIMO) across multiple bacterial species, generalizes to organisms without experimentally validated σ54 binding sites, and is the first reliable in silico method for this task. A web server is provided.
- **Visible evidence base** Abstract, full methods, results and discussion sections, figures referenced (Figures 1–7), supplementary figures referenced (S1, S2), supplementary tables referenced (S1, S2), GitHub repository, Zenodo data deposit
- **Missing materials affecting confidence** Figures and supplementary materials were not provided. Exact hyperparameter values, model architecture details (layer sizes, kernel widths, pooling, etc.) are only partially described and referenced to GitHub. The full dataset composition (e.g., exact number of positive sequences per organism, negative set construction details) is not fully specified in the text. The web server URL in the abstract (http://propr54.molgenrug.nl) differs from the one in the methods (http://sigma54.molgenrug.nl), and neither was tested.

## Reviewer
- **Overall assessment** The manuscript addresses a genuine gap in bacterial genomics: the lack of accurate, genome-scale tools for σ54 promoter and regulon prediction. The authors have assembled a curated dataset of experimentally validated σ54 binding sites from 36 organisms, trained a hybrid CNN-BiLSTM model, and benchmarked it against existing tools using leave-one-group-out cross-validation. The reported performance improvements are substantial and, if reproducible, would represent a meaningful advance. However, the manuscript has several weaknesses that currently prevent full endorsement. The evaluation of generalization to organisms without validated binding sites is indirect and lacks a clear ground truth. The comparison with existing tools, while favorable, is not accompanied by sufficient detail on how those tools were configured or whether their original training data overlap with the test set. The web server is a valuable contribution, but the discrepancy in URLs and lack of testing details are concerning. The writing is generally clear but contains some redundancy and occasional overstatement. Overall, the work is promising and likely of interest to the bacterial genomics and bioinformatics communities, but the evidence as presented does not fully establish all claims.

- **Who would be interested in the results, and why** Researchers studying bacterial gene regulation, particularly those working on σ54-dependent transcription, nitrogen metabolism, flagellar biosynthesis, motility, and virulence in pathogenic bacteria. The tool would also be useful for bioinformaticians developing promoter prediction methods and for experimentalists seeking to validate ChIP-seq or differential expression data. The web server's integration with functional annotation (COG, KEGG, operon predictions) broadens its appeal to genome annotators and systems biologists.

- **Major Strengths**
  - The dataset is larger and more taxonomically diverse than those used in previous σ54 prediction tools, which is a clear improvement.
  - The leave-one-group-out cross-validation strategy is methodologically sound and more rigorous than the hold-out validation used in prior work.
  - The hybrid CNN-BiLSTM architecture is well motivated by the need to capture both local motifs and longer-range sequence context.
  - The performance comparison against three existing tools (Liu et al., iProm-Sigma54, FIMO) on multiple bacterial genomes is a strong feature.
  - The web server with integrated regulon prediction, operon analysis, and functional annotation is a practical and potentially widely used resource.
  - The error analysis (GC content, motif position, PWM scores) provides useful insight into model limitations.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "ProPr54 exhibits high performance when tested on various bacterial species, highly surpassing other available σ54 regulon identification methods."
- **Evidence pointer** Results & discussion, "Model architecture optimization" and "Model validation on unseen data" sections; Figures 2, 3, 5
- **Concern** The performance comparison with Liu et al., iProm-Sigma54, and FIMO is presented as a key result, but the manuscript does not specify how these tools were configured, whether their default parameters were used, or whether the test data overlap with their training data. For example, iProm-Sigma54 was trained predominantly on E. coli sequences; applying it to other organisms without retraining may unfairly disadvantage it. Similarly, FIMO's cutoff of 1e-5 is mentioned, but it is unclear if this is the optimal threshold for each organism. Without these details, the comparison may not be a fair assessment of the tools' capabilities.
- **Why it matters** The claim of "highly surpassing" other methods is central to the manuscript's contribution. If the comparison is not fair or reproducible, the conclusion is weakened.
- **Resolution test** Provide explicit details on how each tool was run (parameters, thresholds, any retraining), and discuss whether the test organisms were represented in the training data of the compared tools. If possible, include a sensitivity analysis with varying thresholds for FIMO and other tools.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance / claim support
- **Claim pointer** "analysis on bacterial genomes, which have no experimentally validated σ54 binding sites, demonstrates the generalization of the model."
- **Evidence pointer** Results & discussion, "Prediction of σ54 promoters in organisms with no experimentally verified σ54 sigmulon" section; Figure 5
- **Concern** The generalization analysis on organisms without validated binding sites (Y. pestis, B. burgdorferi, P. stutzeri) uses precision against a BLAST-based regulon as the only metric. This is circular to some degree, since the BLAST regulon is itself a prediction, and the precision calculation depends on the quality of that reference. The manuscript does not report recall or any other metric for these organisms, nor does it discuss the limitations of using BLAST-based regulons as a proxy for ground truth. The claim of "demonstrates generalization" is therefore not fully supported.
- **Why it matters** Generalization to novel organisms is a key selling point of the tool. If the evaluation is not robust, the claim is overstated.
- **Resolution test** Provide additional metrics (e.g., recall, F1) and a more detailed discussion of the limitations of the BLAST-based regulon as a reference. Consider validating predictions on a subset of these organisms using an independent method (e.g., ChIP-seq data if available, or literature-curated binding sites).

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "ProPr54 is the first reliable insilico method for predicting σ54 binding sites"
- **Evidence pointer** Abstract; Introduction; Results & discussion
- **Concern** The claim of being "the first reliable" method is strong and not fully justified. The authors acknowledge prior tools (iProm-Sigma54, iPro54-PseKNC, Liu et al.) but dismiss them based on performance. However, "reliable" is not defined quantitatively. The manuscript does not report confidence intervals, calibration, or a formal statistical test of superiority. Additionally, the term "insilico" is a typographical error ("in silico") that should be corrected.
- **Why it matters** Overclaiming novelty or reliability can undermine the credibility of the work. A more measured claim, supported by statistical evidence, would be more appropriate.
- **Resolution test** Define "reliable" in operational terms (e.g., precision/recall thresholds, calibration) and provide statistical evidence (e.g., confidence intervals, significance tests) for the superiority of ProPr54 over existing tools.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility
- **Claim pointer** "The data underlying this article are available on Github at https://github.com/annejong/ProPr54, and on Zenodo at https://doi.org/10.5281/zenodo.14531825."
- **Evidence pointer** Data availability section
- **Concern** The manuscript states that data and code are available, but the provided URLs were not tested during review. The GitHub repository is referenced for "more detailed information on the architecture and hyperparameters," but the manuscript itself does not include a complete description of the model architecture, training procedure, or hyperparameter values. This makes it difficult to assess the reproducibility of the results from the manuscript alone.
- **Why it matters** Reproducibility is a core requirement for computational biology tools. Without a complete description in the manuscript or a verified repository, the work cannot be fully evaluated.
- **Resolution test** Ensure the GitHub repository is publicly accessible and contains all code, data, and a detailed README. Include a summary of key hyperparameters and architecture details in the manuscript or supplement.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract states "ProPr54 is the first reliable insilico method" but "insilico" is a typo. Also, the abstract does not mention the web server URL, which is a key deliverable.
- **Required correction** Correct "insilico" to "in silico" and include the web server URL in the abstract.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Web server URL
- **Evidence pointer** Abstract vs. Methods
- **Issue** The abstract lists the web server as http://propr54.molgenrug.nl, while the methods section lists http://sigma54.molgenrug.nl. This inconsistency is confusing and may indicate a broken link.
- **Required correction** Verify the correct URL and use it consistently throughout the manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Dataset description
- **Evidence pointer** Materials and methods, "Dataset generation for prediction of σ54 binding sites"
- **Issue** The dataset description mentions 36 organisms in the training set but does not provide a breakdown of how many binding sites come from each organism, nor the total number of positive and negative sequences after data augmentation. This information is important for assessing potential taxonomic bias.
- **Required correction** Provide a supplementary table listing the number of binding sites per organism and the final dataset sizes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical rigor
- **Affected element** Error analysis
- **Evidence pointer** Results & discussion, "Model architecture optimization" section
- **Issue** The error analysis reports significant differences (P < 0.001) between groups but does not specify which statistical test was used or whether multiple testing corrections were applied.
- **Required correction** Specify the statistical test used and whether corrections for multiple comparisons were applied.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Figure 4
- **Evidence pointer** Results & discussion, "Prediction of σ54 promoters with perfect positioning" section
- **Issue** The text states that iProm-Sigma54 and FIMO achieved a recall of 0 on five out of seven organisms, but it is unclear whether this is due to the tools failing to identify any true positives or due to a mismatch in the input format (e.g., the tools may not accept full intergenic regions).
- **Required correction** Clarify whether the tools were run on the same input format and whether any preprocessing was applied to accommodate their requirements.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability
- **Affected element** Conclusions
- **Evidence pointer** Conclusions section
- **Issue** The conclusion states "ProPr54 is the first tool able to identify the σ54 regulon" but the manuscript does not clearly define what constitutes "the regulon" in this context (i.e., the set of genes under σ54 control). The distinction between promoter prediction and regulon prediction could be clarified.
- **Required correction** Define "regulon" operationally and explain how the tool's output relates to regulon membership.

- **Technical failings that need to be addressed before the case is established**
  - R1-M1: Fairness and reproducibility of tool comparisons
  - R1-M2: Robustness of generalization claims
  - R1-M4: Completeness of model description and repository verification

- **Assessment against Nature-style criteria**
  - **Originality** The work is original in its application of a hybrid CNN-BiLSTM architecture to σ54 promoter prediction and in its integration of promoter prediction with regulon inference via protein homology and operon analysis. However, the individual components (CNN for promoter prediction, BLAST for regulon inference) are not novel in themselves. The novelty lies in the combination and the scale of the curated dataset.
  - **Scientific importance** σ54 is an understudied but biologically significant sigma factor, and accurate prediction tools are lacking. The potential to predict regulons in pathogenic bacteria has clear translational relevance. The work addresses a real need.
  - **Interdisciplinary readership** The work is primarily of interest to microbiologists and bioinformaticians. The web server's integration with functional annotation may attract a broader genomics audience, but the manuscript's focus on model architecture and performance metrics may limit its accessibility to non-specialists.
  - **Technical soundness** The methodology is generally sound, but the concerns above (fairness of comparisons, robustness of generalization evaluation, completeness of model description) need to be addressed. The leave-one-group-out cross-validation is a strength.
  - **Readability for nonspecialists** The manuscript is clearly written but assumes familiarity with machine learning concepts and bacterial promoter structure. The abstract is accessible, but the methods section is dense. A brief explanation of σ54 biology and the significance of the -24/-12 motif would improve accessibility.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is valuable, and the reported performance is promising. However, the manuscript currently does not fully establish the claims of superiority and generalization due to the concerns outlined above. Addressing these issues would significantly strengthen the work.

## Risk / unsupported claims
- The claim that ProPr54 is "the first reliable" tool is not quantitatively supported.
- The claim of "demonstrates generalization" to organisms without validated binding sites is based on a circular evaluation using BLAST-based regulons.
- The performance comparison with existing tools may not be fair or reproducible without additional details.
- The web server URL inconsistency raises concerns about the availability and stability of the resource.
- The statement that "ProPr54 is the first tool able to accurately identify the σ54 regulon" is not fully supported, as the manuscript does not clearly define the regulon prediction task or its evaluation.