## Review setup
- **Input scope** Full manuscript text (main text, methods, and supplementary figure/table references as described)
- **Assessment boundary** Scientific claims, methodological soundness, validation approach, and generalizability of the DeepRec framework as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present DeepRec, a deep learning framework that encodes DNA physicochemical signatures in the major and minor grooves to predict transcription factor (TF)–DNA binding affinities and interpret binding mechanisms. The framework is claimed to (1) outperform or complement sequence-based one-hot encoding by capturing physicochemical dependencies between base pairs, (2) predict DNA contacts consistent with co-crystal structures for MAX, MEF2B, p53, ATF4, and C/EBPβ, (3) identify binding geometries such as bidentate H-bonds and methyl-Arg-G triads, and (4) predict the effects of cytosine methylation on TF binding without expanding the feature space.
- **Visible evidence base** Main text figures referenced (Figs. 1–6), supplementary figures (S1–S3) and tables (S1) as cited, SELEX-seq and EpiSELEX-seq datasets (accession numbers provided), PDB structures (5EYO, 1N6J, 3Q06, 6MG2)
- **Missing materials affecting confidence** Actual figure images, supplementary figures and tables, quantitative performance metrics (e.g., correlation coefficients, AUC values), detailed model architecture specifications, hyperparameter ranges, dataset preprocessing details, and code implementation details are not provided in the supplied text. These are essential for full technical evaluation.

## Reviewer
- **Overall assessment** The manuscript presents a conceptually interesting and potentially valuable approach to modeling TF–DNA binding by moving beyond nucleotide sequence to physicochemical signatures. The idea of encoding base-pair chemistry directly, rather than expanding sequence alphabets, is elegant and addresses a real limitation of current methods. The application to modified bases (e.g., 5mC) without feature expansion is a notable strength. However, the manuscript as provided lacks critical quantitative validation details, comparative benchmarks against existing methods, and clear evidence that the physicochemical encoding provides superior predictive performance over simpler sequence-based approaches. The claims of mechanistic insight are supported only by qualitative agreement with a small number of co-crystal structures, and the statistical rigor of these comparisons is not established. The writing is generally clear but some methodological details are underspecified. Overall, the core idea has merit, but the evidence presented is insufficient to fully establish the claimed advantages.

- **Who would be interested in the results, and why** Researchers in computational biology, specifically those working on TF–DNA binding prediction, protein–DNA recognition mechanisms, and the functional effects of DNA modifications such as methylation. The approach may also interest experimentalists studying TF binding mechanisms who could use DeepRec as a hypothesis-generating tool. The broader chromatin biology and gene regulation communities would find the application to modified bases relevant, particularly given the growing interest in epigenetic regulation.

- **Major strengths** 
  1. The physicochemical encoding scheme is conceptually novel and addresses a genuine limitation of sequence-based models, particularly for modified bases.
  2. The framework is generalizable across TF families with different binding mechanisms (major groove, minor groove, combined).
  3. The perturbation-based interpretation approach provides mechanistic insights that go beyond simple motif discovery.
  4. The ability to model methylated and unmethylated data without expanding feature dimensions is practically important.
  5. The authors acknowledge limitations and future improvements, which is commendable.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "DeepRec accurately predicts possible binding contacts for several TFs across TF families at physicochemical resolution"
