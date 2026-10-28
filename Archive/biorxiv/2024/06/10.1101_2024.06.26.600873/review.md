## Review setup
- **Input scope** Full manuscript text (abstract, introduction, approach overview, results, discussion, footnotes) from bioRxiv preprint
- **Assessment boundary** Scientific content, methodological soundness, claims vs. evidence, and presentation quality as presented in the provided text
- **Shared manuscript claim summary** The authors introduce motifDiff, a scalable computational tool for quantifying variant effects on transcription factor binding using mono- and dinucleotide position weight matrices, with a statistically rigorous normalization strategy (probNorm) that outperforms raw log-odds differences and existing tools, and demonstrate its utility across in vivo ground truth datasets and in evolutionary analyses of human accelerated regions
- **Visible evidence base** Text descriptions of results referencing Figures 1-6, Supplemental Figures S1 and S3, and Table 1; no actual figure data, numerical values, or code outputs are provided in the supplied material
- **Missing materials affecting confidence** All figure contents, numerical results, statistical test outputs, dataset details, and code implementation specifics are absent from the provided text, preventing independent verification of any reported performance claims

## Reviewer
- **Overall assessment** The manuscript presents a conceptually sound and potentially useful tool for variant effect prediction using biophysical TF binding models. The motivation is clear, and the probNorm normalization strategy is a reasonable contribution. However, the provided text lacks all quantitative evidence, making it impossible to evaluate the validity of the central claims. The performance comparisons, benchmark results, and evolutionary analyses are described only qualitatively. The manuscript would benefit from a more rigorous presentation of results, including effect sizes, confidence intervals, and statistical details. The claim that deep learning models perform poorly on common variant prediction is referenced but not demonstrated with data in this text. The HAR analysis is intriguing but the interpretation is speculative given the absence of data. Overall, the idea has merit, but the case is not established from the supplied material.
- **Who would be interested in the results, and why** Computational genomics researchers developing or applying variant effect prediction tools, particularly those working on regulatory genomics and TF binding. Evolutionary biologists studying regulatory sequence evolution, especially in the context of human accelerated regions. Researchers in functional genomics who need interpretable, scalable tools for prioritizing non-coding variants. The tool's speed advantage over deep learning methods could appeal to those working with large-scale variant datasets.
- **Major strengths** The probNorm normalization approach is a principled improvement over raw log-odds differences, addressing a known limitation in PWM-based scoring. The focus on common variants measured in vivo is a practically relevant benchmark scenario. The scalability analysis, while not quantified in the text, addresses a real need in the field. The HAR application demonstrates a useful interpretability advantage of biophysical models over black-box deep learning approaches. The tool is made available as open-source software.
- **Major Concerns** 
  - R1-M1: The manuscript provides no quantitative results whatsoever. All performance claims are qualitative ("probNorm was best in all cases", "performance is similar", "small but uniform improvement") without any numerical values, effect sizes, or statistical measures. This makes the central claims unverifiable.
  - R1-M2: The comparison to deep learning methods, particularly Sei, is central to the motivation but is not substantiated with data. The claim that Sei performs best "in most" tasks is stated without showing the actual performance values or the magnitude of differences.
  - R1-M3: The ADASTRA single-score analysis (Figure 3) is described as showing probNorm "best in all cases" but then exceptions are noted (BRD4, IKZF1, STAT1), creating an internal inconsistency in the narrative.
  - R1-M4: The HAR analysis is presented as revealing "unique insights" but the interpretation is speculative. The claim that TF gains are enriched for neurodevelopmental roles is not supported by any statistical evidence in the text, and the discrepancy with Sei's loss-enriched predictions is not resolved or discussed in depth.
  - R1-M5: The dinucleotide model analysis concludes they "do not improve" prediction but the text suggests exceptions (STAT1, BRD4) and interactions with normalization, which complicates the conclusion without clear explanation.
