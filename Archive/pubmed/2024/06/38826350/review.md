## Review setup
- **Input scope** Full manuscript text (preprint, bioRxiv 2024.05.23.594371)
- **Assessment boundary** Scientific content, methodology, claims, and evidence as presented in the provided text. No supplementary figures, tables, or data files were available for inspection.
- **Shared manuscript claim summary** The authors report ChIP-Seq mapping of in vivo DNA binding for 139 E. coli transcription factors, and introduce BoltzNet, a neural network that predicts TF-DNA binding energy from sequence using a biophysically motivated architecture. They report models for 125 TFs, validate predictions with Library-ChIP and biolayer interferometry, and draw conclusions about clustered binding sites, accessory bases, weak binding, and genome background affinity.
- **Visible evidence base** Main text figures referenced (Figures 1-6), methods text, and abstract. Supplementary figures and tables (Figure S1-S21, Tables S1-S3) are mentioned but not provided.
- **Missing materials affecting confidence** Supplementary figures and tables, raw ChIP-Seq data, model parameters, training details, BLI raw traces, Library-ChIP library composition, and code. These are essential for full verification of the claims.

## Reviewer

- **Overall assessment** This manuscript presents a substantial dataset and a novel modeling approach with clear potential value to the prokaryotic gene regulation community. The biophysical grounding of the neural network architecture is a genuine strength and distinguishes this work from purely black-box deep learning approaches. However, the provided text does not contain sufficient quantitative detail to fully assess model performance, validation rigor, or the strength of several biological conclusions. The claims regarding genome-wide prediction, quantitative energy accuracy, and physiological relevance require the supplementary materials and additional analyses to be fully established.

- **Who would be interested in the results, and why** Researchers studying bacterial gene regulation, transcription factor DNA-binding specificity, and biophysical modeling of protein-DNA interactions. The ChIP-Seq compendium for 139 E. coli TFs is a resource of broad utility. The BoltzNet architecture may interest computational biologists developing interpretable neural networks for genomics. Synthetic biologists designing predictable regulatory elements would also benefit from quantitative binding energy prediction.

- **Major strengths**
  1. The scale of the dataset (139 TFs mapped by ChIP-Seq under standardized conditions) is a significant resource contribution.
  2. The BoltzNet architecture is genuinely novel in its explicit biophysical design, with a single energy matrix and exponential activation, directly linking neural network parameters to thermodynamic quantities.
  3. The combination of in vivo (Library-ChIP) and in vitro (BLI) validation for designed sequences is a rigorous approach to testing predictive power.
  4. The demonstration that weak binding sites are accurately modeled and physiologically relevant is an important conceptual contribution.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "BoltzNet accurately predicts enrichment in all experiments" and "BoltzNet accurately predicts binding energy" with R2 values between 0.51 and 0.99.