- **Evidence pointer** Figures 3–6, supplementary figures S1–S3; quantitative metrics not provided in text
- **Concern** The manuscript claims accurate prediction of binding contacts but provides no quantitative performance metrics. No correlation coefficients, AUC values, precision-recall scores, or any statistical measures of predictive accuracy are reported in the main text. The only quantitative statement is "The results showed a good correlation" (for cross-platform validation), but the actual correlation value is not given.
- **Why it matters** Without quantitative metrics, the reader cannot assess whether the model performs adequately, how it compares to existing methods, or whether the predictions are statistically meaningful. The claim of "accurate" prediction is unsupported.
- **Resolution test** Provide quantitative performance metrics (e.g., Pearson/Spearman correlation between predicted and measured binding affinities, AUC for binary binding classification) for all tested TFs, including confidence intervals. Compare against a sequence-based baseline model (e.g., one-hot encoding with identical architecture) to demonstrate added value.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "DeepRec is capable of predicting binding mechanisms with respect to the co-crystal structure"
- **Evidence pointer** Figures 3C–F, 4C–F, 5C–D, 6E–H; qualitative visual comparisons only
- **Concern** The validation of predicted contacts against co-crystal structures is purely qualitative. The authors state that predicted features are "consistent with" or "in agreement with" crystal structures, but no systematic quantitative comparison is provided. It is unclear how many predicted contacts were compared, what fraction matched, or whether the agreement exceeds chance.
- **Why it matters** Qualitative visual comparison is subject to confirmation bias and does not establish that the model reliably identifies true binding contacts. A systematic evaluation is needed to support the claim of mechanistic prediction.
- **Resolution test** Define a clear metric for contact prediction accuracy (e.g., fraction of predicted significant positions that correspond to actual protein–DNA contacts within a defined distance threshold in the crystal structure). Report this metric for all TFs and compare against a null model or sequence-based baseline.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "DeepRec predicts the effects of methylation on TF binding using high-throughput binding data and explain possible binding mechanisms"
- **Evidence pointer** Figure 6, supplementary figure S3; dataset accessions provided
- **Concern** The methylation analysis is described qualitatively. The authors state that predictions "showed a decrease in binding affinity" for ATF4 and "weak or no preference" for C/EBPβ, but no quantitative measures of predicted versus measured methylation effects are provided. The comparison to previous studies is mentioned but not quantified.
- **Why it matters** The ability to predict methylation effects is a key claimed advantage of the physicochemical encoding. Without quantitative validation against experimental measurements, this claim is not established.
- **Resolution test** Provide quantitative comparison between predicted methylation effects (difference in predicted binding affinity between methylated and unmethylated sequences) and experimentally measured effects (e.g., from EpiSELEX-seq enrichment ratios). Report correlation coefficients and error metrics.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "Compared to the one-hot sequence-encoding scheme, our method provides a fundamental description of the actual molecular interactions between TFs and DNA"
- **Evidence pointer** Figure 1, methods section; no direct comparison shown
- **Concern** The claimed advantage over one-hot encoding is not directly demonstrated. No experiments are shown that compare DeepRec's performance with physicochemical encoding versus the same architecture with one-hot sequence encoding. The authors argue conceptually why physicochemical encoding should be better, but provide no empirical evidence.
- **Why it matters** The central premise of the manuscript is that physicochemical encoding is superior to sequence encoding. Without a direct comparison, the added value of the approach is not established.
- **Resolution test** Train the same architecture with one-hot sequence encoding on the same datasets and compare predictive performance, interpretation quality, and ability to capture methylation effects. Report quantitative comparisons.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "DeepRec utilizes a forward perturbation-based approach to calculate the binding difference between the presence and absence of a chemical group at a given position, regardless of nucleotide sequence"
- **Evidence pointer** Methods section, Figure 2D; implementation details not provided
- **Concern** The perturbation approach is described at a high level, but critical details are missing. How exactly is a physicochemical signature "nullified"? How are the four positions (Pos1–4) in the major groove and three in the minor groove defined for different base pairs? How are the perturbations propagated through the network? What is the mathematical definition of –ΔΔΔG?
- **Why it matters** Reproducibility is a core requirement for computational methods. Without these details, other researchers cannot implement or validate the approach.
- **Resolution test** Provide a complete mathematical description of the encoding scheme, the perturbation procedure, and the calculation of –ΔΔΔG. Include pseudocode or a detailed algorithm description. Make the code publicly available with documentation.

