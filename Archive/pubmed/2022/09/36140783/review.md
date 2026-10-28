## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific content, methodology, claims, and evidence presented in the manuscript
- **Shared manuscript claim summary** The authors propose multinomial convolutions as an interpretable alternative to standard convolutions in CNNs for genomic sequence modeling. They implement this in a model called MuSeAM and demonstrate on a human liver enhancer MPRA dataset that it achieves higher predictive performance than conventional CNNs while learning filters that directly recapitulate known transcription factor motifs without post hoc analysis.
- **Visible evidence base** Abstract, Introduction, Results (Sections 2.1–2.4), Discussion, Methods (Sections 4.1–4.8), Figure 1 and Figure 2 referenced, Figure S1 referenced
- **Missing materials affecting confidence** Figures and supplementary materials not provided; no code or data availability statement; no detailed hyperparameter search results; no statistical significance testing for performance comparison; no cross-validation variance reported

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting idea: constraining first-layer convolution filters to be multinomial distributions over nucleotides, thereby making them directly interpretable as position weight matrices. The implementation appears straightforward and the authors demonstrate competitive performance on a real dataset. However, the evidence base is thin in several critical areas. The performance comparison against conventional CNNs lacks statistical rigor, the claim of "consistently better results" is not supported by the single dataset presented, and the biological validation of discovered motifs is limited to database matching without functional validation. The novelty relative to existing softmax-normalized approaches is not clearly delineated. The manuscript is clearly written and the method is reproducible in principle, but the strength of the claims exceeds what the presented evidence supports.

- **Who would be interested in the results, and why** Researchers in computational genomics and regulatory genomics who use deep learning for sequence-to-function modeling would be the primary audience. Those interested in interpretable machine learning for biology, particularly motif discovery from CNN models, would also find this relevant. The method offers a potential alternative to post hoc interpretation tools like DeepSHAP or TF-MoDISco, which may appeal to practitioners seeking more direct interpretability. The biophysical grounding of the approach may also interest researchers building mechanistic models of gene regulation.

- **Major strengths**
  1. The core idea is conceptually clean and addresses a real limitation of standard CNNs in genomics: the need for post hoc interpretation.
  2. The mathematical formulation is simple and elegant, with the gradient simplification (d ln T_i,j / d X_i,j = 1 − T_i,j) being a nice theoretical contribution.
  3. The authors demonstrate the method on a real, publicly available dataset with a reasonable sample size.
  4. The writing is clear and accessible, with good motivation for the approach.
  5. The authors are appropriately cautious in the Discussion about not overclaiming universal superiority.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor of performance comparison
