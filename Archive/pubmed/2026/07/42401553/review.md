## Review setup
- **Input scope** Full manuscript text (abstract, introduction, results, discussion, methods) without figures, tables, or supplementary materials
- **Assessment boundary** Scientific validity, technical soundness, and significance of the claims as presented in the text; no assessment of figures or supplementary data possible
- **Shared manuscript claim summary** The authors introduce PISA (pairwise influence by sequence attribution), a method for interpreting sequence-to-function deep learning models at single-base resolution. They apply PISA to ChIP-nexus, ATAC-seq, and MNase-seq data, revealing positional effects of TF motifs, detecting motifs with mixed positive and negative contributions, identifying experimental biases, and enabling bias-corrected nucleosome prediction models. They further use these models to discover nucleosome-positioning motifs, identify chromatin domain boundaries, and design sequences with altered nucleosome positioning validated experimentally.
- **Visible evidence base** Abstract, introduction, results, discussion, and methods sections; no figures, tables, or supplementary materials provided
- **Missing materials affecting confidence** All figures and figure legends, all supplementary figures and tables, Supplementary Data 1, Supplementary Video 1, model performance metrics referenced as Supplementary Tables 1-6, and the code repository contents

## Reviewer
- **Overall assessment** This manuscript presents a conceptually valuable extension of attribution methods for sequence-to-function models, with a particularly clever approach to separating enzymatic bias from biological signal in MNase-seq data. The PISA framework addresses a genuine limitation of existing interpretation tools by providing positional, rather than aggregate, attribution. However, the current text does not provide sufficient quantitative evidence to fully evaluate the claims. Key performance metrics, validation statistics, and comparative analyses are all relegated to supplementary materials that were not available for review. The experimental validation of designed sequences is described but not shown. The barrier identification method is intriguing but its biological validation appears indirect. The manuscript would benefit from clearer articulation of the novelty relative to existing attribution approaches and from more rigorous statistical framing of the barrier detection method.
- **Who would be interested in the results, and why** Researchers developing and applying interpretable deep learning methods in genomics, particularly those working on regulatory genomics, chromatin biology, and nucleosome positioning. The bias-correction approach for MNase-seq will interest experimentalists using nucleosome mapping assays. The barrier identification method may interest chromatin structure researchers. The software package BPReveal will be useful to the broader community applying BPNet-style models.
- **Major strengths** The PISA concept directly addresses a known limitation of attribution methods by providing positional resolution. The synthetic bias track approach for MNase-seq is conceptually elegant and leverages the additive property of Shapley values in a non-obvious way. The application to multiple data types (ChIP-nexus, ATAC-seq, MNase-seq) demonstrates versatility. The experimental validation of designed sequences, while not shown in the provided text, represents a strong commitment to testing predictions. The identification of barriers through systematic motif perturbation is a creative use of model interpretation.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The claim that PISA can detect experimental biases and enable bias-corrected MNase-seq models relies on the assumption that subtracting PISA values between the 5' and 3' end models isolates enzymatic bias. The authors acknowledge this assumption may fail for partial nucleosomes but state that "isolating regions with uniform nucleosome size does not affect bias model performance" (Supplementary Fig. 7).
  - **Evidence pointer** Methods section "Synthetic bias calculation"; Supplementary Fig. 7
  - **Concern** The validation of the bias subtraction method is not visible in the provided materials. The claim that partial nucleosomes do not affect performance is critical to the method's validity, but the supporting evidence is only in supplementary materials. Moreover, the assumption that a base affecting one end of a nucleosome but not the other is purely bias-related may not hold for sequences that influence nucleosome positioning in an asymmetric manner. The authors should provide a more rigorous theoretical justification or additional empirical validation that the subtraction isolates bias rather than discarding legitimate asymmetric biological signals.
  - **Why it matters** The bias-correction method is a central contribution of the paper. If the subtraction method inadvertently removes or distorts biological signal, all downstream analyses using the bias-corrected model would be compromised.
  - **Resolution test** Provide the supplementary figure showing that uniform nucleosome size does not affect performance, and add a simulation or control experiment demonstrating that known asymmetric biological signals are preserved after bias subtraction.

  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The barrier identification method claims to identify chromatin domain boundaries by detecting transitions in lean values from positive to negative. The authors state that "more than half of them within <100 bp distance" of Micro-C-derived boundaries.
  - **Evidence pointer** Results section "Barrier elements limit the effects of nucleosome-positioning motifs"; Supplementary Fig. 11
  - **Concern** The statistical significance of the overlap between identified barriers and Micro-C boundaries is not reported in the text. A 50% overlap within 100 bp could be meaningful or could reflect chance, depending on the genomic density of barriers and boundaries. The method for combining results from four different motifs into a single barrier set is not described. The threshold for calling a barrier (at least 7 out of 8 tests) appears arbitrary and its sensitivity and specificity are not characterized.
  - **Why it matters** The barrier identification is presented as a major biological finding. Without proper statistical validation, the claim that these barriers correspond to real chromatin domain boundaries is not established.
  - **Resolution test** Provide a null model or permutation test showing that the overlap with Micro-C boundaries is significantly greater than expected by chance. Describe how results from different motifs are combined and justify the threshold choice.

  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The authors claim that their bias-corrected MNase-seq model achieves "unprecedented" nucleosome prediction and enables de novo discovery of nucleosome-positioning motifs.
  - **Evidence pointer** Results section "PISA visualizes how de novo discovered motifs affect nucleosomes"; Supplementary Tables 3-4
  - **Concern** The performance comparison with prior models is not presented in the text. The claim of "unprecedented" performance requires quantitative comparison with existing nucleosome prediction models, not just with the Routhier et al. model. The text mentions that the model achieves higher accuracy than Routhier et al. but does not provide the actual numbers or describe the evaluation metrics.
  - **Why it matters** The central value proposition of the bias-correction approach is that it enables better nucleosome prediction. Without a clear demonstration of improvement over the state of the art, this claim is unsupported.
  - **Resolution test** Provide the performance comparison table in the main text, including multiple baseline models and multiple evaluation metrics.

  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Scientific importance
  - **Claim pointer** The authors claim that PISA "reveals the basis of Micro-C chromatin domain boundaries through systematic motif perturbations" and that barriers are "composed of nucleosome-positioning motifs."
  - **Evidence pointer** Results section "Barrier elements limit the effects of nucleosome-positioning motifs"; Fig. 6
  - **Concern** The causal relationship between the identified barriers and chromatin domain boundaries is not established. The authors show correlation between barrier positions and Micro-C boundaries, and enrichment of specific motifs at barriers, but do not demonstrate that these motifs cause the boundaries. The claim that polyA motifs can form domain boundaries "through a mechanism that is not understood" is speculative.
  - **Why it matters** The biological interpretation of the barrier findings is a significant part of the paper's impact. Overstating the causal relationship could mislead readers.
  - **Resolution test** Provide experimental evidence that disrupting the identified motifs at barrier positions affects chromatin domain boundaries, or soften the causal language.

- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Model training details
  - **Evidence pointer** Methods section "Data"
  - **Issue** The text states that model parameters were maintained "to the extent possible" from previous studies but does not specify which parameters were changed or why.
  - **Required correction** Provide a table of hyperparameters for each model trained, including any deviations from prior work.

  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Definition of PISA
  - **Evidence pointer** Results section "PISA reveals pairwise relationships between the input sequence and the output profile"
  - **Issue** The formal definition of PISA values is not provided in the main text. The notation is introduced but the computational procedure is only described in the methods.
  - **Required correction** Include a brief formal definition or pseudocode in the main text to make the method accessible to readers.

  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Motif discovery
  - **Evidence pointer** Results section "PISA visualizes how de novo discovered motifs affect nucleosomes"
  - **Issue** The text states that motifs were discovered using TF-MoDISco but does not describe the significance thresholds or false discovery rate control.
  - **Required correction** Describe the motif discovery parameters and any multiple testing corrections applied.

  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Genetic algorithm
  - **Evidence pointer** Methods section "Genetic algorithm"
  - **Issue** The genetic algorithm parameters (population size, number of generations, mutation rate, etc.) are not specified.
  - **Required correction** Provide the full parameter set for the genetic algorithm.

  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure references
  - **Evidence pointer** Throughout results
  - **Issue** The text frequently references figures and supplementary figures, but the figures were not provided for review. This makes it impossible to verify the described patterns.
  - **Required correction** Ensure that all key claims are supported by quantitative values in the text, not only by visual patterns in figures.

  - **Concern ID** R1-m6
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Comparison with existing methods
  - **Evidence pointer** Discussion
  - **Issue** The discussion mentions limitations of existing attribution methods but does not quantitatively compare PISA with these methods on the same datasets.
  - **Required correction** Add a comparison with at least one existing attribution method to demonstrate the advantages of PISA.

- **Technical failings that need to be addressed before the case is established** R1-M1 (bias subtraction validity), R1-M2 (statistical validation of barriers), R1-M3 (performance comparison with state of the art)

## Risk / unsupported claims
- The claim of "unprecedented nucleosome prediction models" is unsupported without quantitative comparison with existing methods.
- The claim that barriers identified through lean value transitions correspond to chromatin domain boundaries is not statistically validated.
- The claim that polyA motifs can form chromatin domain boundaries is speculative and not directly tested.
- The claim that PISA can detect experimental biases is plausible but the validation is not visible in the provided materials.
- The claim that the bias-corrected model enables de novo discovery of nucleosome-positioning motifs is not quantitatively evaluated in the text.
- The experimental validation of designed sequences is described but the results are not shown in the provided text.
- The performance comparison with the Routhier et al. model is mentioned but the actual metrics are not provided.
- The claim that PISA reveals "the basis" of Micro-C chromatin domain boundaries overstates the correlational evidence presented.