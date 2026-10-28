## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods, data/code availability statements)
- **Assessment boundary** Scientific content, methodology, benchmarking design, claims and their support by the presented evidence; not editorial or formatting issues
- **Shared manuscript claim summary** The authors report the results of the IBIS community challenge, in which participants built transcription factor binding specificity models (PWMs and arbitrary advanced approaches, "Triple-A") from multi-assay experimental data for 40 human transcription factors. They claim that (i) properly designed deep learning models consistently outperform traditional PWMs in cross-platform benchmarking, (ii) PWMs remain competitive when backed by internal benchmarking, (iii) the challenge design prevents information leakage and enables fair comparison, and (iv) the provided data and software constitute a reusable resource for future benchmarking.
- **Visible evidence base** Abstract, full text of Introduction, Results, Discussion, Methods, Data Availability, Code Availability, Acknowledgments; references to supplementary figures, tables, and data files are made but the supplementary materials themselves were not provided
- **Missing materials affecting confidence** Supplementary figures (SF1–SF10), supplementary tables (ST1, ST2), supplementary data (SD1), supplementary methods, the full benchmark results per team and per TF, the actual test data and labels, and the bibis software package were not available for inspection. This limits verification of quantitative claims and detailed methodological descriptions.

## Reviewer
- **Overall assessment** This manuscript describes a large-scale, well-organized community benchmarking effort for transcription factor binding specificity modeling. The challenge design is thoughtful, with clear separation of training and test data, multiple platforms, and pre-registered evaluation protocols. The main finding, that deep learning models outperform PWMs in cross-platform transfer but that PWMs remain competitive when carefully benchmarked, is plausible and of interest to the field. However, the manuscript as presented has several weaknesses. The description of the ranking procedure is incomplete, the statistical analysis of performance differences is not reported, and the claim that deep learning models "consistently" outperform PWMs is not supported by the quantitative data shown in the main text. The post-challenge analysis of additional deep learning methods is described only briefly, and the failure of language models is reported without sufficient detail. The manuscript would benefit from a more rigorous presentation of the benchmarking results, including confidence intervals and effect sizes, and from a clearer articulation of what the community should learn from the results.
- **Who would be interested in the results, and why** Researchers in computational genomics, regulatory genomics, and machine learning applied to DNA sequence analysis. The manuscript provides a benchmark resource and a comparative assessment of modeling approaches that is directly relevant to anyone developing or using TF binding specificity models. The finding that deep learning models can transfer across experimental platforms better than PWMs, but that PWMs remain competitive, is of practical importance for tool selection. The challenge data and software are a resource for future method development.
- **Major strengths** (1) The challenge design is rigorous, with pre-registered protocols, multiple platforms, and clear separation of training and test data. (2) The use of 40 transcription factors, including poorly studied ones, provides a broad and realistic test bed. (3) The comparison of PWMs and deep learning models in a community setting is novel and valuable. (4) The provision of data, code, and an online benchmarking platform is a significant contribution to the field. (5) The post-challenge assessment of additional methods, including language models, adds depth to the analysis.
- **Major Concerns** See items R1-M1 to R1-M5 below.
- **Minor Comments** See items R1-m1 to R1-m6 below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (ranking procedure incomplete), R1-M2 (no statistical analysis of performance differences), R1-M3 (claim of "consistent" deep learning advantage not supported by shown data), R1-M4 (post-challenge analysis insufficiently described), R1-M5 (no analysis of failure modes or platform-specific patterns).
- **Assessment against Nature-style criteria**  
  *Originality*: The manuscript is original in its community-challenge approach to TF binding specificity modeling, and the comparison of PWMs and deep learning models in this setting is novel. However, the individual components (benchmarking, PWM vs. deep learning comparisons) are not new.  
  *Scientific importance*: The results are of importance to the field of regulatory genomics, as they provide a fair comparison of modeling approaches and a reusable benchmark. The finding that deep learning models transfer across platforms better than PWMs, but that PWMs remain competitive, is a useful contribution.  
  *Interdisciplinary readership*: The manuscript is likely to appeal to computational biologists, machine learning researchers, and experimentalists interested in TF binding. The writing is generally accessible, but some sections (e.g., the ranking procedure) are difficult to follow.  
  *Technical soundness*: The challenge design is sound, but the presentation of results lacks statistical rigor. The ranking procedure is not fully described, and no confidence intervals or significance tests are provided. The post-challenge analysis is described too briefly to assess its validity.  
  *Readability for nonspecialists*: The abstract and introduction are clear, but the results section assumes familiarity with the specific benchmarking protocols and metrics. The manuscript would benefit from a more explicit explanation of the ranking procedure and the meaning of the performance metrics.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript describes a valuable resource and a well-designed challenge, but the presentation of results needs to be more rigorous and complete before the claims are fully established.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors state that they used a "hierarchical ranking strategy" to rank teams, but the description of this procedure is incomplete. The Methods section says "First, the ranks of individual submissions were obtained: Then, for each discipline:" and then stops, with no further explanation.
