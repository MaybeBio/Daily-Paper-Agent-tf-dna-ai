## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, conclusion, data availability, author contributions, conflict of interest, publisher's note, supplementary material notice)
- **Assessment boundary** Scientific and technical evaluation of the reported methods, results, and claims as presented in the provided text. No external data, code, or supplementary files were accessed.
- **Shared manuscript claim summary** The authors report that DeeperBind, trained via DeepRAM on the Colab platform, achieves AUC above 0.96 for MYC binding site prediction when trained on multiple cell lines. Analysis of learned filters reveals the canonical E-box CACGTG and a non-canonical motif resembling SP1 and MIZ-1 consensus sequences, suggesting the model can distinguish activation-associated and repression-associated MYC binding contexts.
- **Visible evidence base** Abstract; Introduction; Materials and methods (narrative description, no code or full architecture details); Results (Tables 1-3 referenced, Figure 3 referenced, Figure 4 referenced); Conclusion; Data availability statement; Author contributions; Conflict of interest; Publisher's note; Supplementary material notice.
- **Missing materials affecting confidence** Tables 1-3 and Figures 2-4 are referenced but not provided in the submitted text. No code, hyperparameters, dataset details, or evaluation scripts are included. No comparison with existing tools beyond a brief mention. No statistical significance tests or confidence intervals are reported in the text.