- **Minor Comments** 
  - R1-m1: The abstract mentions "mono and dinucleotide position weight matrices" but the introduction of dinucleotide models in the results is abrupt; a brief methodological description of how DWMs are constructed and used would help.
  - R1-m2: The text states "our computational frameworks is flexible" (grammatical error) and "This tool was used recently in several high impact studies" (tense inconsistency); careful proofreading is needed.
  - R1-m3: The discussion of why IKZF1's own PWM was not selected in favor of RUNX1 is interesting but speculative; the authors should acknowledge alternative explanations more explicitly.
  - R1-m4: The statement that "the low performance is mainly a function of dataset noise rather than modeling limitations" is a strong conclusion that requires more direct evidence, such as noise estimation or simulation.
  - R1-m5: The timing comparison with motifbreakR is mentioned but no actual timing data are provided; this is a key selling point and should be quantified.
- **Technical failings that need to be addressed before the case is established** R1-M1 (no quantitative results), R1-M2 (unsubstantiated deep learning comparison), R1-M4 (speculative HAR interpretation without statistical support)
- **Assessment against Nature-style criteria** 
  - Originality: Moderate. The probNorm normalization is a novel contribution, but the overall approach of PWM-based variant scoring is well established. The application to HARs is a new angle.
  - Scientific importance: Moderate. The tool addresses a practical need, but the demonstrated advantages over existing methods are not quantified in the provided text. The impact on the field would depend on the actual performance gains.
  - Interdisciplinary readership: Limited. The manuscript is primarily of interest to computational genomics specialists. The evolutionary application could broaden appeal, but the presentation is technical.
  - Technical soundness: Not assessable from the provided material. The methodological description is clear at a conceptual level, but the absence of results prevents evaluation of whether the implementation and evaluation are sound.
  - Readability for nonspecialists: The introduction and approach overview are accessible, but the results section assumes familiarity with TF binding assays, QTL analysis, and deep learning architectures. The manuscript would benefit from a brief primer on these concepts.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual contribution is promising, but the complete absence of quantitative results means the central claims cannot be evaluated. The authors should provide full numerical results, statistical analyses, and figure data before the case can be assessed.

### Major Concern 1
- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The manuscript claims probNorm outperforms other PWM-based methods and approaches deep learning performance, with statements like "probNorm was best in all cases" and "the sequence of performance is un-normalized ≤ FABIAN ≤ ProbNorm ≤ Sei"
- **Evidence pointer** Results section, Figures 2-6, Table 1 (all referenced but not provided)
- **Concern** The text contains no numerical values, correlation coefficients, AUC scores, confidence intervals, or p-values. All performance comparisons are described qualitatively. Without the actual data, it is impossible to assess the magnitude of improvements, whether differences are statistically significant, or whether the claimed performance ordering is robust.
- **Why it matters** The central contribution of the manuscript is a new method with claimed performance advantages. These claims are the basis for recommending the tool to the community. Without quantitative evidence, the claims are unverifiable and the scientific case is not established.
- **Resolution test** Provide all numerical results in the main text or supplementary materials, including correlation coefficients, AUC values, and appropriate statistical tests (e.g., paired tests across datasets) with effect sizes and confidence intervals.

### Major Concern 2
- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim-evidence alignment
- **Claim pointer** The manuscript states that deep learning methods "perform inadequately on some variant effect prediction tasks, especially with common genetic variants" and uses Sei as a benchmark, claiming it achieves "maximum correlation... improved only to 0.65"
- **Evidence pointer** Introduction, Results section, Figure 2 (referenced but not provided)
- **Concern** The motivation for the tool relies heavily on the claimed inadequacy of deep learning methods for common variant prediction. However, no data are shown to support this claim. The single correlation value of 0.65 is mentioned without context, such as what the theoretical maximum might be, what the variance across tasks is, or how this compares to other deep learning methods.
- **Why it matters** If deep learning methods actually perform well on these tasks, the motivation for a simpler biophysical approach is weakened. The comparison is central to positioning the tool in the field.
- **Resolution test** Provide a systematic comparison of Sei (and ideally other deep learning methods) on the same benchmark datasets, with full performance distributions, and discuss the implications for the claimed inadequacy.

### Major Concern 3
- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Internal consistency
- **Claim pointer** The text states "probNorm was best in all cases" for the ADASTRA single-score task, but then notes exceptions: "exclusive of BRD4, IKZF1 and STAT1"
- **Evidence pointer** Results section, Figure 3 (referenced but not provided)
- **Concern** The claim of "best in all cases" is immediately contradicted by the exceptions listed. This creates confusion about the actual performance pattern. The exceptions are dismissed as cases where "the prediction problem is not well specified," but this is asserted without evidence.
- **Why it matters** The exceptions may reveal important limitations of the method or the PWM models. Understanding why the method fails for certain TFs is scientifically important and could guide future improvements.
- **Resolution test** Clarify the performance pattern, provide a detailed analysis of the exceptional cases, and discuss what they reveal about the method's limitations.

