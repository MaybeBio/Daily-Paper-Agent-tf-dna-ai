## Review setup
- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussions, conclusion) as provided.
- **Assessment boundary** Scientific and technical evaluation of the proposed method, experimental design, results, and claims as presented in the provided text. No external data or code were accessed.
- **Shared manuscript claim summary** The authors propose Gen-DNA-TCN, an autoregressive generative model for designing functional yeast promoter sequences. The model is initialized with parameters from a pre-trained predictive model (Pre-DNA-TCN) and fine-tuned on real promoter sequences. The authors claim that Gen-DNA-TCN generates diverse, unique, and functional synthetic promoters with expression profiles and transcription factor binding site distributions similar to real sequences, while achieving high computational efficiency.
- **Visible evidence base** Abstract, Introduction, Methods (Sections 2.1–2.4), Results (Sections 3.1–3.4), Discussions (Sections 4.1–4.2), Conclusion, and references to Figures 1–11 and Tables 1–4. No figures, tables, or supplementary materials were actually provided in the submitted text.
- **Missing materials affecting confidence** All figures, tables, and supplementary data referenced in the text are absent. No code, model weights, or detailed hyperparameter settings are provided. No wet-lab validation data are included. The exact training/validation split and data preprocessing steps are described but not fully reproducible without the original datasets.

## Reviewer
- **Overall assessment** The manuscript presents a potentially useful approach to synthetic promoter design by leveraging a pre-trained predictive model to initialize a generative autoregressive model. The idea of transferring knowledge from a high-accuracy predictor to a generator is conceptually sound and could be of interest to the synthetic biology and computational genomics communities. However, the current manuscript has significant limitations in evidence presentation and methodological clarity. The absence of all figures and tables makes it impossible to verify the reported results. Several claims, particularly regarding "functionality" and "similarity" of generated sequences, are not supported by direct experimental validation. The comparison with existing methods is qualitative and lacks quantitative benchmarks. The manuscript would benefit from clearer statistical reporting, inclusion of baseline comparisons, and a more rigorous demonstration of biological relevance.
- **Who would be interested in the results, and why** Researchers in synthetic biology, promoter engineering, and computational genomics would be interested. The method addresses a practical need for designing functional promoters with desired expression characteristics. The use of a pre-trained predictor to guide generative modeling is a transferable concept that could inspire similar approaches in other sequence design tasks. The reported computational efficiency is also attractive for large-scale design efforts.
- **Major strengths** 1) The conceptual framework of using a pre-trained predictive model to initialize a generative model is novel and potentially impactful. 2) The method is computationally efficient compared to GAN-based approaches, as claimed. 3) The evaluation considers multiple aspects: expression distribution, transcription factor binding site distribution, and sequence diversity. 4) The use of a community benchmark (Random Promoter DREAM Challenge) provides a solid foundation for the predictive model.
- **Major Concerns** 
  - R1-M1: Lack of wet-lab validation for "functionality" claim.
  - R1-M2: Absence of all figures and tables, making results unverifiable.
  - R1-M3: Insufficient comparison with existing generative methods.
  - R1-M4: Ambiguity in the generative process and model architecture details.
  - R1-M5: Statistical significance of reported correlations not established.
- **Minor Comments** 
  - R1-m1: Typographical error "JASPER" should be "JASPAR".
  - R1-m2: Inconsistent terminology for "starting nucleotides" and "effective history".
  - R1-m3: The description of the t-SNE visualization lacks parameters (e.g., perplexity).
  - R1-m4: The discussion of limitations is brief and does not address potential biases in the training data.
- **Technical failings that need to be addressed before the case is established** R1-M1, R1-M2, R1-M3, R1-M4, R1-M5.
- **Assessment against Nature-style criteria** 
  - Originality: The approach of using a pre-trained predictor to initialize a generative model is original in the context of promoter design. However, similar transfer learning ideas exist in other domains.
  - Scientific importance: The problem of functional promoter design is important for synthetic biology. The method could contribute to this area if validated.
  - Interdisciplinary readership: The work bridges machine learning and synthetic biology, which could attract a broad audience. However, the presentation is heavily technical and may not be accessible to non-specialists without additional context.
  - Technical soundness: The technical approach is plausible, but the lack of figures, tables, and detailed statistical analysis undermines confidence. The evaluation metrics are appropriate but not fully reported.
  - Readability for nonspecialists: The manuscript is dense and assumes familiarity with both deep learning and promoter biology. The abstract is clear, but the methods and results sections are challenging for a general reader.
- **Recommendation posture** Currently not established from the provided evidence. The manuscript has potential but requires major revisions, including provision of all figures and tables, wet-lab validation or clear justification for the "functional" claim, quantitative comparison with baselines, and improved statistical reporting.

