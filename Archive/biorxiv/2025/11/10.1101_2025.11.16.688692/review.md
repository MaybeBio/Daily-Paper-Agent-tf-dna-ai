## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, methods, data/code availability, author contributions, competing interests, funding, acknowledgments, footnotes)
- **Assessment boundary** Scientific content, methodology, claims, and evidence as presented in the provided text. No external data or literature verification performed.
- **Shared manuscript claim summary** The manuscript reports the results of the IBIS community challenge, in which participants built models of transcription factor (TF) binding specificity from multi-assay experimental data for 40 human TFs. The authors claim that (1) properly designed deep learning models consistently outperform traditional position weight matrices (PWMs) and other machine learning methods in cross-platform benchmarking, (2) PWMs perform surprisingly well out of the box, being only slightly behind the best deep learning models, and (3) the challenge provides a robust framework and dataset for fair evaluation of TF binding models.
- **Visible evidence base** Abstract, Introduction, Results sections (Design and implementation of the IBIS Challenge; IBIS Solutions and Winners; Triple-A models outperform PWMs, but by a limited margin and only when thoroughly designed; Better TFBS prediction does not necessarily improve recognition of regulatory variant effects; Deeper exploration of the Triple-A models with the IBIS benchmarking suite), Methods sections (Challenge overview, General rules, Experimental data preprocessing, Benchmarking protocols, Ranking strategy, Post-challenge models), Data Availability, Code Availability, Author Contributions, Competing Interests, Funding, Acknowledgments, Footnotes.
- **Missing materials affecting confidence** Figures and tables referenced (Figure 1, 2, 3, 4; Supplementary Figures SF1-SF10; Supplementary Tables ST1-ST2; Supplementary Data SD1; Supplementary Methods) are not provided. Detailed numerical results, performance metric values, statistical significance tests, and full participant method descriptions are not available. The manuscript text alone does not permit independent verification of the benchmarking outcomes or the comparative claims.

## Reviewer
- **Overall assessment** This manuscript describes a large-scale, community-driven benchmarking effort for TF binding specificity models, with a well-designed cross-platform evaluation strategy. The organization of the challenge, the use of hidden test data, and the inclusion of multiple performance metrics are commendable. The main claims, however, are only partially supported by the text provided. The assertion that deep learning models outperform PWMs is presented qualitatively, without quantitative effect sizes or statistical testing in the visible text. The claim that PWMs perform "surprisingly well" is similarly under-supported. The post-challenge analysis of additional deep learning models and the rSNP evaluation are interesting but the results are not fully described. The manuscript would benefit from clearer presentation of the quantitative benchmarking results and a more critical discussion of the limitations of the evaluation framework.
- **Who would be interested in the results, and why** Researchers in regulatory genomics, computational biology, and machine learning applied to genomics would be interested. The manuscript provides a benchmark dataset and evaluation protocol that could serve as a standard for future TF binding model development. The comparative analysis of PWMs versus deep learning approaches is directly relevant to practitioners building such models. The rSNP evaluation adds a practical dimension that would interest those studying regulatory variant effects.
- **Major strengths** (1) The challenge design is rigorous, with clear separation of training and test data, chromosome-level holdouts, and pre-announced evaluation metrics. (2) The use of multiple experimental platforms and cross-platform evaluation is a significant strength, as it tests generalization rather than platform-specific overfitting. (3) The inclusion of both primary (A2G, G2A) and secondary (WET) disciplines provides a comprehensive assessment. (4) The post-challenge evaluation of additional models, including DNA language models, adds depth. (5) The development of the bibis package and the public availability of data and code are valuable contributions to the community.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (quantitative support for the headline claim), R1-M2 (statistical significance of performance differences), R1-M3 (rSNP evaluation methodology and interpretation), R1-M4 (generalizability of the findings beyond the specific dataset).
- **Assessment against Nature-style criteria**  
  *Originality*: The manuscript is original in its scale and design, but the core question (deep learning vs. PWMs for TF binding) is not new. The novelty lies in the community challenge format and the cross-platform evaluation.  
  *Scientific importance*: The findings are of moderate importance. They confirm that deep learning can outperform PWMs but also show that PWMs remain competitive, which is a useful but not transformative result. The benchmark dataset and tools are potentially more valuable than the specific findings.  
  *Interdisciplinary readership*: The topic is of interest to computational biologists, machine learning researchers, and experimental biologists studying gene regulation. The writing is accessible but assumes familiarity with TF binding assays and motif models.  
  *Technical soundness*: The challenge design is sound, but the visible text does not provide sufficient quantitative detail to fully assess the technical soundness of the benchmarking results. The rSNP evaluation is described but not fully validated.  
  *Readability for nonspecialists*: The abstract and introduction are clear, but the results and methods sections are dense and would be challenging for nonspecialists. The manuscript would benefit from a more accessible summary of the key findings and their implications.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript describes a valuable community resource and a well-designed benchmarking effort. However, the main claims require stronger quantitative support and clearer presentation of the results. The rSNP analysis needs more careful interpretation. If these issues are addressed, the manuscript would be suitable for publication in a high-impact journal.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "Benchmarking demonstrated a consistent advantage of properly designed deep learning models over traditional position weight matrices and other machine learning methods."