- **Evidence pointer** Figure 2B, Figure 5, Methods (BoltzNet Training)
- **Concern** The reported R2 range of 0.51-0.99 for BLI validation is very wide. The lower bound (0.51) indicates poor predictive accuracy for at least one TF. The text does not specify which TFs fall at which end of this range, nor the number of sequences tested per TF. Additionally, the training procedure uses the same ChIP-Seq data for both training and reporting training-set R2, which is not a valid measure of generalization. The leave-one-out cross-validation is described only for the top 10 enriched regions of PdhR, not for all 125 models.
- **Why it matters** The central claim of the paper is that BoltzNet provides quantitative, accurate predictions of binding energy. If the accuracy is highly variable across TFs, or if the reported accuracy metrics are based on training data, the generalizability of the approach is not established.
- **Resolution test** Provide per-TF R2 values for both training and held-out data. Report cross-validated accuracy for all 125 models, not just PdhR. Specify the number of BLI-measured sequences per TF and provide the full correlation plots.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "We have generated high-confidence models for 125 TFs" and "models for 125 that passed criteria for accuracy in predicting coverage and for specificity on the whole genome."
- **Evidence pointer** Results (A compendium of TF binding models), Methods (BoltzNet Training)
- **Concern** The criteria for model acceptance are stated as R2 > 0.6 on training set and specificity > 60% on the whole genome. These thresholds appear arbitrary and are not justified. More critically, the specificity calculation is not described. How is a "true" binding site defined for specificity calculation? If it is based on the called enriched regions, the metric is circular. The text also does not state how many of the 14 failed models were close to passing, which would indicate whether the thresholds are meaningful.
- **Why it matters** The claim of 125 high-confidence models is a key deliverable. If the acceptance criteria are weak or circular, the number of reliable models may be substantially lower.
- **Resolution test** Clearly define the specificity metric and the reference set of true binding sites. Provide a distribution of R2 and specificity values across all 139 TFs, and justify the chosen thresholds.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Scientific importance
- **Claim pointer** "The majority (>79%) of protein molecules for our studied TFs are bound 'non-specifically' to genome rather than being free in solution."
- **Evidence pointer** Results (Transcription factors primarily bound non-specifically to genome), Figure 6
- **Concern** This is a striking claim with significant implications for understanding TF cellular function. However, the calculation depends on several assumptions: the estimated number of TFs per cell, the volume of the cell, the genome-wide energy distribution, and the extrapolation from 101 bp windows to the entire genome. The text does not provide the calculation details or the uncertainty in these estimates. The claim also appears to be based on only 5 TFs studied by BLI, yet is generalized to all 125 modeled TFs.
- **Why it matters** If correct, this finding changes the conceptual framework for TF search and binding in bacteria. If the calculation is fragile, the claim could be misleading.
- **Resolution test** Provide the full calculation with all assumptions stated. Show how the estimate varies with reasonable changes in TF copy number, cell volume, and energy threshold. State whether this analysis was performed for all 125 TFs or only the 5 with BLI data.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "BoltzNet sums the contributions of clustered sites, the accuracy of which suggests that cooperative interactions do not substantially impact occupancy."
- **Evidence pointer** Results (Role of clustered binding sites and accessory bases), Figure 3C
- **Concern** This is an important negative result, but the evidence presented in the text is indirect. The accuracy of predictions for sequences with clustered sites is consistent with additive energy contributions, but it does not directly rule out cooperative interactions that happen to have similar net effects. A more direct test would involve comparing predicted and measured energies for sequences where cooperative effects are expected to be strong.
- **Why it matters** The claim about cooperativity affects the interpretation of the model and its applicability to more complex regulatory regions.
- **Resolution test** Perform a direct analysis comparing predicted and measured binding energies for a set of sequences designed to test cooperative effects, or acknowledge this as a limitation of the current analysis.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Introduction, Results
- **Evidence pointer** Location not provided
- **Issue** The manuscript assumes familiarity with ChIP-Seq analysis conventions and biophysical modeling terminology. Terms such as "energy matrix models," "effective binding energy," and "coverage normalization" are used without brief definitions.
- **Required correction** Add brief definitions or intuitive explanations when these terms are first introduced.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods (BoltzNet Training)
- **Evidence pointer** Location not provided
- **Issue** The description of the negative sampling strategy is incomplete. The text states 5000 randomly selected genomic regions are used, but does not specify whether these are excluded from enriched regions, how their length is matched, or whether they are sampled once or per epoch.
- **Required correction** Provide a complete description of the negative sampling procedure.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods (BoltzNet Architecture and Implementation)
- **Evidence pointer** Location not provided
- **Issue** The text states that the convolution layer uses a single 25 bp kernel, but does not specify the stride, padding, or how the kernel handles the 101 bp input across positions. The relationship between the kernel length and the reported "nucleotide resolution" predictions is not fully explained.
- **Required correction** Provide the full architecture details, including stride, padding, and how nucleotide-resolution scores are derived from the 25 bp kernel.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Interdisciplinary readership
- **Affected element** Results (Large-scale mapping of TF binding sites in E. coli)
- **Evidence pointer** Figure 1
- **Issue** The text states that enriched regions include "the vast majority of reported high-confidence binding sites in RegulonDB" but does not provide the fraction or a comparison to previously published ChIP-Seq datasets for the same TFs.
- **Required correction** Provide a quantitative comparison to RegulonDB and to any existing ChIP-Seq data for overlapping TFs.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Methods (BioLayer Interferometry)
- **Evidence pointer** Location not provided
- **Issue** The BLI analysis is described as fitting a 1:1 binding model, but the text does not state how many independent replicates were performed, how the fitting was validated, or how the reported R2 values were calculated (e.g., correlation of predicted vs. measured energies, or goodness of fit of the binding curves).
- **Required correction** Specify the number of replicates, the fitting procedure, and the exact definition of the reported R2.