### Major Concerns

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Claim validity
- **Claim pointer** The abstract and introduction claim that Gen-DNA-TCN generates "functional" synthetic yeast promoter sequences.
- **Evidence pointer** Section 3.1, 3.3; location not provided
- **Concern** The term "functional" is used to describe the generated sequences, but no wet-lab experiments are reported to confirm that these sequences actually drive gene expression in vivo or in vitro. The evaluation relies solely on computational predictions from Pre-DNA-TCN and transcription factor binding site motif analysis. Computational prediction of expression is not equivalent to functional validation.
- **Why it matters** The central claim of the manuscript is that the generated sequences are functional. Without experimental validation, this claim is unsupported and potentially misleading. The synthetic biology community requires experimental evidence to establish functionality.
- **Resolution test** Provide experimental validation of a subset of generated promoters (e.g., reporter assays in yeast) demonstrating that they drive expression at levels consistent with predictions. Alternatively, clearly rephrase claims to state that sequences are "predicted to be functional" and discuss the limitations of computational validation.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence completeness
- **Claim pointer** The results section reports detailed quantitative comparisons (e.g., expression distributions, transcription factor binding site frequencies, Levenshtein distances) and visualizations (Figures 1–11, Tables 1–4).
- **Evidence pointer** Section 3; location not provided
- **Concern** All figures and tables are referenced but not included in the provided manuscript text. Without these, the reported results cannot be verified or assessed. The reader cannot evaluate the validity of the claims regarding similarity of distributions, correlation coefficients, or diversity.
- **Why it matters** The manuscript's conclusions rest entirely on these visual and tabular results. Their absence makes the manuscript incomplete and unverifiable.
- **Resolution test** Include all figures and tables in the manuscript or supplementary materials. Ensure they are clearly labeled and referenced in the text.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** No
- **Axis** Comparative evaluation
- **Claim pointer** The introduction criticizes existing methods (e.g., GAN-based, diffusion-based) for high computational cost, implying Gen-DNA-TCN is superior.
- **Evidence pointer** Section 1; location not provided
- **Concern** The manuscript does not provide a quantitative comparison of Gen-DNA-TCN with existing generative methods (e.g., DeepSEED, PromoDGDE, or other baselines) in terms of sequence quality, diversity, expression prediction accuracy, or computational cost. The claims of superiority are based on qualitative descriptions of prior work.
- **Why it matters** Without direct comparison, it is unclear whether Gen-DNA-TCN offers a meaningful improvement over existing approaches. The synthetic biology community needs benchmarks to choose among methods.
- **Resolution test** Include a comparative study with at least one or two baseline generative methods, using the same evaluation metrics and datasets. Report computational cost (e.g., training time, GPU hours) for all methods.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Methodological clarity
- **Claim pointer** The methods section describes the Gen-DNA-TCN architecture and training process, but key details are ambiguous.
- **Evidence pointer** Section 2.3; location not provided
- **Concern** The description of the generative process is unclear. Specifically, the text states that the model generates sequences of length 80, but then mentions generating up to 93 nucleotides and appending flanking sequences. The role of the "effective history" and the exact mechanism of autoregressive generation (e.g., how the model handles the flanking sequences) is not fully explained. Additionally, the choice of 1,000 epochs and the learning rate are stated, but no justification or sensitivity analysis is provided.
- **Why it matters** Reproducibility is a core requirement for computational methods. Ambiguities in the architecture and training details prevent other researchers from implementing or building upon the method.
- **Resolution test** Provide a more detailed and precise description of the model architecture, including layer sizes, number of layers, and the exact generation procedure. Include a pseudocode or algorithm box. Justify the choice of hyperparameters or provide a sensitivity analysis.

- **Concern ID** R1-M5
- **Severity** Major
- **Blocking** No
- **Axis** Statistical rigor
- **Claim pointer** The results report Pearson correlation coefficients (e.g., r=0.818, r=0.918) between transcription factor binding site frequencies in synthetic and real sequences.
- **Evidence pointer** Section 3.1; location not provided
- **Concern** The manuscript does not report confidence intervals, p-values, or any measure of statistical uncertainty for the reported correlation coefficients. It is unclear whether the differences between models (e.g., Model 1 vs. Model 2) are statistically significant.
- **Why it matters** Without statistical inference, the reader cannot assess the reliability of the reported similarities or the significance of differences between models. This weakens the conclusions drawn from the comparisons.
- **Resolution test** Provide confidence intervals or p-values for all reported correlation coefficients. Use appropriate statistical tests (e.g., bootstrap or permutation tests) to compare models.

### Minor Comments

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Accuracy
- **Affected element** Text
- **Evidence pointer** Section 2.4; location not provided
- **Issue** The database is referred to as "JASPER" but the correct name is "JASPAR".
- **Required correction** Correct the typo to "JASPAR".

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Terminology
- **Evidence pointer** Section 2.3; location not provided
- **Issue** The terms "starting nucleotides" and "effective history" are used but not clearly defined. It is unclear if they refer to the same concept.
- **Required correction** Define both terms explicitly and use them consistently throughout the manuscript.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Reproducibility
- **Affected element** Visualization
- **Evidence pointer** Section 3.2; location not provided
- **Issue** The t-SNE visualization is mentioned but no parameters (e.g., perplexity, learning rate) are given, making it difficult to reproduce.
- **Required correction** Provide the t-SNE parameters used for the visualization.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Discussion
- **Evidence pointer** Section 4; location not provided
- **Issue** The discussion does not address potential limitations of the approach, such as the reliance on a specific predictive model (Pre-DNA-TCN) or the generalizability to other organisms or promoter types.
- **Required correction** Add a paragraph discussing limitations and potential avenues for future work.

## Risk / unsupported claims
- The claim that generated sequences are "functional" is unsupported without wet-lab validation.
- The claim of "high computational efficiency" is not quantified or compared with baselines.
- The claim that Model 1 "accurately learns" transcription factor binding site distributions is based on visual inspection of figures that are not provided.
- The generalizability of the method to other organisms or sequence types is not demonstrated.
- The statistical significance of differences between models is not established.