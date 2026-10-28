## Review setup

- **Input scope** Full manuscript text (summary, introduction, results, discussion, methods, data availability, code availability, author contributions, acknowledgements, footnotes)
- **Assessment boundary** Scientific content, methodology, claims, and evidence as presented in the provided text. No external data or unpublished materials were consulted.
- **Shared manuscript claim summary** The authors present GHT-SELEX, a high-throughput in vitro selection method using fragmented genomic DNA, and apply it to 179 transcription factors (TFs) across 25 families. They report that many human TFs possess higher intrinsic sequence specificity than previously appreciated, that GHT-SELEX binding peaks often resemble in vivo ChIP-seq peaks, that PWM-based motif scanning can achieve comparable predictive performance when appropriate scoring methods are used, and that C2H2 zinc finger proteins frequently use alternative subsets of their DNA-binding domains to recognize distinct target sites, often arising from internal duplication and divergence.
- **Visible evidence base** Results sections describing method development, control experiments, reproducibility assessments, peak overlap analyses, PWM scanning comparisons, and C2H2-zf domain analyses. Methods sections describing experimental protocols, statistical frameworks (MAGIX, RCADEEM), and data processing. References to supplementary tables, figures, and documents are made but their contents are not provided.
- **Missing materials affecting confidence** Supplementary tables (S1-S11), supplementary documents (S1-S4), extended data figures, the accompanying Codebook consortium manuscripts, and the online data repositories are referenced but were not available for review. This limits verification of quantitative results, detailed experimental parameters, and the full set of analyses.

## Reviewer