- **Concern ID** R1-m6
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Discussion
- **Evidence pointer** Location not provided
- **Issue** The discussion of the "background affinity of the genome" is interesting but brief. The text does not discuss how this background affinity might vary with growth conditions, genomic context, or nucleoid-associated proteins.
- **Required correction** Expand the discussion to address these contextual factors or acknowledge them as limitations.

## Risk / unsupported claims
- The claim that 125 models are "high-confidence" is not fully supported without the supplementary tables and a clear description of the acceptance criteria and their justification.
- The claim that "cooperative interactions do not substantially impact occupancy" is not directly tested and is inferred from the accuracy of an additive model.
- The quantitative estimate that >79% of TF molecules are genome-bound is based on assumptions not fully described in the text and is generalized from 5 TFs to all 125.
- The claim of "nucleotide resolution" predictions is not fully supported by the architecture description, which uses a 25 bp kernel.
- The statement that BoltzNet "provides directly interpretable physical predictions" is only partially supported; the mapping from the neural network output to absolute binding energies (in kBT) is described, but the calibration procedure and its validation are not fully detailed.
- The generalizability of BoltzNet to other organisms or to TFs with different binding modes (e.g., requiring cofactors) is discussed only briefly and is not tested.

## Assessment against Nature-style criteria
- **Originality** High. The combination of a large standardized ChIP-Seq compendium with a biophysically interpretable neural network is novel. The explicit design of the network architecture to mirror a thermodynamic model is a creative and valuable contribution.
- **Scientific importance** Moderate to high. The dataset is a significant resource. The finding that weak binding sites are accurately modeled and physiologically relevant is conceptually important. The quantitative framework for predicting binding energy has practical applications. However, the broad conceptual advance over existing models of TF binding is incremental rather than transformative.
- **Interdisciplinary readership** Moderate. The work bridges genomics, biophysics, and machine learning. The biophysical modeling and the neural network design will interest researchers in all three areas. However, the presentation is likely to be most accessible to specialists in bacterial gene regulation.
- **Technical soundness** The core approach is sound, but the provided text does not contain sufficient detail to fully verify the claims. The training and validation procedures need more detail, and the metrics for model acceptance need clearer definition. The BLI validation, while a strength, shows a wide range of accuracy that needs explanation.
- **Readability for nonspecialists** The abstract and introduction are clear, but the results and methods sections assume significant background knowledge. The manuscript would benefit from brief explanations of key biophysical and computational concepts.

## Recommendation posture
Supportive if technical concerns are resolved. The dataset and the BoltzNet architecture are valuable contributions with clear potential. However, the current text does not provide enough quantitative detail to fully establish the accuracy, generalizability, and biological significance of the models. The authors should provide the supplementary data, clarify the validation metrics, and address the concerns about the genome-wide occupancy estimate and the cooperativity claim. Once these issues are resolved, this work would be of significant interest to the gene regulation and computational biology communities.