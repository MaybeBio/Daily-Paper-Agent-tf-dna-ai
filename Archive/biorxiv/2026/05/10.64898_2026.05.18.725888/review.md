## Review setup

- **Input scope** Full manuscript text (abstract, introduction, methods, results, discussion, data availability, acknowledgments) as provided by the author. No figures, tables, or supplementary materials were included in the supplied material.
- **Assessment boundary** This review assesses the scientific claims, methodological soundness, and evidentiary support based solely on the text provided. No raw data, code outputs, or figure contents were available for independent verification.
- **Shared manuscript claim summary** The authors claim that pairwise-additive models (PWM, PSAM) systematically underperform relative to models incorporating non-additive interactions (adjacent dinucleotide, CNN) when predicting absolute TF–DNA dissociation constants (Kd) measured by the ivt FOODIE assay across 45 TFs. They further claim that the magnitude of non-pairwise-additivity is TF-family-dependent and that long-range interposition dependencies are widespread and energetically significant.
- **Visible evidence base** Text descriptions of results referencing Figures 1–5, median Pearson correlation coefficients for four models, and qualitative descriptions of epistasis maps. No actual figure content, numerical tables, or statistical details were provided in the supplied material.
- **Missing materials affecting confidence** All figures and their underlying data, model training details (hyperparameters, data splits, sequence lengths), the complete list of 45 TFs with family assignments, the definition of the interposition dependency score formula (appears truncated), statistical significance tests, and code verification. The Methods section is incomplete with respect to several critical details.

## Reviewer