- **Evidence pointer** Results section "Triple-A models outperform PWMs, but by a limited margin and only when thoroughly designed"; Figure 2; Supplementary Figure SF3
- **Concern** The claim of consistent advantage is stated qualitatively, but the visible text does not provide quantitative effect sizes, confidence intervals, or the number of TFs for which the advantage holds. The normalized log2-odds metric is described, but the actual values are not reported in the text. Without these numbers, the reader cannot assess the magnitude or consistency of the advantage.
- **Why it matters** The headline claim of the manuscript depends on this comparison. If the advantage is small or inconsistent across TFs, the conclusion would be substantially weakened. The current presentation does not allow the reader to evaluate this.
- **Resolution test** Provide a table or figure showing the distribution of normalized performance scores for all models across all TFs and platforms, with summary statistics (median, interquartile range) and the proportion of TFs for which the best deep learning model outperforms the best PWM. Include confidence intervals or a statistical test (e.g., Wilcoxon signed-rank test) comparing the best deep learning model to the best PWM per TF.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** "the top-scoring triple-A models clearly outperformed PWM-based solutions from the competition and MEX"
- **Evidence pointer** Results section "Triple-A models outperform PWMs, but by a limited margin and only when thoroughly designed"; Figure 2; Supplementary Figure SF4
- **Concern** The text states that top-scoring models "clearly outperformed" PWMs, but no statistical significance testing is described. Given the variability across TFs and platforms, it is unclear whether the observed differences are robust or could be due to chance. The ranking stability analysis (1000 random subsamples) is mentioned for team rankings, but not for the PWM versus triple-A comparison.
- **Why it matters** Without statistical testing, the claim of superiority is not established. The reader cannot distinguish a robust effect from a few favorable TFs driving the average.
- **Resolution test** Perform a per-TF paired comparison between the best triple-A model and the best PWM (or MEX) for each platform, and report the proportion of TFs where the triple-A model wins, along with a sign test or Wilcoxon signed-rank test p-value. Report effect sizes with confidence intervals.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodology and interpretation
- **Claim pointer** "Better TFBS prediction does not necessarily improve recognition of regulatory variant effects"
- **Evidence pointer** Results section "Better TFBS prediction does not necessarily improve recognition of regulatory variant effects"; Figure 3; Supplementary Figure SF5
- **Concern** The rSNP evaluation is described briefly, and the conclusion is that better TFBS prediction does not translate to better variant effect prediction. However, the methodology for this evaluation is not fully described in the visible text. The concordance curve approach is mentioned, but the details of how the models were scored, how the allelic preferences were determined, and how the area under the curve was computed are not provided. The interpretation of the results is also unclear: does this mean the models are not capturing the relevant binding determinants, or is the evaluation metric not sensitive enough?
- **Why it matters** This is an important negative result that could have implications for the use of TF binding models in variant effect prediction. However, without a clear description of the methodology and a discussion of potential confounders, the conclusion is not fully supported.
- **Resolution test** Provide a detailed description of the rSNP evaluation methodology, including the scoring function, the selection of rSNPs, and the computation of the concordance curve. Discuss potential limitations, such as the choice of threshold, the number of rSNPs per TF, and whether the results are consistent across TFs. Consider whether the evaluation metric is appropriate for the question being asked.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** "the largest open community challenge in Inferring BInding Specificities (IBIS), where participants all over the world were invited to construct binding specificity models from multi-assay experimental data for poorly studied human transcription factors"
- **Evidence pointer** Results section "Design and implementation of the IBIS Challenge"; Table 1
- **Concern** The challenge focuses on 40 human TFs, with only 2 positive controls in the Final stage. The authors note that the TFs belong to 13 structural families, but the text does not discuss how representative these TFs are of the broader human TF repertoire. The generalizability of the findings to other TFs, particularly those with different DNA binding domains or less well-characterized binding preferences, is not addressed.
- **Why it matters** The conclusions about the relative performance of PWMs and deep learning models may not hold for all TFs. If the challenge TFs are biased toward certain families or binding modes, the findings may not generalize.
- **Resolution test** Discuss the diversity of the TFs included in the challenge and compare their properties (e.g., binding motif length, complexity, family representation) to the broader set of human TFs. Acknowledge the limitation and suggest how the findings might extend to other TFs.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract, first sentence
- **Issue** The phrase "mecca of algorithmic bioinformatics" is informal and not standard scientific language.
- **Required correction** Replace with a more formal description, e.g., "a central problem in algorithmic bioinformatics."

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods, "General notes on position matrices"
- **Evidence pointer** Methods section, "General notes on position matrices"
- **Issue** The pseudocount value of 0.00001 is stated, but the rationale for this specific value is not provided.
- **Required correction** Briefly justify the choice of pseudocount or cite a reference for this value.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results, "IBIS Solutions and Winners"
- **Evidence pointer** Results section "IBIS Solutions and Winners"; Supplementary Table ST2
- **Issue** The text mentions that 19 teams submitted solutions, but does not describe the range of approaches used beyond a few examples. A summary of the diversity of methods would be informative.
- **Required correction** Add a brief summary of the types of methods used by participants (e.g., number of CNN-based, PWM-based, hybrid approaches).

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Results, "Deeper exploration of the Triple-A models with the IBIS benchmarking suite"
- **Evidence pointer** Results section "Deeper exploration of the Triple-A models with the IBIS benchmarking suite"; Figure 4
- **Issue** The text states that LegNet-Max and LegNet-WE were the best among tested models, but does not discuss why these specific modifications improved performance.
- **Required correction** Provide a brief interpretation of why variable kernel sizes and max pooling might improve generalization.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "Ranking Strategy"
- **Evidence pointer** Methods section "Ranking Strategy"
- **Issue** The description of the rank aggregation procedure is dense and may be difficult for readers to follow.
- **Required correction** Consider adding a step-by-step example or a schematic diagram to illustrate the ranking process.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Accessibility
- **Affected element** Data Availability
- **Evidence pointer** Data Availability section
- **Issue** The data are available on Zenodo, but the specific access conditions or any restrictions are not mentioned.
- **Required correction** State whether the data are freely accessible or if any restrictions apply.

## Risk / unsupported claims
- The claim that "properly designed deep learning models" consistently outperform PWMs is not quantitatively supported in the visible text. The magnitude and consistency of the advantage are not reported.
- The claim that PWMs perform "surprisingly well" is subjective and not supported by specific comparisons to prior expectations or benchmarks.
- The claim that the rSNP evaluation shows that better TF binding prediction does not improve variant effect prediction is not fully supported due to incomplete methodology description.
- The generalizability of the findings to all human TFs is not established, given the limited and potentially biased selection of TFs in the challenge.
- The performance of DNA language models is stated to be poor, but the specific results are not presented in the text.
- The claim that the IBIS framework "establishes a robust foundation" for future evaluation is reasonable but is an assertion of future utility that cannot be fully validated from the current results.