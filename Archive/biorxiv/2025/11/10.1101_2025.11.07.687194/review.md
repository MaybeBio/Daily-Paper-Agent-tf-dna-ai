## Review setup
- **Input scope** Full manuscript text (abstract, introduction, materials and methods, results, conclusions, data availability, acknowledgments, footnotes)
- **Assessment boundary** Scientific and technical evaluation of the manuscript as submitted to bioRxiv, based solely on the provided text
- **Shared manuscript claim summary** The authors introduce WaveDNA, a deep learning framework that encodes DNA sequences as two-dimensional wavelet transform images and classifies them using a ResNet50 CNN pretrained on ImageNet. They claim that WaveDNA achieves predictive accuracy comparable to state-of-the-art transformer-based models (DNABERT-2, Nucleotide Transformer) and outperforms HyenaDNA on TFBS prediction across 13 ENCODE ChIP-seq datasets, while using approximately fivefold fewer parameters and substantially less computational resources. They further claim that the image-based representation enables interpretability via Grad-CAM, with attribution maps significantly correlating with ChIP-seq signal.
- **Visible evidence base** Abstract; Introduction; Materials and Methods (encoding, classification, interpretability, validation datasets, benchmark models); Results (predictive performance, scalability, interpretability); Conclusions; Data Availability; Acknowledgments; Footnotes
- **Missing materials affecting confidence** Figures 1-4 are referenced but not provided; Supplementary Files (Sections 1-5, Figures 1-3, Tables 1-2) are referenced but not provided; no quantitative results (exact F1/MCC values per TF, p-values, confidence intervals) are given in the text; no hyperparameter details for baseline models; no dataset statistics (number of sequences per TF, sequence length distribution); no details on the scalar nucleotide mapping function (equation missing); no details on wavelet transform parameters (scales, frequencies); no code or reproducibility verification

## Reviewer

- **Overall assessment** The manuscript presents a conceptually interesting idea: leveraging wavelet transforms to convert DNA sequences into image-like representations, thereby enabling transfer learning from ImageNet-pretrained CNNs and access to computer vision interpretability tools. The motivation is clear and the potential for computational efficiency is plausible. However, the current manuscript, as provided, lacks the quantitative detail necessary to evaluate the central claims. The results section reports aggregate scores but no per-TF breakdown, no variance measures, and no statistical test details beyond a mention of Kolmogorov-Smirnov tests. The interpretability analysis is described qualitatively, with correlation values and p-values not reported. The methods section omits critical implementation details, including the nucleotide-to-scalar mapping and wavelet transform parameters. Without these, the claims of comparable performance, efficiency, and interpretability cannot be independently assessed. The manuscript is well-written and the narrative is coherent, but the evidence base is insufficient for the strength of the claims made.

- **Who would be interested in the results, and why** Computational biologists and bioinformaticians working on TFBS prediction, regulatory genomics, and deep learning applications to genomics would be the primary audience. Researchers interested in efficient model architectures, transfer learning from computer vision, and interpretable AI for biology would also find the approach relevant. The potential for reduced computational cost and improved interpretability compared to transformer-based models addresses practical concerns in the field.

- **Major strengths** The core idea of using wavelet transforms to bridge DNA sequence analysis and image-based deep learning is novel and creative. The approach has clear practical advantages: it avoids the need for large-scale genomic pretraining, leverages mature computer vision architectures and interpretability tools, and potentially offers substantial computational savings. The use of chromosome-stratified cross-validation and the filtering of negative sequences to exclude DHSs overlapping ChIP-seq peaks are methodologically sound choices. The comparison against three diverse baseline models (CNN-based HyenaDNA and transformer-based DNABERT-2, NT) is appropriate.

- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** "WaveDNA achieves predictive accuracy comparable to state-of-the-art DL models while using approximately fivefold fewer parameters and substantially less computational resources."
- **Evidence pointer** Results section, Figures 2A and 2B (not provided)
- **Concern** The central performance claim is supported only by aggregate macro-averaged F1 and MCC values (0.934 and 0.874 for WaveDNA; 0.962 and 0.924 for DNABERT-2; 0.879 and 0.751 for NT; 0.701 and 0.485 for HyenaDNA). No per-TF results, standard deviations, confidence intervals, or effect sizes are reported. The statistical comparison is mentioned as a Kolmogorov-Smirnov test, but no test statistics or exact p-values are given. Without these details, the claim of "comparable" performance cannot be rigorously evaluated, and the practical significance of a 0.03 F1 difference is unclear.
- **Why it matters** The primary contribution of the manuscript is the claim that a lightweight model can match transformer performance. This claim requires robust statistical evidence, including variance across datasets and per-TF breakdowns, to establish that the aggregate scores are not driven by a few favorable cases. The absence of this information prevents readers from assessing the reliability and generalizability of the findings.
- **Resolution test** Provide a supplementary table with per-TF F1 and MCC values for all models, including means, standard deviations, and 95% confidence intervals. Report exact p-values for the Kolmogorov-Smirnov tests and, ideally, additional paired statistical tests (e.g., Wilcoxon signed-rank) across the 13 datasets. If the claim is that performance is "comparable," consider reporting equivalence tests or effect sizes to quantify the magnitude of differences.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical completeness
- **Claim pointer** "WaveDNA applies the CWT using the Morlet wavelet as the mother function" and "each DNA sequence is first converted into a one-dimensional numerical signal by applying a scalar mapping function"
- **Evidence pointer** Materials and Methods, Section 2.1 (equations not provided)
- **Concern** The methods section omits critical implementation details. The nucleotide-to-scalar mapping function is referenced but the actual equation is missing. The wavelet transform parameters (e.g., range of scales, number of scales, sampling frequency) are not specified. The process by which the 2D wavelet coefficient matrix is converted into a fixed 224x224 image for ResNet50 input is not described. These details are essential for reproducibility and for understanding the information loss or compression that occurs during encoding.
- **Why it matters** The novelty of the approach lies in the wavelet-based encoding. Without precise specification of the mapping and transform parameters, other researchers cannot replicate the method, and reviewers cannot assess whether the encoding preserves biologically relevant sequence information. The fixed image size also raises questions about how variable-length sequences are handled, which is not addressed.
- **Resolution test** Provide the complete mathematical formulation of the nucleotide-to-scalar mapping, the wavelet transform parameters (mother wavelet, scale range, number of scales), and the procedure for resizing or cropping the wavelet coefficient matrix to 224x224. Describe how sequence length variability is handled and whether any information is lost in the resizing process.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Interpretability validation
- **Claim pointer** "The results revealed statistically significant positive correlations (maximum p < 0.05) in all datasets), demonstrating that WaveDNA's activation patterns align with experimentally measured TF binding signals."
- **Evidence pointer** Results section, Figure 4 (not provided)
- **Concern** The interpretability analysis is described only qualitatively. No correlation coefficients, p-values, or sample sizes are reported. The statement "maximum p < 0.05" is ambiguous and appears to contain a typographical error. The choice of the layer with "highest activation variance" is not justified, and it is unclear whether this selection was made post hoc, which could introduce bias. The comparison with ChIP-seq signal is meaningful, but the analysis lacks a null model or permutation test to establish that the observed correlations are specific to the model's learned features rather than a trivial property of the input representation.
- **Why it matters** Interpretability is a key claimed advantage of WaveDNA over transformer models. To substantiate this claim, the authors must demonstrate that the Grad-CAM attributions are not only statistically correlated with ChIP-seq signal but also that this correlation is specific to the model's learned representations and not an artifact of the wavelet encoding or the attribution method. The current description does not allow such an assessment.
- **Resolution test** Report the full distribution of correlation coefficients per TF, including means, standard deviations, and exact p-values. Clarify the layer selection procedure and whether it was determined a priori. Include a permutation test or comparison with attributions from a randomly initialized model to establish specificity. Provide representative examples of Grad-CAM maps alongside ChIP-seq signal profiles.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Baseline fairness
- **Claim pointer** "WaveDNA was initialized with ResNet50 weights pretrained on ImageNet" and "DNABERT-2 and NT were fine-tuned using the same optimization scheme adopted for WaveDNA."
- **Evidence pointer** Materials and Methods, Section 2.4; Results, Section 3.1
- **Concern** The comparison may not be entirely fair. WaveDNA benefits from ImageNet pretraining, which provides a strong inductive bias for image feature extraction, while DNABERT-2 and NT are initialized from genomic pretraining. The authors state that DNABERT-2 and NT were fine-tuned with the same optimization scheme, but the batch size differs (32 for DNABERT-2, 4 for WaveDNA and NT), and it is unclear whether hyperparameter tuning was performed for each model. The choice of three epochs for all models may disadvantage the transformer models, which typically require more epochs to converge. The authors do not report whether learning rates or other hyperparameters were optimized for each baseline.
- **Why it matters** The claim of "comparable performance with fewer parameters" is only meaningful if the baselines are given a fair chance to perform well. If the transformer models are undertrained or poorly tuned, the comparison is biased in favor of WaveDNA. The practical recommendation to use WaveDNA over transformers depends on a fair and rigorous comparison.
- **Resolution test** Report the hyperparameter search procedure for each model, including the range of learning rates, batch sizes, and epochs considered. Justify the choice of three epochs for all models, or show that longer training does not significantly improve baseline performance. Consider reporting results with multiple random seeds to assess variance.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Generalizability
- **Claim pointer** "The selected TFs span a range of DNA-binding domains, motif lengths, information content, and sequence variability, ensuring a comprehensive evaluation represented across distinct binding preferences and regulatory context."
- **Evidence pointer** Materials and Methods, Section 2.4; Results, Section 3.1
- **Concern** The manuscript claims generalizability based on 13 TFs, but no details are provided on the diversity of these TFs in terms of binding domain families, motif complexity, or chromatin context. The selection criteria for the 13 TFs are not described. It is unclear whether the dataset includes TFs with weak or diffuse binding patterns, which would test the model's ability to capture subtle signals. The claim of "comprehensive evaluation" is not supported by the evidence presented.
- **Why it matters** The utility of WaveDNA as a general-purpose tool for TFBS prediction depends on its performance across a wide range of TF binding characteristics. If the 13 TFs are biased toward strong, well-defined motifs, the results may not generalize to more challenging cases. The authors should demonstrate that their TF selection is representative and that the model performs well across diverse binding scenarios.
- **Resolution test** Provide a table listing the 13 TFs with their binding domain families, motif lengths, information content, and the number of positive and negative sequences per TF. Justify the selection criteria. If possible, include TFs with diverse binding characteristics, such as pioneer factors or TFs with weak motifs, to strengthen the generalizability claim.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, Results
- **Evidence pointer** Abstract, Results Section 3.1
- **Issue** The abstract states "approximately fivefold fewer parameters" but the Results section reports "approximately 25 million parameters for WaveDNA, 117 million for DNABERT-2, 500 million for NT, and 6.5 million for HyenaDNA." The fivefold claim is relative to DNABERT-2 (117/25 = 4.68), but relative to NT (500/25 = 20) the reduction is much larger. The claim should be clarified to specify the reference model.
- **Required correction** Specify the reference model for the parameter reduction claim, e.g., "approximately fivefold fewer parameters than DNABERT-2" or report the range of reductions across all baselines.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results Section 3.1
- **Evidence pointer** Results Section 3.1
- **Issue** The text states "we conducted two-sample Kolmogorov-Smirnov tests to the distributions of F1 and MCC scores" but does not report the test statistics or p-values. The statement "p < 0.05" and "p > 0.1" is mentioned but without exact values.
- **Required correction** Report exact p-values for all statistical tests, or include them in a supplementary table.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Materials and Methods, Section 2.4
- **Evidence pointer** Materials and Methods, Section 2.4
- **Issue** The manuscript states that all models were trained on "identical training and test dataset splits" but does not describe how the splits were generated (e.g., random seed, chromosome assignment). The chromosome-stratified cross-validation strategy is mentioned but not detailed.
- **Required correction** Describe the cross-validation procedure in detail, including the number of folds, the specific chromosomes used for testing, and the random seed used for any random processes.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Results Section 3.2
- **Evidence pointer** Results Section 3.2
- **Issue** The scalability analysis reports runtime and memory usage but does not specify the hardware configuration beyond "a single NVIDIA GeForce RTX 4090 GPU." The software environment (e.g., PyTorch version, CUDA version) is not mentioned.
- **Required correction** Report the full hardware and software environment, including GPU, CPU, RAM, and software versions, to ensure reproducibility of the scalability measurements.

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Interpretability
- **Affected element** Results Section 3.3
- **Evidence pointer** Results Section 3.3
- **Issue** The interpretability analysis is described as comparing Grad-CAM activations with ChIP-seq signal, but the method for extracting the ChIP-seq signal at the specific genomic coordinates of the test sequences is not described. It is unclear whether the signal was averaged over the entire sequence or at specific positions.
- **Required correction** Describe the procedure for extracting ChIP-seq signal for each test sequence, including the genomic coordinate mapping and any normalization steps.