- **Overall assessment** This manuscript describes a technically sophisticated and potentially valuable new method for characterizing TF-DNA interactions in vitro using genomic DNA as the substrate. The central observation, that many TFs show higher intrinsic specificity than commonly assumed and that this specificity can recapitulate a substantial fraction of in vivo binding, is important and challenges prevailing models. The application to C2H2-zf proteins, revealing modular and alternative use of DNA-binding domains, is a significant advance. However, the strength of the conclusions depends heavily on the quality of the computational pipelines (MAGIX, RCADEEM) and on comparisons to external datasets, and the provided text does not contain sufficient quantitative detail to fully assess these. The manuscript is well-written and the logic is clear, but several claims require additional evidence or clarification.
- **Who would be interested in the results, and why** Researchers in transcriptional regulation, genomics, and bioinformatics would be the primary audience. The method itself will be of interest to those studying TF binding specificity, and the large dataset of new TF motifs will be a valuable community resource. The findings on C2H2-zf proteins and their modular DNA binding have implications for understanding TF evolution and function. The observation that intrinsic specificity can explain a large fraction of in vivo binding will be of interest to those modeling gene regulatory networks and interpreting non-coding variation.
- **Major strengths** The development of GHT-SELEX is a genuine methodological innovation, addressing a real limitation of existing in vitro approaches by using genomic DNA as the binding substrate. The scale of the study, with over 1,500 experiments on 179 TFs, is impressive. The integration of multiple data types (GHT-SELEX, HT-SELEX, ChIP-seq) and the development of bespoke analytical tools (MAGIX, RCADEEM) demonstrate a rigorous approach. The finding that PWM scanning performance is highly dependent on scoring method is a practical and important insight. The analysis of C2H2-zf domain usage is novel and provides a framework for understanding this large and poorly characterized TF family.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness and validation of the central claim
  - **Claim pointer** The manuscript claims that "many human TFs possess much higher sequence specificity than anticipated" and that GHT-SELEX peaks are "often surprisingly similar to those obtained in vivo."
  - **Evidence pointer** Results sections "Development and testing of GHT-SELEX" and "Unexpectedly high overlap between TF binding to the genome in vitro and in vivo"; Figures 1, 2, 4; Tables S4, S9
  - **Concern** The central claim of high intrinsic specificity rests on the comparison between GHT-SELEX peaks and ChIP-seq peaks. The Jaccard statistic is used, and the authors report a median value of 0.127, which they describe as "surprisingly high." However, the text does not provide a clear null expectation or a comparison to what would be obtained with a random or low-specificity TF. The permutation test is mentioned, but the resulting distribution and the significance of the observed values are not shown in the provided text. Furthermore, the comparison to PWM-based predictions is used to argue that motifs are accurate, but the text states that the overlap between PWM predictions and ChIP-seq is "similar" to the GHT-SELEX-ChIP-seq overlap. This raises the question of whether the high overlap is driven by the intrinsic specificity of the TF or by the properties of the genomic regions (e.g., open chromatin, low complexity) that are captured by both methods. The authors need to provide a more rigorous demonstration that the observed overlap is specifically due to sequence-specific recognition by the TF.
  - **Why it matters** This is the foundational claim of the paper. If the overlap between GHT-SELEX and ChIP-seq is not demonstrably higher than what would be expected by chance or by non-specific factors, the conclusion that TFs have high intrinsic specificity is not supported.
  - **Resolution test** Provide a clear null distribution for the Jaccard statistic, for example by using a TF with a known weak or non-specific DNA-binding domain, or by using a scrambled version of the TF's own motif. Show that the observed Jaccard values for the TFs in this study are significantly higher than this null. Additionally, perform a control experiment where the GHT-SELEX is performed with a non-DNA-binding protein to assess non-specific background enrichment.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness of the analytical pipeline
  - **Claim pointer** The manuscript claims that MAGIX is a valid statistical framework for identifying enriched genomic intervals from GHT-SELEX data, and that RCADEEM can accurately identify alternative DNA-binding modes of C2H2-zf proteins.
  - **Evidence pointer** Methods sections "MAGIX statistical framework" and "Modeling alternative C2H2-zf binding modes with RCADEEM"; Extended Data Fig. 1
  - **Concern** The description of MAGIX in the Methods is high-level and lacks critical details. The model assumes a Poisson process for read counts, but the text does not specify how overdispersion, which is common in sequencing data, is handled. The choice of prior covariance matrix via empirical Bayes is mentioned, but the sensitivity of the results to this choice is not discussed. For RCADEEM, the method relies on a pre-existing "recognition code" to initialize the model. The accuracy of the final results is therefore dependent on the accuracy of this code, and the text does not provide a measure of how sensitive the RCADEEM output is to errors in the initial predictions. The validation of RCADEEM is shown for CTCF, a well-studied protein, but the text does not provide a systematic validation across the other 85 proteins for which predictions were made.
  - **Why it matters** The conclusions about alternative DNA-binding modes and the utility of the method for C2H2-zf proteins depend entirely on the correctness of these computational tools. If the methods are not robust or are overly sensitive to initial conditions, the biological conclusions may be unreliable.
  - **Resolution test** Provide a more detailed description of the MAGIX model, including how overdispersion is modeled and how the prior is chosen. Perform a sensitivity analysis for RCADEEM by running it with perturbed initial recognition code predictions and showing that the final results are stable. Validate RCADEEM on a set of C2H2-zf proteins with known alternative binding modes, perhaps using mutagenesis or domain-swap experiments.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Completeness of evidence for a key sub-claim
  - **Claim pointer** The manuscript claims that "high specificity can also be obtained from motif scans, but performance is highly dependent on the derivation and use of the motifs, including accounting for multiple local matches."
  - **Evidence pointer** Results section "Multiple explanations for the high sequence specificity observed in GHT-SELEX"; Figure 5
  - **Concern** The finding that sum-of-affinity scoring outperforms maximum or log-odds scoring for PWM scans is interesting and practically important. However, the text does not provide a clear explanation of why this is the case. The authors suggest it reflects "avidity" or cooperative binding, but this is speculative. The analysis is also limited to the TFs in this study, and it is not clear if this finding generalizes. The text states that "there were still many TFs for which we could not derive a PWM that rivals GHT-SELEX data," which suggests that the PWM model is still insufficient for a large fraction of TFs. The authors should clarify the fraction of TFs for which the PWM approach works well and the properties of those TFs.
  - **Why it matters** This is a practical claim that could influence how researchers use PWM-based scans. If the finding is not general or the reasons are not understood, its utility is limited.
  - **Resolution test** Provide a more detailed analysis of the TFs for which sum-of-affinity scoring works well versus those for which it does not. Test the sum-of-affinity approach on an independent dataset of TFs with known in vivo binding sites. Provide a more rigorous test of the "avidity" hypothesis, perhaps by comparing the predicted cooperative binding sites with experimentally validated cooperative interactions.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity and completeness of reporting
  - **Affected element** Methods section "GHT-SELEX and HT-SELEX library preparation"
  - **Evidence pointer** Methods section
  - **Issue** The description of the GHT-SELEX library preparation is missing some practical details. The text states that the DNA was fragmented to a median length of ~64 bp, but it does not specify the range of fragment sizes or the method used for size selection. The number of PCR cycles for library amplification is not stated.
  - **Required correction** Provide the full size range of the fragmented DNA and the specific size selection method. State the number of PCR cycles used in library preparation.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results section "Unexpectedly high overlap between TF binding to the genome in vitro and in vivo"
  - **Evidence pointer** Figure 4c
  - **Issue** The Wilcoxon test is used to compare the observed Jaccard values to the permuted values. The text reports a p-value of 1.3x10^-39. While this is highly significant, the text does not state the number of permutations used or whether the test is one-sided or two-sided.
  - **Required correction** State the number of permutations and the direction of the test.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Interpretation of results
  - **Affected element** Discussion section
  - **Evidence pointer** Discussion
  - **Issue** The authors speculate that TFs with high intrinsic specificity may be able to "overcome the chromatin state." This is an interesting idea, but it is not directly tested in this manuscript. The text should be clearer that this is a hypothesis, not a conclusion.
  - **Required correction** Rephrase the statement to clearly indicate that this is a speculative interpretation that requires further testing.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Resource availability
  - **Affected element** Data Availability section
  - **Evidence pointer** Data Availability section
  - **Issue** The data availability statement mentions that the entire Codebook data structure is available at a website, but it is not clear if this includes all the processed data and results from this specific manuscript, or just the raw data.
  - **Required correction** Clarify what exactly is available at the website, and whether it includes all the processed data, peak calls, and motif models used in this study.