- **Evidence pointer** Methods, "Ranking Strategy" section
- **Concern** The ranking procedure is a central element of the challenge, as it determines the winners and the comparison between PWMs and Triple-A models. The current description is incomplete and does not allow the reader to understand how the ranks were computed, how the different metrics were combined, or how the hierarchical averaging was performed. This is a critical methodological detail that must be fully described.
- **Why it matters** Without a complete description of the ranking procedure, the results cannot be reproduced or independently verified. The ranking procedure also affects the interpretation of the performance differences between PWMs and Triple-A models.
- **Resolution test** Provide a complete, step-by-step description of the ranking procedure, including the exact formulas used for rank computation, the normalization steps, and the hierarchical averaging. This could be in the Methods section or in a supplementary note.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report that "the top-scoring triple-A models clearly outperformed PWM-based solutions" and that "properly designed deep learning models" have a "consistent advantage" over PWMs. However, no statistical analysis is presented to support these claims.
- **Evidence pointer** Results, "Triple-A models outperform PWMs, but by a limited margin and only when thoroughly designed" section; Figures 2 and 3
- **Concern** The manuscript reports performance differences between PWMs and Triple-A models but does not provide confidence intervals, standard errors, or significance tests for these differences. The number of TFs (30 in the final stage) is small, and the performance varies across TFs and platforms. Without a statistical analysis, it is not possible to assess whether the observed differences are robust or could be due to chance.
- **Why it matters** The main conclusion of the manuscript, that deep learning models outperform PWMs in cross-platform transfer, rests on the observed performance differences. Without a statistical analysis, the reader cannot assess the strength of the evidence for this claim.
- **Resolution test** Provide a statistical analysis of the performance differences, such as paired tests (e.g., Wilcoxon signed-rank test) across TFs, with appropriate correction for multiple testing. Report effect sizes and confidence intervals for the differences.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors state that "properly designed deep learning models" have a "consistent advantage" over PWMs. However, the data shown in Figure 2 and the text suggest that the advantage is modest and varies across TFs and platforms. The word "consistent" may overstate the findings.
- **Evidence pointer** Results, "Triple-A models outperform PWMs, but by a limited margin and only when thoroughly designed" section; Figure 2
- **Concern** The claim of a "consistent advantage" is not supported by the data as presented. The text itself notes that "numerous deep learning–based approaches failed substantially in cross-experiment validation," and the performance differences in Figure 2 appear to be small and variable. The authors should either provide a more nuanced interpretation of the results or present additional evidence to support the claim of consistency.
- **Why it matters** The claim of a consistent advantage is a key takeaway message of the manuscript. If it is overstated, it could mislead readers about the practical benefits of deep learning models for TF binding specificity modeling.
- **Resolution test** Revise the language to accurately reflect the magnitude and variability of the performance differences. Alternatively, provide additional analyses (e.g., per-TF or per-platform breakdowns) that demonstrate the consistency of the advantage.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The authors describe a "post-challenge assessment of a selection of other deep learning methods" that "further solidified this finding." However, the description of this assessment is very brief, and it is not clear which methods were tested, how they were trained, or how they were evaluated.
- **Evidence pointer** Results, "Triple-A models outperform PWMs, but by a limited margin and only when thoroughly designed" section; Methods, "Post-challenge deep learning models" section
- **Concern** The post-challenge assessment is an important part of the manuscript, as it provides additional evidence for the main findings. However, the description is insufficient to understand what was done. For example, it is not clear whether the same training/test splits were used, how hyperparameters were selected, or how the results were aggregated.
- **Why it matters** Without a clear description of the post-challenge assessment, the reader cannot evaluate the validity of the additional evidence or compare it with the challenge results.
- **Resolution test** Provide a more detailed description of the post-challenge assessment, including the models tested, the training procedure, the evaluation protocol, and the results. This could be in the Methods section or in a supplementary note.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The authors report that "the positional weight matrices displayed a surprisingly strong performance out of the box, being only slightly behind the best deep learning models." This is an interesting finding, but the manuscript does not explore why PWMs perform so well or under what conditions they might be preferred.
- **Evidence pointer** Results, "Triple-A models outperform PWMs, but by a limited margin and only when thoroughly designed" section
- **Concern** The finding that PWMs are competitive with deep learning models is potentially important for practical applications, but the manuscript does not discuss the implications. For example, PWMs are simpler, more interpretable, and require less computational resources. The authors could discuss the trade-offs between PWMs and deep learning models in more detail.
- **Why it matters** The manuscript aims to inform the field about the relative merits of different modeling approaches. A more detailed discussion of the practical implications of the findings would increase the impact of the work.
- **Resolution test** Add a discussion of the practical implications of the results, including the trade-offs between PWMs and deep learning models in terms of performance, interpretability, and computational cost.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Design and implementation of the IBIS Challenge" section
- **Evidence pointer** "The IBIS challenge ran from March to September 2024 in two stages." The text later says "The Final stage started in midsummer 2024 and ended in September 2024." The exact dates of the final stage are not given.
- **Issue** The timeline of the challenge is not fully specified.
- **Required correction** Provide the exact start and end dates for both the Leaderboard and Final stages.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "IBIS Solutions and Winners" section
- **Evidence pointer** "19 teams submitted their solutions for the Final stage to compete in four primary disciplines (A2G-AAA, G2A-AAA, A2G-PWM, G2A-PWM) and the secondary WET disciplines"
- **Issue** It is not clear whether all 19 teams submitted solutions for all four primary disciplines, or whether some teams only participated in a subset.
- **Required correction** Clarify how many teams submitted solutions for each discipline.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Triple-A models outperform PWMs, but by a limited margin and only when thoroughly designed" section
- **Evidence pointer** "For the baseline, we assembled the MEX1 collection of PWMs reusing the strategy of the Codex Motif Explorer11 with IBIS training data only."
- **Issue** The name "Codex Motif Explorer" is used here, but elsewhere in the manuscript it is called "Codebook Motif Explorer" (e.g., in the Introduction and Methods). This inconsistency is confusing.
- **Required correction** Use a consistent name for the Codebook Motif Explorer throughout the manuscript.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "Post-challenge deep learning models" section
- **Evidence pointer** "For training the A2G models, the positive sets were used 'as is' and only HT-SELEX data were utilized."
- **Issue** It is not clear what "as is" means in this context. Does it mean that all positive sequences were used without any filtering or subsampling?
- **Required correction** Clarify what "as is" means and describe any preprocessing steps applied to the positive sets.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Methods, "Post-challenge deep learning models" section
- **Evidence pointer** "For G2A, the positive sets were used 'as is'. The negative set consisted of sequences bound by other proteins and sequences generated by single-nucleotide shuffling of the positive sequences, maintaining a 1:1:1 ratio, as for A2G."
- **Issue** The ratio 1:1:1 is mentioned, but it is not clear what the three components are. Is it positive:negative-other-proteins:negative-shuffled?
- **Required correction** Clarify the composition of the training data and the meaning of the 1:1:1 ratio.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Results, "Better TFBS prediction does not necessarily improve recognition of regulatory variant effects" section
- **Evidence pointer** "For Triple-As, the scoring was performed by the authors of each solution, whereas for PWMs, we scored the variants with PERFECTOS-APE36."
- **Issue** It is not clear whether the Triple-A models were scored using the same protocol as the PWMs, or whether the authors of the Triple-A solutions used different scoring methods.
- **Required correction** Clarify whether the Triple-A scoring was standardized across teams, and if not, how the results were compared.

## Risk / unsupported claims
- The claim that "properly designed deep learning models" have a "consistent advantage" over PWMs is not supported by the data as presented, given the lack of statistical analysis and the observed variability across TFs and platforms (R1-M2, R1-M3).
- The claim that the post-challenge assessment "further solidified this finding" is not verifiable from the provided text, as the assessment is described too briefly (R1-M4).
- The claim that the challenge design "prevents information leakage" is plausible but not fully verifiable, as the details of the data preprocessing and test set construction are not fully described in the provided text.
- The claim that the provided data and software constitute a "fair cross-platform evaluation" framework is not fully verifiable, as the software and data are not available for inspection in this review.
- The performance of individual teams and the specific ranking of teams are not verifiable, as the supplementary tables (ST1, ST2) were not provided.