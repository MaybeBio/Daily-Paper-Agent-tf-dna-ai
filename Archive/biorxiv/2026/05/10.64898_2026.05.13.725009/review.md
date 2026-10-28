## Review setup

- **Input scope** Full manuscript text, including abstract, introduction, results, discussion, methods, and supplementary figure references
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and claims as supported by the provided text; no assessment of code functionality or figure content beyond what is described
- **Shared manuscript claim summary** The authors present MIMOSA, a model-independent framework for comparing transcription factor binding site motifs by their recognition profiles on shared DNA sequences rather than by internal model parameters. They claim competitive retrieval performance against established PWM-based tools on HOCOMOCO benchmarks and demonstrate utility in interpreting de novo ATF3 ChIP-seq motifs across different model classes.
- **Visible evidence base** Abstract, Introduction, Results sections A-C, Discussion, Methods sections D-G, figure references (Figures 1-6), supplementary figure references (S3-S7), author contributions, funding statement
- **Missing materials affecting confidence** Actual figures and supplementary materials are not provided; exact numerical values for benchmark results are only partially reported in text; no code repository contents or documentation are visible; no detailed parameter settings for benchmark comparisons are given

## Reviewer

- **Overall assessment** The manuscript presents a conceptually interesting approach to a genuine problem in the field: comparing TFBS motifs across different model representations. The core idea of comparing recognition profiles rather than model parameters is sound and addresses a real limitation of existing tools. The benchmark results, as described, suggest performance comparable to established methods, which is encouraging. However, the manuscript has several weaknesses that prevent full confidence in the claims. The description of the benchmark methodology is incomplete, particularly regarding the construction of the null distribution and the statistical comparisons. The ATF3 case study is illustrative but limited to a single TF. The methods section lacks sufficient detail for reproduction, and the dependence on a single benchmark dataset (HOCOMOCO) raises questions about generalizability. The writing is generally clear, but some technical aspects require clarification.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on TFBS motif discovery, motif database curation, and comparative analysis of regulatory genomics data. The framework would be of particular interest to researchers who use alternative motif models (e.g., BaMM, DIMONT, Slim) and need tools to compare their outputs with PWM-based references. The approach could also appeal to developers of motif discovery tools who need benchmarking strategies that are not limited to PWM representations.

- **Major strengths**
  1. The conceptual advance of comparing motifs by functional output rather than internal representation is novel and addresses a real gap in the field.
  2. The benchmark design using cross-experimental comparisons (in vitro vs. in vivo) is appropriate and demonstrates practical relevance.
  3. The ATF3 case study provides a concrete example of how the framework can reveal biologically meaningful distinctions between motif models.
  4. The manuscript is generally well-written and the motivation is clearly articulated.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "MIMOSA achieved retrieval performance comparable to established PWM-oriented tools, including Tomtom and MACRO-APE, with mean reciprocal rank (MRR) and Recall@k close to the best-performing methods."
