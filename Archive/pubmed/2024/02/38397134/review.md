## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Methods, results, and conclusions as presented in the provided manuscript
- **Shared manuscript claim summary** The authors present DARDN, a dual-CNN deep learning method with residual connections, for classifying long DNA sequences surrounding cancer-specific CTCF binding sites versus constitutive CTCF binding sites. They use DeepLIFT for interpretability to identify sequence motifs of potential oncogenic transcription factors. The method is validated on simulated data and applied to six cancer types, with RBPJ identified in T-ALL and cancer-type-specific motifs reported for AML, BRCA, CRC, LUAD, and PRAD.
- **Visible evidence base** Methods section (Sections 2.1-2.3), Results sections (3.1-3.3), Figures 1-5 referenced, Appendix tables and figures referenced
- **Missing materials affecting confidence** Actual figure images, appendix tables (A1-A5), appendix figures (A1-A5), hyperparameter details, training/validation split specifics, code availability, and full motif enrichment results

## Reviewer
- **Overall assessment** The manuscript addresses an important problem in cancer genomics: identifying sequence features that distinguish cancer-specific CTCF binding sites from constitutive ones, without prior localization information. The combination of CNNs with DeepLIFT for long-range regulatory feature discovery is a reasonable approach. However, the manuscript has several technical weaknesses that undermine confidence in the central claims. The validation on simulated data is overly simplistic, the robustness evaluation is incomplete, and the biological interpretation of identified motifs lacks experimental or orthogonal support. The claim of identifying "oncogenic regulatory features" is not fully established from the provided evidence.
- **Who would be interested in the results, and why** Researchers in computational genomics, cancer epigenomics, and regulatory biology would be interested. The method addresses a real challenge in analyzing long regulatory regions and could be applicable to other contexts where distal regulatory elements need to be identified from sequence alone. The cancer-type-specific motif findings could be of interest to those studying transcriptional dysregulation in specific cancers.
- **Major strengths** The problem is well-motivated and clinically relevant. The method is designed to be simple and versatile, relying only on DNA sequence. The use of DeepLIFT for interpretability is appropriate. The authors test multiple cancer types, which strengthens the generalizability claim. The simulation study provides a basic proof-of-concept.
- **Major Concerns** See detailed items below.
- **Minor Comments** See detailed items below.
- **Technical failings that need to be addressed before the case is established** R1-M1 (simulation validation), R1-M2 (robustness evaluation), R1-M3 (biological validation), R1-M4 (model architecture justification)
- **Assessment against Nature-style criteria** Originality: moderate. The combination of dual CNNs with residual connections and DeepLIFT for this specific problem is somewhat novel, but the individual components are well-established. Scientific importance: potentially high if the findings are robust, but the current evidence does not fully support the claims. Interdisciplinary readership: the topic is relevant to both computational and biological audiences, but the presentation is more suited to a specialized computational journal. Technical soundness: several concerns as detailed below. Readability for nonspecialists: the manuscript is generally readable, but some methodological details are unclear.
- **Recommendation posture** Currently not established from the provided evidence. The core claims require additional validation and clarification.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The simulation study demonstrates DARDN's ability to identify inserted RBPJ motifs with 100% accuracy.
- **Evidence pointer** Section 3.1, Figure 2
- **Concern** The simulation is overly simplistic. The authors inserted the exact RBPJ consensus sequence (CCTGGGAA) at random positions in sequences that were selected to have no CTCF binding sites. This creates an artificially easy classification problem where the motif is perfectly conserved and the background is clean. Real regulatory sequences contain degenerate motifs, partial matches, and other confounding features. The 100% accuracy is therefore not informative about real-world performance.
- **Why it matters** The simulation is the primary evidence that the pipeline works. If the simulation does not reflect realistic conditions, the claimed ability to identify oncogenic regulatory features in real data is not supported.
- **Resolution test** The authors should design a more challenging simulation that includes motif degeneracy, background noise, and partial motif occurrences. They should also test whether the method can distinguish between multiple similar motifs and report performance metrics beyond accuracy, such as precision and recall at the motif level.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The robustness evaluation shows consistent RBPJ enrichment across different input sequence lengths and sampling strategies.
- **Evidence pointer** Section 3.2, Figures 3-5
- **Concern** The robustness evaluation has several issues. First, the authors report percentile ranks of RBPJ among enriched motifs, but the total number of motifs detected varies (e.g., 32 vs. 264), making cross-condition comparisons difficult. Second, the sampling experiments show substantial variability in RBPJ rank (e.g., 69th percentile in Run 1 of background sampling), which is not adequately explained. Third, the authors do not report confidence intervals or statistical significance for the motif enrichment. Fourth, the choice of 150 most significant T-ALL-specific CTCF sites for foreground sampling introduces selection bias.
- **Why it matters** The robustness of the method is central to the claim that it can reliably identify oncogenic regulatory features. The current evaluation does not convincingly demonstrate this.
- **Resolution test** The authors should provide a more systematic robustness analysis, including multiple random seeds, statistical significance testing for motif enrichment, and a clear explanation for the observed variability. They should also justify the choice of 150 foreground sites and assess the impact of this selection.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** The method identifies potential oncogenic transcription factors in six cancer types, with RBPJ in T-ALL and other cancer-type-specific motifs.
- **Evidence pointer** Section 3.3, Appendix A
- **Concern** The biological validation is weak. For T-ALL, the authors rely on prior knowledge that RBPJ is an oncogenic TF, but they do not provide independent evidence that the identified RBPJ motifs are functional. For the other five cancer types, the identified motifs are not validated against known biology or experimental data. The claim that these are "potential oncogenic transcription factors" is speculative without functional validation or at least comparison with independent datasets.
- **Why it matters** The scientific importance of the work depends on the biological relevance of the identified features. Without validation, the findings remain computational predictions with uncertain biological significance.
- **Resolution test** The authors should validate a subset of identified motifs using independent methods, such as ChIP-seq data for the predicted TFs, reporter assays, or comparison with known regulatory variants. At minimum, they should compare their findings with existing databases of TF binding and cancer-associated mutations.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** The dual-CNN architecture with residual connections is necessary for improved classification performance.
- **Evidence pointer** Section 2.3, Table 1
- **Concern** The justification for the model architecture is incomplete. The authors state that plain CNNs are "ineffective" and that the dual-CNN with residual connections performs better, but they do not provide a systematic ablation study. It is unclear whether the improvement comes from the dual architecture, the residual connections, the kernel size choices, or some combination. The kernel sizes of 4 and 8 are chosen based on the RBPJ motif, which introduces a potential circularity when evaluating RBPJ enrichment.
- **Why it matters** Understanding which architectural components contribute to performance is important for the method's generalizability and for users who may want to adapt it to other problems.
- **Resolution test** The authors should perform an ablation study that systematically removes or modifies each architectural component (e.g., single CNN, no residual connections, different kernel sizes) and reports the impact on classification performance and motif identification.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.1
- **Evidence pointer** Section 2.1
- **Issue** The description of data augmentation is vague. The authors state that they shift sequences "stochastically between 1 and 5 base pairs" but do not specify the exact procedure, such as whether shifts are applied independently to each sequence, whether both left and right shifts are used, and how many augmented sequences are generated per original sequence.
- **Required correction** Provide a detailed description of the augmentation procedure, including the number of augmented sequences generated and the exact shifting algorithm.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Section 2.3
- **Evidence pointer** Section 2.3
- **Issue** The manuscript does not specify the training procedure in sufficient detail, including the number of epochs, learning rate, batch size, optimizer, and early stopping criteria. This information is essential for reproducibility.
- **Required correction** Add a detailed description of the training procedure, including all hyperparameters and the hardware/software environment used.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 3.2
- **Evidence pointer** Figure 3
- **Issue** The y-axis labels in Figure 3 are not described in the text. It is unclear whether the percentile rank is calculated based on the number of motifs or the enrichment score.
- **Required correction** Clarify the calculation of percentile rank and describe the axes of Figure 3 in the text.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 3.3
- **Evidence pointer** Appendix A
- **Issue** The appendix tables and figures are referenced but not described in the main text. The reader cannot assess the full list of identified motifs without accessing the appendix.
- **Required correction** Provide a summary of the key findings from the appendix in the main text, including the top motifs for each cancer type and their enrichment scores.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.3
- **Evidence pointer** Section 2.3
- **Issue** The description of the DeepLIFT reference value is unclear. The authors state that they use "the averaged frequency at each index" from 80% of constitutive sites, but it is not clear how this is incorporated into the DeepLIFT computation.
- **Required correction** Provide a more detailed explanation of how the reference value is constructed and used in the DeepLIFT analysis.

## Risk / unsupported claims
- The claim that DARDN identifies "potential oncogenic transcription factors" in five cancer types beyond T-ALL is unsupported by functional validation or independent evidence.
- The claim that the method is "broadly applicable for mining insights from diverse biological sequences" is not supported by experiments on diverse sequence types.
- The statement that "long-range interactions exist between cooperating transcription factors and specific CTCF" is inferred from distance distributions but not directly tested.
- The claim that the dual-CNN architecture is superior to plain CNNs is not fully supported without an ablation study.
- The simulation results (100% accuracy) are presented as evidence of validity but are not representative of real-world complexity.