- **Concern ID** R1-M6
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "We selected these TFs based on the primary consideration that they have representative binding mechanisms, and they each have available high-quality high-throughput experimental data and corresponding co-crystal structures"
- **Evidence pointer** Results section; dataset details not provided
- **Concern** The manuscript does not describe the datasets used for training and validation in sufficient detail. How many sequences were used for each TF? What was the sequence length? How were training/validation/test splits performed? Were the same sequences used across TFs? How were the EpiSELEX-seq data processed and combined?
- **Why it matters** Dataset characteristics significantly affect model performance and generalizability. Without this information, the results cannot be properly interpreted or reproduced.
- **Resolution test** Provide detailed dataset descriptions including sequence counts, lengths, source experiments, preprocessing steps, and train/validation/test splits for each TF.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure 1 description
- **Evidence pointer** Figure 1, main text
- **Issue** The description of the physicochemical signature positions in Figure 1 is brief. The distinction between major and minor groove positions and how they map to specific atoms is not fully explained in the main text.
- **Required correction** Expand the figure legend and main text description to clearly define each position (Pos1–4 in major, Pos1–3 in minor) and the specific atoms or chemical groups they represent.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Hyperparameter search
- **Evidence pointer** Methods section, Figure 2B
- **Issue** The hyperparameter search is described as sampling 100 random parameter sets, but the ranges for each parameter are only given in the supplementary table. The criteria for selecting the best parameter set beyond "averaging the three r2 values" are not fully specified.
- **Required correction** Provide the parameter ranges in the main text or clearly reference the supplementary table. Specify whether any additional criteria (e.g., model complexity, overfitting checks) were used in parameter selection.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Readability
- **Affected element** Definition of –ΔΔΔG
- **Evidence pointer** Results section, Figure 3A
- **Issue** The term –ΔΔΔG is introduced without a clear definition in the main text. The reader is referred to the SI Appendix, but the main text should provide at least a brief explanation.
- **Required correction** Add a brief definition of –ΔΔΔG in the main text, explaining how it relates to binding free energy changes and how it is computed from the perturbation analysis.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion of limitations
- **Evidence pointer** Conclusions section
- **Issue** The limitations section mentions that the number of physicochemical signature positions "might be vague" and that discrete encoding treats O and N as equal, but does not discuss potential limitations of the training data (e.g., potential biases in SELEX-seq data) or the generalizability to other TF families beyond the five tested.
- **Required correction** Add a brief discussion of potential data biases and the expected generalizability to other TF families and binding mechanisms.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Readability
- **Affected element** Figure 6 description
- **Evidence pointer** Figure 6, main text
- **Issue** The description of Figure 6 is dense and the relationship between panels (A–H) is not always clear. The text jumps between predictions, comparisons, and crystal structure validations.
- **Required correction** Restructure the description of Figure 6 to clearly separate prediction results, validation against experimental data, and structural interpretation.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Cross-platform validation
- **Evidence pointer** Supplementary figures S1–S2
- **Issue** The cross-platform validation with SMiLE-seq data is mentioned but not described in detail. The correlation is stated as "good" but no quantitative value is given.
- **Required correction** Provide the actual correlation value and describe the SMiLE-seq dataset and validation procedure in the main text or supplementary material.

- **Concern ID** R1-m7
- **Severity** Minor
- **Axis** Readability
- **Affected element** Author contributions and acknowledgments
- **Evidence pointer** End of manuscript
- **Issue** The acknowledgments are placed under "Author contributions" and the funding information is mixed with acknowledgments. This is a formatting issue that should be corrected.
- **Required correction** Separate acknowledgments from author contributions and ensure funding information is properly listed.

## Risk / unsupported claims
- The claim that DeepRec "accurately predicts possible binding contacts" is unsupported by quantitative metrics in the provided text.
- The claim that the physicochemical encoding is superior to one-hot sequence encoding is not empirically demonstrated.
- The claim that DeepRec "reveals effects of chemical DNA modifications" is supported only by qualitative descriptions without quantitative validation.
- The generalizability of the framework to other TF families beyond the five tested is asserted but not demonstrated.
- The statement that "thymine mimicry could possibly be learned from the methyl group of thymine in the unmethylated data" is speculative and not rigorously tested.
- The claim that the encoding method "can be easily expanded to studies beyond the concept of DNA sequence" is plausible but not demonstrated with examples beyond methylation.
- The performance of the model in terms of predictive accuracy relative to existing state-of-the-art methods is not assessed.