## Risk / unsupported claims

- The claim that "many human TFs possess much higher sequence specificity than anticipated" is not fully supported without a clear null model for the GHT-SELEX/ChIP-seq overlap.
- The claim that GHT-SELEX peaks are "often surprisingly similar" to ChIP-seq peaks is based on a median Jaccard value of 0.127, but the significance of this value is not established in the provided text.
- The claim that "it is common for TFs to possess sufficient intrinsic specificity to delineate a large fraction of in vivo genomic targets" is a strong statement that requires the above points to be resolved.
- The performance of RCADEEM is only validated for CTCF in the provided text. Its accuracy for the other 85 proteins is not demonstrated.
- The claim that sum-of-affinity scoring reflects "avidity" is speculative and not directly tested.
- The success rate of GHT-SELEX for the Codebook proteins is stated as 78% (139/177), but this is based on the assumption that the 163 unsuccessful proteins "simply do not bind DNA with sequence specificity." This is an assumption, not a proven fact, and the text acknowledges this but the framing could be misleading.
- The statement that "the number of in vivo binding sites that are specified intrinsically by TFs is relatively small" is based on the "Top N" analysis, but the interpretation of this result depends on the choice of N and the properties of the Jaccard statistic, which are not fully explored.

## Assessment against Nature-style criteria

- **Originality** The work is highly original. The concept of using genomic DNA as a substrate for SELEX is a novel and powerful idea. The finding that C2H2-zf proteins use alternative DNA-binding domains is a significant conceptual advance. The observation that PWM scanning can be as effective as experimental data when used appropriately challenges existing assumptions.
- **Scientific importance** The findings have the potential to change how the field thinks about TF binding specificity and its role in vivo. The large dataset of new TF motifs will be a valuable community resource. The methodological advances (GHT-SELEX, MAGIX, RCADEEM) are likely to be widely adopted.
- **Interdisciplinary readership** The topic is of central importance to molecular biology, genomics, and bioinformatics. The findings are likely to be of interest to a broad readership in these fields. The manuscript is written in a way that is largely accessible to a non-specialist, although the Methods section is dense.
- **Technical soundness** The experimental design is generally sound, and the scale of the study is a major strength. However, the lack of a clear null model for the key comparison (GHT-SELEX vs ChIP-seq) is a significant weakness. The computational methods are sophisticated, but the description in the Methods is not sufficient to fully assess their robustness.
- **Readability for nonspecialists** The Summary and Introduction are clear and well-written. The Results section is also readable, but the Discussion could be more explicit about the limitations of the study. The Methods section is highly technical and would be difficult for a non-specialist to follow.

## Recommendation posture

Supportive if technical concerns are resolved. The core idea and the biological findings are potentially very important. However, the central claim of high intrinsic specificity needs to be supported by a more rigorous statistical analysis. The description of the computational methods needs to be more detailed to allow for proper evaluation. If these concerns are addressed, this manuscript would be a strong candidate for publication.