### Major Concern 4
- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive rigor
- **Claim pointer** The manuscript claims the HAR analysis reveals "a overall bias toward gains" and that "the transcription factors associated with gains were strongly enriched for neurodevelopmental roles"
- **Evidence pointer** Results section, Figure 8 (referenced but not provided)
- **Concern** The HAR analysis is presented as a key application demonstrating the tool's utility. However, the interpretation is speculative. The discrepancy with Sei's predictions (enriched for losses) is noted but not resolved. The biological significance of the TF gains is asserted without functional validation or discussion of alternative explanations.
- **Why it matters** The evolutionary application is a distinctive contribution of the manuscript. If the interpretation is not well-supported, it weakens the case for the tool's broader utility.
- **Resolution test** Provide statistical support for the enrichment claims, discuss the Sei discrepancy in depth, and consider alternative explanations for the observed patterns.

### Major Concern 5
- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Conclusion support
- **Claim pointer** The manuscript concludes "we find no evidence that DWMs are more effective in capturing variant effects"
- **Evidence pointer** Results section, Figure 6 (referenced but not provided)
- **Concern** The conclusion about dinucleotide models is based on a limited subset of TFs (278) and shows exceptions (STAT1, BRD4) where DWMs improve performance. The interaction with normalization complicates the interpretation. The conclusion may be premature without a more thorough analysis.
- **Why it matters** The dinucleotide model analysis is a significant component of the manuscript. A definitive negative conclusion requires robust evidence across diverse conditions.
- **Resolution test** Provide a more comprehensive analysis of DWM performance, including the conditions under which they help or hurt, and discuss the implications for model choice.

### Minor Comment 1
- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract mentions "mono and dinucleotide position weight matrices" but does not explain what dinucleotide models are or why they might be useful.
- **Required correction** Add a brief explanation of dinucleotide models and their potential advantages in the abstract or introduction.

### Minor Comment 2
- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Language quality
- **Affected element** Approach overview
- **Evidence pointer** Approach overview section
- **Issue** The text contains grammatical errors, e.g., "our computational frameworks is flexible" and "This tool was used recently in several high impact studies" (tense inconsistency).
- **Required correction** Proofread the manuscript carefully and correct all grammatical and stylistic errors.

### Minor Comment 3
- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretive balance
- **Affected element** Discussion of IKZF1
- **Evidence pointer** Results section, Figure 3 (referenced but not provided)
- **Issue** The explanation for why IKZF1's own PWM was not selected in favor of RUNX1 is speculative and presented as if it were established.
- **Required correction** Acknowledge the speculative nature of the explanation and discuss alternative possibilities.

### Minor Comment 4
- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Evidence sufficiency
- **Affected element** Noise attribution
- **Evidence pointer** Results section
- **Issue** The claim that "the low performance is mainly a function of dataset noise rather than modeling limitations" is a strong conclusion without direct evidence.
- **Required correction** Provide evidence for the noise level in the datasets or soften the claim to acknowledge uncertainty.

### Minor Comment 5
- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Timing comparison
- **Evidence pointer** Results section, timing section (referenced but not provided)
- **Issue** The timing comparison with motifbreakR is mentioned but no actual timing data are provided.
- **Required correction** Include the timing results in the main text or supplementary materials.

## Risk / unsupported claims
- The claim that probNorm outperforms all other PWM-based methods is unsupported without numerical results.
- The claim that deep learning methods perform inadequately on common variant prediction is referenced but not demonstrated with data.
- The claim that the HAR analysis reveals a bias toward TF gains with neurodevelopmental relevance is speculative without statistical support.
- The claim that low performance is mainly due to dataset noise is asserted without evidence.
- The conclusion that DWMs do not improve variant effect prediction is based on a limited analysis with noted exceptions.
- The claim that motifDiff is "highly scalable" and "180-480 times faster" than motifbreakR is not quantified in the provided text.
- The biological interpretation of the IKZF1 analysis (RUNX1 contribution) is speculative.