## Reviewer
- **Overall assessment** The manuscript addresses a relevant problem in computational genomics, namely the prediction of MYC transcription factor binding sites using deep learning. The reported AUC values are high, and the observation that learned filters recapitulate known motifs is interesting. However, the manuscript as presented has substantial gaps in methodology reporting, lacks quantitative comparisons with existing tools, and makes claims about functional discrimination (activation vs repression) that are not supported by the evidence provided. The text contains several typographical and grammatical errors that impede readability. The core case, that this approach offers a meaningful advance over existing methods, is not established from the supplied material.
- **Who would be interested in the results, and why** Researchers working on transcription factor binding prediction, particularly those focused on MYC and its role in cancer, may find the reported AUC values and motif discovery results of interest. The potential to identify repression-associated motifs could be relevant to those studying MYC-mediated transcriptional repression. However, the lack of rigorous benchmarking limits the utility for practitioners seeking to choose among available tools.
- **Major strengths** The problem is well motivated, given MYC's importance in cancer. The use of a deep learning approach that learns motifs without prior specification is appropriate. The observation that the model learns both canonical and non-canonical motifs, and that these may correspond to activation and repression contexts, is a potentially interesting finding. The use of dinucleotide shuffling for negative controls is a sound methodological choice.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (lack of dataset and preprocessing details), R1-M2 (lack of comparison with existing tools), R1-M3 (unsupported claim about activation/repression discrimination), R1-M4 (incomplete reporting of results and figures).
- **Assessment against Nature-style criteria** Originality: moderate. The application of an existing tool (DeeperBind) to MYC is incremental, though the focus on repression-associated motifs is somewhat novel. Scientific importance: potentially high if the claims were rigorously supported, but the current evidence is insufficient. Interdisciplinary readership: the topic is of interest to computational biologists and cancer researchers, but the presentation is not accessible to a broad audience due to unclear writing and missing context. Technical soundness: not established from the provided material due to missing methodological details and lack of benchmarking. Readability for nonspecialists: poor, due to numerous typographical errors, unclear sentences, and undefined terms.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript requires major revisions, including full methodological transparency, rigorous benchmarking, and tempering of claims, before the case can be considered.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors claim that DeeperBind achieves AUC above 0.96 for MYC binding site prediction when trained on multiple cell lines.
- **Evidence pointer** Materials and methods, Results, Table 1 (not provided)
- **Concern** The manuscript does not provide sufficient details on the datasets used, including the specific ChIP-seq experiments, the number of peaks, the criteria for selecting the 4000 sequences per experiment, the generation of negative sequences beyond the mention of dinucleotide shuffling, or the train/validation/test splits. Without these details, the reported AUC cannot be independently assessed or reproduced.
- **Why it matters** Reproducibility is a core requirement for computational biology studies. The lack of dataset and preprocessing details prevents other researchers from replicating the experiments or evaluating the robustness of the results.
- **Resolution test** Provide a complete description of all datasets, including accession numbers, peak calling methods, filtering criteria, and exact train/validation/test splits. Include the code and configuration files used for training.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The authors imply that their approach offers improved performance over existing tools, stating "an accuracy above 0.96 AUC" and "a substantial improvement in the accuracy (AUC), when we move from a training set extracted from just one cell line to one coming from multiple."
- **Evidence pointer** Results, Table 2 (not provided), Figure 3 (not provided)
- **Concern** No direct comparison with existing MYC binding site prediction tools or with the original DeepBind/DeeperBind implementations is provided. The only comparison mentioned is with "the original Deepbind experiments," but the details are not given, and the authors note that a full comparison is not possible due to different training set sizes. Without benchmarking against state-of-the-art methods on the same datasets, the claimed advantage is not established.
- **Why it matters** For a tool to be adopted, it must demonstrate clear advantages over existing approaches. The absence of a rigorous comparison undermines the scientific contribution of the work.
- **Resolution test** Perform a benchmark study comparing DeeperBind (as configured here) with at least two existing MYC binding site prediction tools on the same datasets, using identical evaluation metrics and statistical tests.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim support
- **Claim pointer** The authors state that the non-canonical motif "shares similarities with the one recognized by the RPBJ factor" and that it "can be split into two DNA regions which share some degree of similarity with the DNA consensus sequences respectively recognized by the SP1 transcription factor (C/G rich region) or the MIZ-1 initiation factor (TGGGA), usually used by MYC to exert transcriptional repression." They further claim that the PWM from the non-canonical filter had higher affinity for 14 of 21 repression targets, supporting a role in repression.
- **Evidence pointer** Results, Figure 4 (not provided), Table 3 (not provided)
- **Concern** The analysis linking the non-canonical motif to repression is based on a very small set of 21 repression targets and 53 activation targets. The authors do not report any statistical significance testing for the observed enrichment. The similarity to SP1 and MIZ-1 motifs is described qualitatively, without quantitative motif comparison metrics. The claim that the model can discriminate activation from repression contexts is therefore not supported by the evidence.
- **Why it matters** The potential to identify repression-associated motifs is the most novel aspect of the work. If this claim is not rigorously supported, the manuscript's contribution is substantially diminished.
- **Resolution test** Provide a statistical analysis (e.g., Fisher's exact test or a permutation test) for the enrichment of the non-canonical motif in repression targets. Include quantitative motif similarity scores (e.g., Tomtom) against known SP1 and MIZ-1 motifs. Increase the size of the validation set if possible.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The authors report results in Tables 1-3 and Figures 2-4, but these are not included in the submitted text.
- **Evidence pointer** Results, Tables 1-3, Figures 2-4 (all not provided)
- **Concern** The manuscript references multiple tables and figures that are essential for evaluating the claims, but none are provided in the text. The reader cannot assess the reported AUC values, the motif logos, or the PWM scores.
- **Why it matters** Without the actual data and visualizations, the results cannot be verified or interpreted. This is a fundamental issue that prevents any meaningful evaluation of the work.
- **Resolution test** Include all tables and figures in the manuscript, with clear captions and legends. Ensure that all data points are accessible.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Abstract, Introduction, Materials and methods, Results, Conclusion
- **Evidence pointer** Throughout the text
- **Issue** The manuscript contains numerous typographical and grammatical errors, including "Ifox. Iftbox1" (Introduction), "trascriptional" (Introduction), "versatilily" (Introduction), "sub-motifes" (Materials and methods), "obtaines" (Conclusion), and "were it maps" (Conclusion). These errors impede readability and suggest a lack of careful proofreading.
- **Required correction** Perform a thorough language edit of the entire manuscript.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Materials and methods
- **Evidence pointer** "We then sorted each of the retrieved experimental data according to the score associated to each peak, that is, the Myc binding site, selecting peaks with the highest score from each experiment."
- **Issue** The description of peak selection is unclear. It is not specified how many peaks were selected per experiment, what score threshold was used, or how the 4000 sequences per experiment were chosen.
- **Required correction** Clarify the peak selection criteria and the exact number of sequences used for training, validation, and testing.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Accuracy
- **Affected element** Introduction
- **Evidence pointer** "Myc regulates about two thousand genes which can be, however, in part different, depending on the type of tissues and tumours."
- **Issue** The number of genes regulated by MYC is stated without a citation. This is a specific quantitative claim that should be supported by a reference.
- **Required correction** Add a citation for the number of MYC-regulated genes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Consistency
- **Affected element** Results and Conclusion
- **Evidence pointer** The Results section mentions "the non-canonical consensus sequence" and Figure 4, while the Conclusion refers to "the consensus sequence TGGGA, associated with the RPBJ factor." The text in the Results also mentions RPBJ, but the Conclusion does not mention SP1 or MIZ-1.
- **Issue** The description of the non-canonical motif is inconsistent between sections. The Results mention similarity to SP1 and MIZ-1, while the Conclusion only mentions RPBJ. This inconsistency is confusing.
- **Required correction** Ensure that the description of the non-canonical motif is consistent throughout the manuscript.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Data availability statement
- **Evidence pointer** "The original contributions presented in the study are included in the article/Supplementary material, further inquiries can be directed to the corresponding author."
- **Issue** The data availability statement is vague. It does not specify what data or code are available, or under what license.
- **Required correction** Provide a detailed data availability statement, including links to any deposited data or code.

## Risk / unsupported claims
- The claim that the model achieves AUC above 0.96 is not verifiable without the actual results tables and figures.
- The claim that the non-canonical motif is associated with MYC-mediated repression is not statistically supported.
- The claim that the model can discriminate activation-associated from repression-associated MYC binding sites is not supported by the evidence.
- The claim of "substantial improvement" in accuracy when training on multiple cell lines is not supported by a quantitative comparison.
- The claim that the non-canonical motif shares similarity with RPBJ, SP1, and MIZ-1 motifs is qualitative and not quantitatively assessed.
- The statement that MYC regulates "about two thousand genes" is not cited.