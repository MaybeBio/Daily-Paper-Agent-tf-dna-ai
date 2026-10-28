## Review setup
- **Input scope** Full manuscript text including abstract, introduction, methods, results, discussion, and conclusions
- **Assessment boundary** Scientific validity, methodological soundness, interpretation of results, and claims made relative to the evidence presented
- **Shared manuscript claim summary** The authors present CycPred, a deep learning CNN/LSTM model trained on loop-seq data, to predict DNA cyclizability at genomic scale. They report species-specific flexibility patterns around transcription start sites, no general rigid region upstream of TSSs, transcription-factor-dependent flexibility preferences, and associations between rigid DNA regions and mutation/crossing-over events in Arabidopsis thaliana.
- **Visible evidence base** Abstract, full introduction, materials and methods (datasets, model design, statistical analyses), results sections with figures referenced (Figures 1-9, Supplementary Figures S1-S4), discussion, conclusions, availability statement
- **Missing materials affecting confidence** Actual figure images and supplementary figures not provided; exact model hyperparameters and training details only partially described; no code or reproducibility details beyond repository link; no detailed statistical outputs (exact p-values, confidence intervals) for most comparisons; no information on multiple testing corrections

## Reviewer
- **Overall assessment** This manuscript addresses an important and timely topic in genomics and biophysics, namely the prediction and functional interpretation of DNA mechanical properties at genomic scale. The development of CycPred as a computationally efficient alternative to existing tools is a useful contribution. However, the manuscript has several significant weaknesses that currently prevent full support. The central claims regarding functional roles of DNA flexibility are largely based on correlational analyses with modest effect sizes, and the authors themselves acknowledge the need for experimental validation. The lack of clear mechanistic hypotheses, limited methodological detail, and some inconsistencies in interpretation weaken the overall case. The work is likely of interest to the genomics and biophysics communities, but the current evidence base does not fully establish the broader functional claims made in the title and abstract.

- **Who would be interested in the results, and why** Researchers in genomics, chromatin biology, and biophysics would be interested in this work. Specifically, those studying nucleosome positioning, transcription factor binding mechanisms, DNA repair and mutation processes, and meiotic recombination would find the predicted flexibility maps and their associations with genomic features relevant. The computational efficiency of CycPred may also appeal to bioinformaticians seeking scalable tools for genome-wide mechanical property prediction. The cross-species comparisons and the focus on Arabidopsis thaliana provide a plant genomics perspective that broadens the potential audience.

- **Major strengths** 
  1. The development of a computationally efficient deep learning model (CycPred) for DNA cyclizability prediction is a practical contribution, particularly given the demonstrated comparable performance to DNAcycP with substantially lower computational cost.
  2. The systematic cross-species analysis of flexibility patterns around TSSs, covering eight species from different kingdoms, provides a useful comparative framework.
  3. The use of multiple orthogonal genomic datasets in Arabidopsis (methylation, de novo mutations, fixed SNPs, Spo11 crossing-over data) to explore associations with DNA flexibility is commendable.
  4. The authors appropriately acknowledge the correlational nature of their findings and the need for experimental validation.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that CycPred shows "similar performance as DNAcycP" and that the model is reliable for cross-species predictions.