- **Evidence pointer** Results section B, Figures 2-3, Supplementary Figures S3-S6
- **Concern** The benchmark methodology is not described in sufficient detail to evaluate the validity of the performance claims. The text states that HOCOMOCO motifs were used with in vitro motifs as queries and in vivo motifs as targets, but does not specify how the "correct" target was defined, how many queries and targets were used, how the score thresholds were selected, or how statistical significance was assessed for the retrieval task. The description of the null distribution construction in Methods section E is confusing: it mentions "shuffled motifs" and "null query-target comparisons" but does not clarify whether the null distribution is query-specific or pooled across all queries. The claim of "comparable performance" is based on mean values without reported confidence intervals or statistical tests comparing MIMOSA to the other tools.
- **Why it matters** Without a clear and reproducible benchmark protocol, the performance claims cannot be independently verified. The choice of evaluation metrics, the definition of correct matches, and the statistical treatment of results are all critical for interpreting whether MIMOSA truly achieves comparable performance to established tools.
- **Resolution test** Provide a detailed benchmark protocol including: (1) exact definition of "correct" target motifs, (2) number of queries and targets, (3) threshold selection procedure, (4) statistical tests comparing MIMOSA to other tools (e.g., paired tests across queries), and (5) confidence intervals for MRR and Recall@k. Clarify the null distribution construction and whether it is appropriate for the retrieval task.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "MIMOSA assesses motif similarity by comparing calibrated recognition profiles produced by different motif models on the same DNA sequence set, rather than by comparing motif parameters."
- **Evidence pointer** Methods section D, Figure 1
- **Concern** The description of the profile construction and normalization is incomplete. The text states that profiles are normalized using an empirical false-positive rate based on a "calibration sequence set," but does not specify what this calibration set is, how it is selected, or whether it is the same for all comparisons. The choice of the threshold T for defining anchors is mentioned but no guidance is given for how to select it. The shift range [−D, D] and window radius R are not defined. The method for handling different motif lengths and the computational complexity of the enumeration over orientations and shifts are not discussed. These details are essential for understanding the method's behavior and limitations.
- **Why it matters** The core methodological contribution of the paper is the profile-based comparison framework. If the key parameters and procedures are not fully specified, the method cannot be reproduced or properly evaluated. The choice of calibration set and thresholds could significantly affect results.
- **Resolution test** Provide complete specifications for: (1) the calibration sequence set and its construction, (2) the threshold T and how it is selected, (3) the shift range D and window radius R, (4) handling of different motif lengths, and (5) computational complexity. Ideally, include a sensitivity analysis showing how results vary with these parameters.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "Applying MIMOSA to de novo ATF3 ChIP-seq motifs showed that recognition-profile comparison distinguished alternative spacer variants represented as separate PWMs from their integration within more flexible models such as BaMM and Slim."
- **Evidence pointer** Results section C, Figures 4-6, Supplementary Figure S7
- **Concern** The ATF3 case study is presented as a key demonstration of the framework's utility, but it is limited to a single TF and a single dataset. The conclusions drawn from this case study may not generalize. The text states that DIMONT showed a distinct annotation pattern, but the interpretation of this finding is not fully developed. The comparison between profile-based and matrix-based approaches is interesting, but the implications for practical use are not clearly articulated. The choice of the ATF3 dataset and the specific tools used for de novo discovery are not justified.
- **Why it matters** The case study is meant to illustrate the practical value of the framework. If it is limited to a single example, the broader applicability of the approach remains uncertain. The field would benefit from a more systematic evaluation across multiple TFs and datasets.
- **Resolution test** Expand the case study to include additional TFs or datasets, or provide a clear rationale for why the ATF3 example is representative. Discuss the generalizability of the findings and any potential limitations of the approach for other TF families or motif architectures.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "For each motif pair, MIMOSA first creates recognition profiles for a given set of DNA sequences. It then normalizes these profiles, enumerates pairwise shifts and orientations of the recognized motif signal, including forward and reverse-complement alignments, and selects the alignment that maximizes the chosen similarity metric."
- **Evidence pointer** Methods section D, Figure 1
- **Concern** The statistical significance estimation procedure is described in Methods section E, but the connection between the similarity score and the significance estimate is not fully clear. The text states that the null distribution is constructed from "cross-class comparisons of shuffled HOCOMOCO motifs" and that the upper tail is approximated by a generalized extreme value distribution. However, it is not clear how the null distribution accounts for the optimization over shifts and orientations. If the maximum over many alignments is taken, the null distribution should reflect this maximization, otherwise the significance estimates will be overly optimistic. The multiple testing correction is mentioned but not described in detail.
- **Why it matters** The significance estimates are critical for the practical use of MIMOSA in database annotation. If the null distribution does not properly account for the optimization procedure, users may obtain inflated significance values and make incorrect biological conclusions.
- **Resolution test** Provide a detailed description of how the null distribution accounts for the maximization over shifts and orientations. Describe the multiple testing correction procedure. Ideally, include a validation of the significance estimates using simulated or empirical data.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract and Introduction
- **Evidence pointer** Abstract, Introduction
- **Issue** The abstract and introduction assume familiarity with the specific motif model types (BaMM, Slim, DIMONT) and the concept of "recognition profiles" without providing sufficient context for readers who may not be specialists in motif modeling. The term "model-independent" is used prominently but its precise meaning in this context is not immediately clear.
- **Required correction** Briefly define or contextualize the alternative motif models mentioned and clarify what "model-independent" means in the context of the framework (i.e., that it does not require converting models to a common representation).

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods section D
- **Evidence pointer** Methods section D
- **Issue** The notation for the profiles is incomplete. The text states "constructs two positional recognition profiles, and " but the symbols are missing. This appears to be a formatting error.
- **Required correction** Correct the notation so that the profiles are properly defined.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Results section B
- **Evidence pointer** Results section B, Figure 3
- **Issue** The text reports mean MRR values but does not provide standard deviations or confidence intervals. The differences between methods (e.g., 0.833 for Tomtom vs. 0.826 for mimosa-cosine) are small and may not be statistically significant.
- **Required correction** Report variability measures and, if possible, statistical tests for the differences in performance.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Methods section G
- **Evidence pointer** Methods section G
- **Issue** The implementation section mentions the use of NumPy, Numba, and SciPy but does not specify versions or provide details on how to install and run the software. The GitHub link is provided, but no usage examples or documentation are referenced.
- **Required correction** Provide installation instructions, version requirements, and a minimal usage example in the manuscript or refer to documentation in the repository.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion
- **Issue** The discussion of limitations is brief and does not address potential issues such as the choice of the sequence set for profile construction, the sensitivity of results to the calibration set, or the computational cost of the method for large-scale comparisons.
- **Required correction** Expand the limitations section to address these points and provide guidance for users on how to select appropriate parameters.

- **Technical failings that need to be addressed before the case is established**
  1. Incomplete benchmark methodology description (R1-M1)
  2. Underspecified profile construction and normalization parameters (R1-M2)
  3. Unclear statistical significance estimation procedure (R1-M4)

- **Assessment against Nature-style criteria**
  - **Originality** The concept of comparing motifs by their functional output on shared sequences is a novel contribution. While the idea of using recognition profiles is not entirely new, the systematic framework and its application to cross-model comparison represent an original approach.
  - **Scientific importance** The problem addressed is relevant and timely, given the increasing use of alternative motif models. However, the demonstration is limited to a single case study and one benchmark dataset, which limits the strength of the claims about broad utility.
  - **Interdisciplinary readership** The work is primarily of interest to computational biologists and bioinformaticians. The potential for broader readership in molecular biology is limited by the technical nature of the content and the lack of accessible examples of biological insights gained through the framework.
  - **Technical soundness** The core idea is sound, but the manuscript lacks sufficient detail in the methods to fully evaluate technical correctness. The benchmark and significance testing procedures need clarification and validation.
  - **Readability for nonspecialists** The manuscript is generally well-written but assumes significant background knowledge in motif modeling. The abstract and introduction could be more accessible with brief explanations of key concepts.

- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual contribution is valuable and the preliminary results are promising, but the manuscript requires substantial revisions to the methods description and additional validation before the claims can be fully assessed. The authors should provide a complete benchmark protocol, clarify the statistical procedures, and ideally expand the case study to demonstrate broader applicability.