- **Technical failings that need to be addressed before the case is established** R1-M1 (missing per-TF results and statistical details), R1-M2 (incomplete method specification for the wavelet encoding), R1-M3 (inadequate reporting of interpretability validation), R1-M4 (potential baseline unfairness), R1-M5 (insufficient evidence for generalizability)

- **Assessment against Nature-style criteria** 
  - Originality: The idea of using wavelet transforms to convert DNA sequences into images for transfer learning from computer vision is genuinely novel and creative. This is a fresh perspective in a field dominated by one-hot encoding and transformer architectures.
  - Scientific importance: If the claims are substantiated, the work could have practical significance by offering a more efficient and interpretable alternative to large transformer models. However, the importance is incremental rather than transformative, as it applies existing techniques (wavelets, transfer learning, Grad-CAM) in a new domain.
  - Interdisciplinary readership: The work bridges signal processing, computer vision, and genomics, which could appeal to a broad audience. However, the current presentation assumes familiarity with deep learning terminology and may not be accessible to all biologists.
  - Technical soundness: The conceptual framework is sound, but the manuscript as provided lacks the quantitative and methodological detail necessary to verify the technical claims. The missing equations, parameters, and statistical reporting are significant gaps.
  - Readability for nonspecialists: The writing is clear and the narrative is well-structured. However, the methods section is dense and assumes prior knowledge of wavelet transforms and deep learning architectures. A brief intuitive explanation of CWT for a general audience would improve accessibility.

- **Recommendation posture** Supportive if technical concerns are resolved. The core idea is promising and the potential benefits are clear, but the current manuscript does not provide sufficient evidence to establish the central claims. The authors must supply the missing methodological details, per-TF results, and statistical analyses to allow a rigorous evaluation. Once these are provided, the manuscript could be suitable for publication in a specialized computational biology venue, though the incremental nature of the contribution may limit its appeal for a general audience.