- **Evidence pointer** Results section "The CNN/LSTM model shows similar performance as DNAcycP, while being computationally less expensive"; Materials and Methods "Design and training of the deep learning model"
- **Concern** The performance comparison between CycPred and DNAcycP is limited to correlation coefficients and median distances on two datasets. No information is provided on the variability of these metrics (e.g., confidence intervals, standard errors across multiple runs), nor on other important performance metrics such as mean absolute error, R-squared, or calibration. More critically, the model is trained exclusively on yeast loop-seq data and then applied to eight other species without any explicit validation of cross-species transferability. The authors argue that DNA is a universal polymer, but this does not account for potential species-specific biases in the training data or differences in genomic composition that could affect prediction accuracy.
- **Why it matters** The entire downstream analysis depends on the reliability of CycPred predictions across species. If the model does not generalize well beyond yeast, all cross-species conclusions about flexibility patterns and their functional associations would be compromised. The lack of rigorous performance assessment undermines confidence in the central tool of the study.
- **Resolution test** Provide a more comprehensive performance evaluation including multiple metrics with uncertainty estimates, and ideally validate predictions against experimental measurements from at least one non-yeast species. If cross-species validation is not feasible, clearly state this limitation and temper claims accordingly.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The claim that "rigid regions are generally more susceptible to de novo mutations" and the broader implication that DNA flexibility plays a functional role in mutation processes.
- **Evidence pointer** Results section "De novo mutations and fixed SNPs in Arabidopsis thaliana appear more frequently in rigid genomic DNA contexts"; Figure 9
- **Concern** The analysis comparing windows with and without mutations does not adequately control for confounding factors. Mutation rates are known to vary with many genomic features, including GC content, replication timing, chromatin state, and sequence context. The authors do not perform any multivariate analysis or matching to isolate the effect of DNA flexibility from these potential confounders. Additionally, the effect sizes reported are small (0.059-0.309), and while statistically significant due to large sample sizes, their biological relevance is unclear. The causal direction is also ambiguous: rigid DNA could promote mutations, or mutations could alter local DNA flexibility.
- **Why it matters** The association between DNA flexibility and mutation is presented as one of the key novel findings of the study. Without adequate control for confounders and a clear mechanistic framework, this claim is not established. Overstating this finding could mislead subsequent research in mutation biology.
- **Resolution test** Perform a multivariate analysis controlling for known mutation-associated genomic features, or use a matched-control design. Provide a mechanistic hypothesis for how DNA rigidity could influence mutation rates, and discuss alternative explanations. If the effect does not survive confounder control, revise the claim accordingly.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The claim that "no evidence of a generally present region of lowered flexibility upstream of transcription start sites to facilitate transcription factor binding was found."
- **Evidence pointer** Results section "Pronounced changes of cyclizability around transcription start sites"; Figure 2
- **Concern** This finding directly contradicts previous reports, including the yeast study by Basu et al. (28) that provided the training data. The authors do observe a rigid region upstream of TSSs in yeast, consistent with prior work, but not in other species. However, the interpretation is complicated by the fact that the model was trained on yeast data. If the model has learned yeast-specific features, it may not accurately predict flexibility in other species, making cross-species comparisons of TSS-proximal patterns unreliable. Additionally, the TSS annotations used may vary in quality across species, and the choice of a single isoform per gene could introduce bias.
- **Why it matters** The absence of a conserved rigid region upstream of TSSs is a notable negative finding that challenges existing models of transcription initiation. If this claim is incorrect due to methodological limitations, it could mislead the field. Conversely, if correct, it has important implications for understanding species-specific mechanisms of transcription regulation.
- **Resolution test** Validate the model predictions against experimental flexibility measurements in at least one non-yeast species. Perform sensitivity analyses using different TSS annotation sources and including all isoforms. Discuss the implications of the yeast-trained model for cross-species predictions in more detail.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** The claim that "crossing-over and mutation rates, both de novo and fixed, were found to be linked to rigid sequence regions" in Arabidopsis.
- **Evidence pointer** Results section "Analysis of Spo11 oligonucleotides"; Figure 9
- **Concern** The Spo11 analysis shows a statistically significant but very weak correlation (r=-0.003) between Spo11 signal and cyclizability. The authors then resort to a percentile-based comparison to find an association, which is a post-hoc analysis approach. The odds ratio of 1.15 for the top/bottom 2% comparison, while significant, represents a modest enrichment. The biological significance of this effect size is questionable, and the analysis does not account for the known enrichment of Spo11 hotspots in promoter regions, which are also regions of characteristic flexibility patterns. The relationship between DNA flexibility and crossing-over may be indirect, mediated by other features of promoter regions.
- **Why it matters** The link between DNA mechanics and meiotic recombination is an interesting hypothesis, but the evidence presented is weak. Overinterpreting this association could lead to unwarranted conclusions about the role of DNA flexibility in recombination.
- **Resolution test** Perform a more rigorous analysis that controls for promoter proximity and other known Spo11 hotspot features. Consider using continuous regression approaches rather than dichotomized percentile comparisons. Discuss the biological plausibility of the effect size in the context of known recombination mechanisms.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction and Discussion
- **Evidence pointer** Introduction, Discussion
- **Issue** The manuscript assumes substantial background knowledge in both deep learning and DNA biophysics. Terms such as "cyclizability," "loop-seq," and "CNN/LSTM" are introduced but not explained sufficiently for readers outside these specific subfields. The significance of the findings for broader biological questions could be articulated more clearly.
- **Required correction** Provide brief explanations of key technical terms when first introduced. Add a short paragraph in the Discussion that explicitly states the broader implications of the findings for understanding genome function, written in accessible language.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and Methods, "Design and training of the deep learning model"
- **Evidence pointer** Materials and Methods section
- **Issue** The description of the model architecture and training procedure lacks sufficient detail for reproducibility. Hyperparameters (number of layers, filter sizes, learning rate, batch size, epochs, etc.) are not specified. The train/validation/test split procedure is only partially described.
- **Required correction** Provide a complete description of the model architecture and training hyperparameters, either in the main text or as a supplementary table. Include details on data preprocessing, augmentation (if any), and the exact splitting procedure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Results section "A subgroup of Arabidopsis thaliana transcription factors shows distinct DNA rigidity patterns at their binding position compared to non-binding locations of the same motif"
- **Evidence pointer** Results section, Figure 7
- **Issue** The analysis of transcription factor binding is presented briefly, and the criteria for selecting the 25 TFs with "sufficient data" are not clearly defined. The distinction between "bound" and "unbound" motifs relies on DAP-seq data, but the threshold for calling a motif bound is not specified.
- **Required correction** Clarify the criteria for TF selection and the definition of bound versus unbound motifs. Provide more detail on the statistical methods used to compare flexibility profiles between bound and unbound sites.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Materials and Methods, "Statistical analysis of trends in cyclizability at a genomic scale"
- **Evidence pointer** Materials and Methods section
- **Issue** The shuffling procedures are described, but the number of shuffles used for the genomic-scale analysis is not stated. The choice of five shuffles for the whole-genome analysis seems arbitrary and may not provide stable estimates.
- **Required correction** State the number of shuffles used for each analysis and justify this choice. Consider reporting the variability of the shuffled estimates.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Discussion section
- **Issue** The Discussion is largely a summary of the results without deep engagement with the broader literature on DNA mechanics and genome function. The authors do not adequately address how their findings relate to or extend previous work beyond the immediate comparisons to Basu et al. and Li et al.
- **Required correction** Expand the Discussion to place the findings in the context of the wider literature on DNA biophysics, chromatin organization, and genome evolution. Address potential alternative interpretations and propose specific experimental tests of the hypotheses generated.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Abstract
- **Evidence pointer** Abstract
- **Issue** The abstract is dense and technical, making it difficult for a broad readership to grasp the key findings and their significance. The phrase "potentially new functional roles of DNA-flexibility" in the title is vague.
- **Required correction** Revise the abstract to more clearly state the main findings and their implications in accessible language. Consider making the title more specific about the nature of the findings.

## Risk / unsupported claims
- The claim that CycPred predictions are reliable across species is not supported by direct validation data.
- The claim that rigid DNA regions are "generally more susceptible to de novo mutations" is not adequately supported due to lack of confounding factor control.
- The claim that crossing-over sites are linked to rigid DNA regions is based on a weak correlation and a post-hoc percentile analysis.
- The statement that "no evidence of a generally present region of lowered flexibility upstream of TSSs" is presented as a general finding, but the analysis relies on a model trained on yeast data, and the possibility of species-specific prediction biases is not addressed.
- The biological significance of the reported effect sizes (mostly small) is not discussed in the context of known mechanisms.
- The claim that "higher order motifs may also play an important role" is based on a single motif (GAAGAGC) and limited analysis.
- The assertion that the autocorrelation decay distance of ~50 bp has implications for DNA looping models is speculative and not directly tested.