- **Overall assessment** The manuscript addresses an important question in TF–DNA binding modeling: whether pairwise-additive assumptions are sufficient when evaluated against absolute thermodynamic measurements. The use of ivt FOODIE data to benchmark models of increasing complexity is a valuable approach. However, the current text does not provide sufficient quantitative evidence to support the central claims. Key statistical details, figure contents, and methodological specifics are absent from the supplied material, making it impossible to assess the robustness of the conclusions. The conceptual framework is sound and the question is timely, but the evidentiary base as presented is incomplete.
- **Who would be interested in the results, and why** Researchers in transcriptional regulation, computational biology, and biophysics would find these results relevant. The systematic comparison of model classes against absolute Kd data addresses a long-standing debate about the sufficiency of additive models. The finding that non-additivity varies by TF family has practical implications for those building predictive models of TF binding in regulatory genomics. The in silico epistasis analysis could interest those studying allosteric communication in protein–DNA recognition.
- **Major strengths** The use of absolute thermodynamic measurements (Kd) rather than relative occupancy data is a clear strength, as it enables quantitative energetic interpretation. The systematic progression from simple additive models to non-linear architectures provides a clean conceptual framework. The focus on TF-family-specific differences is a useful contribution that moves beyond global averages. The in silico double-mutant approach for mapping interposition dependencies is a reasonable strategy for extracting mechanistic insight from trained models.
- **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Evidence sufficiency
- **Claim pointer** The claim that "pairwise additive models exhibit systematic deviations from the measured affinity landscapes" and that the CNN achieves "the strongest agreement with experiment" is central to the paper.
- **Evidence pointer** Results section, Figures 2 and 3, location not provided
- **Concern** The manuscript reports median Pearson correlation coefficients (0.513, 0.641, 0.701, 0.751) but provides no measures of variance, no per-TF breakdown, no statistical tests comparing model performance, and no information about the distribution of performance across the 45 TFs. The figures referenced are not available in the supplied material. Without these details, the claim that the improvements are systematic and meaningful cannot be evaluated. The difference between PSAM (0.641) and CNN (0.751) may be driven by a subset of TFs, and the text does not address this possibility.
- **Why it matters** The central conclusion of the paper rests on the magnitude and consistency of the performance gap between additive and non-additive models. If the improvement is marginal for most TFs and large for only a few, the claim of "systematic deviations" would be overstated. The absence of statistical rigor undermines the quantitative framework the authors claim to provide.
- **Resolution test** Provide per-TF correlation values, confidence intervals or standard errors for the median correlations, and a statistical test (e.g., paired Wilcoxon signed-rank test) comparing model performance across the 45 TFs. Show the distribution of Δr values in a figure or table.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Methodological completeness
- **Claim pointer** The interposition dependency score ε is defined using an in silico double-mutant approach, and the authors claim it quantifies "energetic epistasis" between positions i and j.
- **Evidence pointer** Methods, In Silico Mutations Analysis section, location not provided
- **Concern** The formula for ε is truncated in the supplied text. The definition is incomplete, and the computational procedure is not fully specified. It is unclear how the CNN predictions are used, whether the analysis is restricted to the core motif or extends to flanking regions, how the 256 flanking sequences were selected beyond "highest experimental affinities," and how the signed mean is computed across substitutions and contexts. Without a complete specification, the results in Figure 5 cannot be interpreted or reproduced.
- **Why it matters** The long-range dependency analysis is a major component of the paper's contribution. If the metric is not precisely defined, the biological conclusions about "energetic coupling across distant positions" are not verifiable. Reproducibility is a core requirement for this type of computational analysis.
- **Resolution test** Provide the complete formula for ε, a step-by-step description of the computational procedure, and details on how flanking sequences were selected and how the aggregation across substitutions and contexts was performed.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Data availability and verification
- **Claim pointer** The authors state that "we utilize data from a high-throughput in vitro assay (ivt FOODIE) to generate genome-scale TF–DNA dissociation constants (Kd)" for 45 TFs.
- **Evidence pointer** Methods, ivt FOODIE Assay and Kd Estimation section; Data Availability section, location not provided
- **Concern** The raw Kd data, the list of 45 TFs, the genomic library details, and the quality metrics for the Kd measurements are not provided. The Data Availability section only mentions code on GitHub, not the underlying experimental data. Without access to the Kd measurements, the benchmark results cannot be independently verified. Additionally, the Methods description of the ivt FOODIE assay is brief and lacks critical details such as the number of replicates, the range of TF concentrations, the fitting procedure for the Hill equation, and quality control criteria.
- **Why it matters** The entire paper depends on the quality and accessibility of the Kd dataset. If the data are not publicly available, the claims cannot be validated by the community. The assay description is also insufficient to assess potential systematic biases in the measurements.
- **Resolution test** Deposit the raw Kd data and the complete list of TFs in a public repository. Provide a detailed Methods description of the ivt FOODIE assay, including replicates, concentration ranges, fitting procedures, and quality filters.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Interpretive caution
- **Claim pointer** The authors claim that "the predicted epistasis represents true physical interaction energies rather than statistical correlations" and that long-range dependencies reflect "energetic coupling across distant positions."
- **Evidence pointer** Discussion section, location not provided
- **Concern** The in silico double-mutant analysis uses CNN predictions, which are themselves learned from the training data. The ε values therefore reflect the model's learned representation, not directly measured physical energies. The claim that these are "true physical interaction energies" is an interpretation that requires additional validation, such as experimental mutagenesis or comparison with independent biophysical measurements. The text does not acknowledge this limitation.
- **Why it matters** Overstating the physical interpretation of model-derived quantities could mislead readers about the strength of the evidence. The distinction between model-inferred and experimentally measured energetic coupling is important for the paper's conclusions.
- **Resolution test** Soften the language to "model-inferred energetic coupling" or provide independent experimental validation for a subset of the predicted long-range interactions.

