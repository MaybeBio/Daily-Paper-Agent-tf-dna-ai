## Review setup
- **Input scope** Full manuscript text
- **Assessment boundary** Scientific claims, methodology, and conclusions as presented in the provided manuscript text
- **Shared manuscript claim summary** The authors present Camformer, a residual convolutional neural network that ranked fourth in the Random Promoter DREAM Challenge 2022, trained on 6.7 million yeast promoter sequences. They report accurate prediction of gene expression (r²=0.914±0.003, ρ=0.962±0.002), systematic evaluation of 270 alternative model configurations, and use of explainability techniques (Grad-CAM and in silico mutagenesis) to uncover cis-regulatory logic, including a specific interaction between IME1 and UME6 motifs.
- **Visible evidence base** Main text including Methods sections 2.1-2.3, Algorithm sections 3.1-3.3, Results sections 4.1-4.4, Discussion, and references to supplementary figures (Fig. S2-S13) and supplementary methods (Methods 1.1-1.5)
- **Missing materials affecting confidence** Supplementary figures and methods referenced but not provided; detailed model architecture hyperparameters not fully specified in main text; statistical test details for some comparisons not fully described; code repository not reviewed

## Reviewer
- **Overall assessment** This manuscript presents a solid, well-executed computational study that provides a thorough analysis of a competitive deep learning model for gene expression prediction. The systematic grid search over 270 model configurations is a valuable contribution, and the use of explainability methods to extract biological insights is commendable. However, the biological novelty of the cis-regulatory findings is modest, and several technical details require clarification to fully assess the robustness of the claims. The manuscript is clearly written and would interest researchers in regulatory genomics and deep learning applications.
- **Who would be interested in the results, and why** Researchers developing deep learning methods for regulatory genomics would benefit from the systematic model comparison and design insights. Computational biologists studying yeast cis-regulation would find the motif interaction analysis useful. The benchmarking against DREAM challenge results provides a reference point for the field. The demonstration that a well-designed CNN can match or exceed transformer-based approaches is relevant to the broader machine learning for genomics community.
- **Major strengths** 1) Systematic and rigorous evaluation of model design choices through a large grid search (270 models), providing practical guidance for model development. 2) Demonstration of robust performance through multiple re-training runs with different seeds, with clear reporting of variance. 3) Use of complementary explainability methods (Grad-CAM and ISM) with concordant results, strengthening the biological interpretation. 4) Fair comparison to baselines using normalized improvement metrics, acknowledging the ceiling effects in different sequence categories. 5) Clear writing and good organization, with methods sufficiently detailed for reproduction.
- **Major Concerns** 
- **Minor Comments** 
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3
- **Assessment against Nature-style criteria** Originality: Moderate. The model architecture is not fundamentally novel, but the systematic analysis of design choices and the application to a DREAM challenge dataset provide some originality. Scientific importance: Moderate. The work provides useful practical insights for model development and demonstrates the utility of explainability for extracting regulatory logic, but the biological findings are largely confirmatory of known interactions. Interdisciplinary readership: Limited. The manuscript is primarily of interest to computational biologists and machine learning researchers working on genomics, with limited broader appeal. Technical soundness: Generally strong, with rigorous evaluation protocols and appropriate statistical tests, though some details require clarification. Readability for nonspecialists: Good. The manuscript is clearly written with appropriate context, though some sections assume familiarity with deep learning concepts.
- **Recommendation posture** Supportive if technical concerns are resolved

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** The claim that "Camformer accurately decodes the association between promoters and gene expression (r²=0.914±0.003, ρ=0.962±0.002) and provides a substantial improvement over previous state of the art" (Abstract and Section 4.1)
- **Evidence pointer** Section 4.1, Fig. 3A-C, Fig. S2
- **Concern** The performance comparison to "previous state of the art" is not clearly defined. The authors compare to the Vaishnav et al. (2022) benchmark model, but it is unclear whether this comparison is made on identical train/test splits and evaluation protocols. Additionally, the comparison to LegNet (ranked first in the DREAM challenge) is mentioned only for the YPD/SD-Ura datasets, not for the main DREAM challenge test set. The claim of "substantial improvement" requires a more rigorous and clearly described baseline comparison.
- **Why it matters** The central claim of the manuscript is that Camformer provides state-of-the-art performance. Without a clear and fair comparison protocol, this claim cannot be properly evaluated, and the contribution of the work is diminished.
- **Resolution test** Provide a detailed description of the evaluation protocol used for all baseline comparisons, including train/test splits, hyperparameter selection, and any data preprocessing differences. Report performance of all models on the same test sets with identical evaluation metrics. If possible, include a direct comparison to LegNet on the DREAM challenge test set.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Reproducibility
- **Claim pointer** The claim that the model and analysis are fully reproducible, as implied by the availability statement: "Data and code are available at: https://github.com/Bornelov-lab/Camformer" (Availability section)
- **Evidence pointer** Section 3.1, Section 3.2, Methods 1.1-1.3 (supplementary)
- **Concern** The main text does not provide sufficient detail on the model architecture, hyperparameter search space, or training procedures to allow independent reproduction. Key details such as the exact number of filters per layer, kernel sizes, pooling strategies, dropout rates, and learning rate schedules are not specified in the main text and are deferred to supplementary methods. The grid search description is incomplete, and the criteria for selecting the "best" model configuration are not clearly stated.
- **Why it matters** Reproducibility is a core requirement for computational studies. Without complete architectural and training details, other researchers cannot build upon this work or verify the claims independently.
- **Resolution test** Provide a complete specification of the model architecture and training procedure in the main text or a clearly accessible supplementary file. Include the full hyperparameter search space, selection criteria, and the final chosen configuration. Ensure the code repository contains all necessary scripts and configuration files to reproduce the reported results.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Statistical rigor
- **Claim pointer** The claim that "an IME1 motif on its own increases gene expression, a co-occurring UME6 motif instead strongly reduces gene expression" (Abstract and Section 4.4)
- **Evidence pointer** Section 4.4, Fig. 6G-H
- **Concern** The statistical evidence supporting the IME1-UME6 interaction claim is not fully described. The manuscript states that the model "consistently associated the presence of both motifs with a strong reduction in gene expression," but the statistical test used to establish this consistency is not specified. It is unclear whether this is based on a formal test of interaction effects, a comparison of ISM scores across motif combinations, or a descriptive observation. The number of sequences containing both motifs (n=386) is reported, but the distribution of ISM scores and the variability across sequences are not shown.
- **Why it matters** The IME1-UME6 interaction is presented as a key biological finding demonstrating the utility of the model for uncovering cis-regulatory logic. Without proper statistical support, this claim is not established, and the biological significance of the work is weakened.
- **Resolution test** Provide a clear description of the statistical analysis used to support the interaction claim, including the specific test, effect size, confidence intervals, and a measure of variability. Show the distribution of ISM scores for the relevant motif combinations and report the number of sequences in each group. If a formal interaction test is used, describe the model and how it was fit.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Section 2.2, Prediction task
- **Evidence pointer** Section 2.2
- **Issue** The prediction task is described in a single sentence: "Our study explores how to define f using a CNN (Fig. 1C)." This is insufficiently detailed. The input and output of the model, the target variable, and the evaluation metric should be clearly stated.
- **Required correction** Expand Section 2.2 to clearly define the prediction task, including the input representation, the output variable, and the loss function used for evaluation.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.1.2, Improvements on previously challenging sequences
- **Evidence pointer** Section 4.1.2, Fig. 4A-B
- **Issue** The definition of "challenging sequences" is not provided. The manuscript mentions that the test set includes sequences with different properties, but it is unclear what makes a sequence "challenging" and how this category was defined.
- **Required correction** Define the "challenging sequences" category and explain how it was constructed. If this is a standard category from the DREAM challenge, provide a reference or description.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Interpretation
- **Affected element** Section 4.3.1, Grad-CAM highlights potential regulatory hierarchy
- **Evidence pointer** Section 4.3.1, Fig. S10
- **Issue** The interpretation of the Grad-CAM results as evidence of a "hierarchy" is speculative. The observation that deeper layers capture upstream motifs could be an artifact of the model architecture rather than a biological hierarchy. The manuscript does not discuss alternative interpretations.
- **Required correction** Acknowledge alternative interpretations of the layer-wise Grad-CAM results and discuss why the hierarchy interpretation is preferred, or soften the claim.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Section 4.1, Ensemble results
- **Evidence pointer** Section 4.1, Fig. 3B-C
- **Issue** The improvement from ensembling is reported as significant (P=.001), but the number of seeds used for the ensemble and the method for combining predictions are not fully described. The text mentions "averaging predictions from several seeds" but does not specify how many seeds were used for the two-seed comparison.
- **Required correction** Specify the number of seeds used for each ensemble comparison and describe the ensembling method in detail.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Section 4.4, Motif analysis
- **Evidence pointer** Section 4.4, Fig. 6A
- **Issue** The SEA enrichment analysis is mentioned but not described. The method for identifying overrepresented motifs in high- and low-expressed sequences is not explained, and the reference for the SEA method is not provided.
- **Required correction** Describe the SEA enrichment analysis method and provide a reference. Specify the motif database used and the significance threshold.

## Risk / unsupported claims
- The claim of "substantial improvement over previous state of the art" is not fully supported without a clearly described and fair comparison protocol.
- The IME1-UME6 interaction claim lacks sufficient statistical detail to be fully evaluated.
- The claim that the model "captures and can be used to study cis-regulatory logic" is supported by descriptive analyses but would benefit from validation against independent experimental data.
- The performance on YPD and SD-Ura datasets is reported as "similar to LegNet," but the comparison is not quantified or statistically tested.
- The claim that "all our best-performing models were CNNs" is based on the DREAM challenge results but the comparison to transformer models is not systematically presented.
- The biological interpretation of the Grad-CAM layer-wise analysis as evidence of "hierarchy" is not fully supported and should be treated as speculative.