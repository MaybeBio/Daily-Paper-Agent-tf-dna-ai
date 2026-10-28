## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, methods, and supplementary figure/table references.
- **Assessment boundary** Scientific validity, methodological soundness, reproducibility, and significance of the claims presented. No assessment of editorial fit or formatting.
- **Shared manuscript claim summary** The authors propose Hi-C-LSTM, a recurrent neural network model that learns low-dimensional latent representations of intra-chromosomal Hi-C contacts. They claim these representations (1) reconstruct Hi-C maps with high accuracy, outperforming existing methods; (2) capture functional genomic elements and conformation-related transcription factors; (3) enable in-silico perturbation experiments, including duplication and knockout simulations, validated against experimental data.
- **Visible evidence base** Main text figures 1–7, supplementary figures 1–16, supplementary tables 1–3, methods section, and data availability statements.
- **Missing materials affecting confidence** Supplementary figures and tables referenced in the text were not provided in the submitted material. Specific numerical results for classification metrics (e.g., mAP values) and statistical significance tests are not fully reported in the main text. Code repository is referenced but not accessible for review.

## Reviewer
- **Overall assessment** The manuscript presents a novel application of recurrent neural networks to learn interpretable representations of chromatin contacts. The methodological contribution is clear and the in-silico perturbation experiments are a valuable addition to the field. However, several technical aspects require clarification and additional validation to fully support the claims, particularly regarding the comparison with existing methods, the interpretation of feature attribution results, and the generalizability of the approach.
- **Who would be interested in the results, and why** Researchers in computational genomics, chromatin biology, and 3D genome organization. The method offers a new tool for analyzing Hi-C data, identifying regulatory elements, and predicting the effects of genomic variants on chromatin structure, which is relevant for understanding gene regulation and disease mechanisms.
- **Major strengths**
  - Novel use of LSTM for representation learning of Hi-C data, addressing the sequential nature of the genome.
  - Comprehensive evaluation across multiple downstream tasks (classification, feature attribution, perturbation).
  - Demonstration of practical utility through in-silico perturbation experiments validated against experimental data.
  - Clear and detailed methods section, facilitating reproducibility.
- **Major Concerns**
  - **R1-M1** (Major, Blocking: No): The comparison with existing methods (SNIPER, SCI) may be unfair or incomplete. The authors adapt SNIPER to their task (SNIPER-FC) but do not clearly describe the adaptation process or whether the hyperparameters were optimized for each method. Additionally, the comparison is limited to reconstruction accuracy; a more thorough comparison on downstream tasks (e.g., classification) would strengthen the claims.
  - **R1-M2** (Major, Blocking: No): The feature attribution analysis (Integrated Gradients) is used to identify genomic elements driving conformation. However, the validation of these attributions is largely qualitative (visual inspection of tracks). A quantitative assessment, such as comparing attribution scores to known functional elements with statistical tests, would provide stronger evidence.
  - **R1-M3** (Major, Blocking: No): The in-silico perturbation experiments, while promising, are limited to a few loci. The manuscript would benefit from a more systematic evaluation across multiple loci and cell types to demonstrate the generalizability of the approach. The authors acknowledge this limitation but do not provide a clear path forward.
  - **R1-M4** (Major, Blocking: No): The manuscript does not report confidence intervals or statistical significance for the key quantitative results (e.g., R-squared values, mAP scores). This makes it difficult to assess the robustness of the findings.
- **Minor Comments**
  - **R1-m1** (Minor, Axis: Clarity): The abstract states "affect" instead of "effect" in the first sentence. Please correct this typo.
  - **R1-m2** (Minor, Axis: Reproducibility): The methods section mentions a GitHub repository, but the specific version or commit hash is not provided. Please include this for reproducibility.
  - **R1-m3** (Minor, Axis: Clarity): The description of the "frame" concept in Figure 2 and the methods section is somewhat unclear. A more explicit definition of frame boundaries and their role in the model would be helpful.
  - **R1-m4** (Minor, Axis: Completeness): The manuscript mentions "Supplementary Table 1" for p-values but does not describe the statistical test used. Please specify the test and the correction for multiple comparisons.
- **Technical failings that need to be addressed before the case is established**
  - R1-M1, R1-M2, R1-M3, R1-M4.
- **Assessment against Nature-style criteria**
  - **Originality**: High. The application of LSTM to Hi-C representation learning is novel and distinct from existing approaches.
  - **Scientific importance**: Moderate to high. The method addresses a key challenge in linking 1D genome to 3D conformation and has potential applications in variant interpretation.
  - **Interdisciplinary readership**: Moderate. The work will appeal to computational biologists and genomics researchers, but may be less accessible to a broader audience.
  - **Technical soundness**: Moderate. The core methodology is sound, but the evaluation and validation have gaps that need to be addressed.
  - **Readability for nonspecialists**: Moderate. The manuscript is generally well-written, but some technical details (e.g., LSTM architecture, Integrated Gradients) may be challenging for nonspecialists.
- **Recommendation posture** Supportive if technical concerns are resolved. The manuscript presents a promising method with clear potential, but the current evidence is insufficient to fully support all claims.

## Risk / unsupported claims
- The claim that Hi-C-LSTM "outperforms existing methods" is not fully supported due to potential biases in the comparison and lack of statistical testing.
- The claim that feature attribution identifies "genomic drivers of conformation" is not quantitatively validated.
- The generalizability of in-silico perturbation results to other loci and cell types is not established.
- The performance of Hi-C-LSTM on low-coverage or sparse Hi-C data is not evaluated, limiting the scope of the claims.