- **Claim pointer** "MuSeAM fit this dataset with a mean Spearman correlation coefficient of 0.52... the best-performing conventional CNN architecture achieved a mean Spearman correlation value of 0.42, establishing that the multinomial convolution approach of MuSeAM demonstrates considerably higher performance for this dataset."
- **Evidence pointer** Section 2.3, location not provided
- **Concern** The performance comparison between MuSeAM and conventional CNNs is based on a single mean value per model, with no reported variance, confidence intervals, or statistical significance testing. The claim of "considerably higher performance" is not supported without knowing the distribution of Spearman correlations across the 10 folds. A difference of 0.10 in mean Spearman correlation could be within the noise of the cross-validation procedure, especially with only 2440 sequences.
- **Why it matters** The central practical claim of the paper is that multinomial convolutions do not sacrifice accuracy while providing interpretability. If the performance difference is not statistically robust, the advantage of the method is weakened. Readers need to know whether the observed difference is reproducible and meaningful.
- **Resolution test** Report the per-fold Spearman correlations for both models, provide standard deviations or confidence intervals, and perform a paired statistical test (e.g., Wilcoxon signed-rank test) across the 10 folds. If the difference is not significant, temper the claim accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Generalizability of performance claims
- **Claim pointer** "we demonstrate the efficacy of MuSeAM in accurately modeling genomic data" and "consistently provided better results than those derived from the alternative architectures of conventional CNN models"
- **Evidence pointer** Abstract; Section 3, location not provided
- **Concern** The entire empirical evaluation rests on a single dataset (one MPRA experiment in one cell type). The claim of "consistently better results" implies robustness across datasets and conditions, but no such evidence is presented. The Discussion acknowledges this limitation, but the abstract and introduction make broader claims that are not supported by the evidence.
- **Why it matters** Genomic datasets vary widely in their characteristics (sequence length, number of samples, signal-to-noise ratio, regulatory complexity). A method that works well on one liver enhancer dataset may not generalize. The claim of general efficacy is important for the method's adoption, and the current evidence is insufficient.
- **Resolution test** Apply MuSeAM to at least one additional dataset from a different cell type or assay (e.g., a different MPRA dataset, a chromatin accessibility dataset, or a splicing dataset). If additional experiments are not feasible, substantially temper the language in the abstract and introduction to reflect the single-dataset nature of the evidence.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Novelty and differentiation from prior work
- **Claim pointer** "To our best knowledge, the notion of multinomial convolutions has not previously been used for the purpose of motif learning in CNN models."
- **Evidence pointer** Section 3, location not provided
- **Concern** The authors acknowledge a preprint by Ploenzke and Irizarry that pursues a similar goal, and they mention softmax normalization as a related concept. However, the differentiation from these approaches is not fully articulated. The claim of novelty is plausible but not rigorously established. A more thorough literature review and explicit comparison of the mathematical formulation against related approaches would strengthen the novelty claim.
- **Why it matters** If the approach is essentially equivalent to a softmax-normalized convolution with a specific background correction, the novelty contribution is incremental. The authors need to clearly state what is genuinely new about their formulation beyond the specific application context.
- **Resolution test** Provide a formal comparison of the multinomial convolution formulation against softmax-normalized convolutions and the Ploenzke and Irizarry approach, highlighting the specific mathematical and practical differences. If the differences are minor, reframe the contribution as an application and empirical demonstration rather than a novel architectural concept.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Biological validation of discovered motifs
- **Claim pointer** "we found matching TFs for 506 motifs using a motif database search" and "our analysis also revealed six novel motifs"
- **Evidence pointer** Section 2.4, location not provided
- **Concern** The biological validation consists solely of matching learned motifs to known motifs in databases and checking TF expression in HepG2 cells. This is a standard but weak form of validation. The functional relevance of the discovered motifs is not tested (e.g., through mutagenesis, reporter assays, or comparison with independent ChIP-seq data). The claim that the model "can identify known activating and repressing TFs" is based on the sign of fully connected layer weights, which is an indirect inference.
- **Why it matters** For a method whose primary selling point is interpretability, the biological validity of the interpretations is crucial. Database matching can produce false positives, and the sign of weights in a linear layer does not necessarily reflect the true regulatory role of a TF in a complex regulatory context.
- **Resolution test** Provide additional validation, such as comparing learned motifs against ChIP-seq peaks for the identified TFs in HepG2 cells, or testing whether the predicted activating/repressing roles are consistent with known functional annotations. At minimum, acknowledge the limitations of the validation approach more explicitly.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Reproducibility and completeness of methods
- **Claim pointer** "We provide the details in the Methods section" regarding hyperparameter search
- **Evidence pointer** Section 4.7, location not provided
- **Concern** The hyperparameter search is described only in terms of ranges tested, not the actual search procedure (e.g., random search, grid search, Bayesian optimization), the number of configurations evaluated, or the criteria for selecting the final architecture. The optimal hyperparameters are listed for both models, but the process by which they were identified is not transparent. Additionally, no code or data availability statement is provided.
- **Why it matters** Reproducibility is a core expectation for computational methods papers. Without a clear description of the search procedure and access to code, other researchers cannot replicate the results or apply the method to their own data.
- **Resolution test** Provide a detailed description of the hyperparameter search procedure, including the number of configurations tested, the search strategy, and the selection criteria. Include a code availability statement and, ideally, a link to a public repository with the implementation and instructions for reproducing the results.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity of presentation
- **Affected element** Figure 1
- **Evidence pointer** Section 2.1, location not provided
- **Issue** The description of Figure 1A is brief and does not fully explain the schematic. The relationship between the raw parameters X, the transformed kernel T, and the background correction is not visually clear from the text alone.
- **Required correction** Expand the figure legend to clearly explain each component of the schematic, including the role of the background distribution B and the meaning of the α parameter.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4, location not provided
- **Issue** The p-value for the Welch t-test is reported as "<2.2×10−16", which is the smallest value R can report. This is fine, but the test statistic and degrees of freedom are not reported.
- **Required correction** Report the t-statistic and degrees of freedom alongside the p-value for completeness.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation of results
- **Affected element** Section 2.4
- **Evidence pointer** Section 2.4, location not provided
- **Issue** The statement "we found matching TFs for 506 motifs" is ambiguous. It is unclear whether this means 506 out of 512 total motifs (the number of filters in the model) or 506 unique TFs. The denominator is not stated.
- **Required correction** Clarify the total number of motifs considered and the proportion that had database matches.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Discussion completeness
- **Affected element** Section 3
- **Evidence pointer** Section 3, location not provided
- **Issue** The Discussion does not address potential limitations of the multinomial convolution approach, such as the constraint on filter values potentially limiting the representational capacity of the model, or the choice of background distribution affecting results.
- **Required correction** Add a paragraph discussing limitations and potential failure modes of the approach.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Terminology consistency
- **Affected element** Throughout
- **Evidence pointer** Sections 2.1 and 4.4, location not provided
- **Issue** The terms "multinomial convolution" and "multinomial motif" are used somewhat interchangeably. The distinction between the mathematical object (the convolution kernel) and its interpretation (the motif) could be made clearer.
- **Required correction** Define both terms explicitly at first use and maintain consistent usage throughout.

## Risk / unsupported claims
- The claim of "consistently better results" for MuAM over conventional CNNs is unsupported by the single-dataset evidence presented.
- The claim that the approach "does not make any assumptions about the concentration of TFs" is not substantiated with a formal argument or citation.
- The statement that multinomial convolutions "can be used in any new context" is an assertion without demonstration; no examples of application beyond the trained model are provided.
- The claim of novelty ("not previously been used") is plausible but not rigorously established through a comprehensive literature search.
- The biological relevance of the six "novel motifs" is not validated beyond database non-matching, which is weak evidence of novelty.
- The performance difference between MuAM and conventional CNNs (0.52 vs 0.42 Spearman correlation) is presented as meaningful, but no effect size or practical significance is discussed.