- **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Clarity
- **Affected element** Abstract, first sentence
- **Evidence pointer** Abstract, location not provided
- **Issue** The phrase "ivt FOODIE" is used without expansion or context in the abstract. Readers unfamiliar with the assay will not know what it measures or how it works.
- **Required correction** Expand the acronym at first use, e.g., "in vitro transcription factor occupancy detection by engineered deaminase (ivt FOODIE)," or provide a brief parenthetical description.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Completeness
- **Affected element** Methods, Model Training section
- **Evidence pointer** Methods, Sequence Representation, Model Training, and Evaluation, location not provided
- **Issue** The description of the CNN architecture is minimal. The number of filters, kernel sizes, stride, padding, pooling layers, dropout, learning rate, optimizer, loss function, and training epochs are not specified. The train/validation/test split procedure is also not described.
- **Required correction** Provide full architectural and training details to enable reproduction.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Statistical reporting
- **Affected element** Results, Figure 3 description
- **Evidence pointer** Results section, location not provided
- **Issue** The text reports median Pearson correlations but does not report the range, interquartile range, or any measure of dispersion. It is unclear whether the performance differences are consistent across all TFs or driven by outliers.
- **Required correction** Report the full distribution of per-TF correlations, including quartiles or standard deviations, and consider showing a boxplot or violin plot.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Terminology
- **Affected element** Discussion, first paragraph
- **Evidence pointer** Discussion section, location not provided
- **Issue** The phrase "circumvented non-pairwise-additivity" in the final summary sentence is unclear. It is not obvious what "circumvented" means in this context.
- **Required correction** Rephrase for clarity, e.g., "established a rigorous quantitative deep learning framework that accounts for non-pairwise-additive effects."

- **Concern ID** R1-m5
- **Severity** Minor
- **Axis** Referencing
- **Affected element** Introduction, reference 21
- **Evidence pointer** Introduction, location not provided
- **Issue** The ivt FOODIE assay is cited as reference 21, but the reference list is not provided in the supplied material. The reader cannot verify the assay details or the prior publication.
- **Required correction** Ensure the reference list is complete and that reference 21 is a peer-reviewed publication describing the ivt FOODIE assay.

- **Technical failings that need to be addressed before the case is established** The incomplete definition of the interposition dependency score (R1-M2) and the absence of statistical validation for the model comparison (R1-M1) are the most critical technical issues. The lack of data availability (R1-M3) also prevents independent verification. These must be resolved before the central claims can be considered established.
- **Assessment against Nature-style criteria** 
  - Originality: The application of absolute Kd measurements to benchmark additive versus non-additive models is a valuable and relatively underexplored approach. The focus on TF-family-specific differences adds a useful dimension. However, the conceptual framework of comparing additive and non-additive models is not entirely new, and the novelty rests on the scale and quality of the data.
  - Scientific importance: The question of whether pairwise-additive models are sufficient for TF–DNA binding is of broad importance in regulatory genomics. If the claims are substantiated, the results would have practical implications for model choice in predictive applications. The potential impact is high.
  - Interdisciplinary readership: The topic bridges biophysics, computational biology, and genomics. The writing is generally accessible, though the Methods section assumes familiarity with deep learning and high-throughput binding assays. The abstract is clear for a broad audience.
  - Technical soundness: Cannot be fully assessed from the supplied material. The incomplete Methods, missing statistical details, and truncated formula prevent evaluation of the technical rigor. The conceptual approach is reasonable, but the execution details are not verifiable.
  - Readability for nonspecialists: The Introduction and Discussion are well written and accessible. The Results section relies heavily on figures that were not provided, making it difficult to follow the narrative. The abstract is concise and clear.
- **Recommendation posture** Currently not established from the provided evidence. The conceptual framework is promising and the question is important, but the supplied material lacks the quantitative detail, statistical rigor, and data availability required to support the central claims. The manuscript could become publishable after substantial revision and supplementation of the missing information.

## Risk / unsupported claims

- The claim that "pairwise additive models exhibit systematic deviations" is unsupported without per-TF performance distributions and statistical tests.
- The claim that "the predicted epistasis represents true physical interaction energies" is an interpretation that goes beyond what model-derived quantities can establish without independent validation.
- The claim that "long-range interposition dependencies" are "widespread" is based on Figure 5, which was not provided, and the incomplete definition of ε prevents assessment.
- The claim that the CNN "achieved the strongest agreement with experiment" is based on median correlations without measures of variance or significance.
- The claim that "the magnitude of non-pairwise-additivity depends strongly on the TF family" is based on Figure 4, which was not provided, and no quantitative family-level statistics are given in the text.
- The statement that "distal coupling collectively accounted for up to 40% of the non-pairwise-additive energy landscape" is unverifiable without the underlying data and figure content.