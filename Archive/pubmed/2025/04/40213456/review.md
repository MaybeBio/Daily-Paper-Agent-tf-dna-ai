## Review setup
- **Input scope** Full manuscript text (abstract, main text, experimental section) as provided
- **Assessment boundary** Scientific claims, methodology, data interpretation, and generalizability as presented in the supplied material
- **Shared manuscript claim summary** The authors propose a deep learning-based approach using InceptionV3 to classify histone-DNA interactions based on polarized light microscopy images of drying droplet patterns. They report 100% classification accuracy for four DNA types, differential prediction accuracy for binding affinity based on DNA type (eukaryotic vs. prokaryotic) and size, and generalizability to unknown species (84.4% and 96.25% accuracy for strong and medium binders, respectively).
- **Visible evidence base** Main text figures referenced (Figures 1-6), supplementary figures referenced (Figures S1-S5), experimental methods, ethidium bromide displacement assay results
- **Missing materials affecting confidence** Raw image data, full confusion matrices for all experiments, hyperparameter details, cross-validation results, statistical significance tests for accuracy differences, code availability, detailed Grad-CAM analysis, and quantitative binding affinity measurements (e.g., Kd values) for direct comparison

## Reviewer
- **Overall assessment** The manuscript presents a novel application of deep learning to classify histone-DNA interactions via drying droplet patterns, a technique with potential for high-throughput screening. The core concept is interesting and the reported accuracies are impressive. However, several methodological gaps and potential overclaims regarding binding affinity prediction and generalizability require clarification and additional validation before the case is fully established.
- **Who would be interested in the results, and why** Researchers in biophysics, molecular biology, and biotechnology interested in protein-DNA interactions, label-free biosensing, and machine learning applications in biological pattern recognition. The method could appeal to those seeking rapid, low-cost screening tools for DNA-binding proteins or ligands.
- **Major strengths** 1) Novel application of drying droplet patterns combined with deep learning for protein-DNA interaction analysis. 2) High reported classification accuracies (100% for DNA type). 3) Demonstration of generalizability to unseen species, albeit with lower accuracy. 4) Use of complementary techniques (SEM, TOF-SIMS) for pattern characterization. 5) Potential for high-throughput, automated screening.
- **Major Concerns** 
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Claim validity
  - **Claim pointer** The manuscript claims that the CNN can predict "binding affinities" of histone-DNA interactions based on drying droplet patterns, with higher accuracy for eukaryotic DNA (99%) compared to prokaryotic DNA (93%).
  - **Evidence pointer** Figure 4, Results section "Relative Affinity of H1–DNA Interaction - Based on DNA Type"
  - **Concern** The claim of predicting "binding affinity" is not directly supported by quantitative binding measurements. The ethidium bromide displacement assay provides a relative, indirect measure of binding, but no actual binding constants (e.g., Kd) or quantitative affinity values are reported. The CNN classifies images into categories (DNA type, ratio), but the link between classification accuracy and actual binding affinity is inferred, not demonstrated. Higher classification accuracy for eukaryotic DNA is interpreted as reflecting higher binding affinity, but this correlation is not rigorously established.
  - **Why it matters** The central premise of the manuscript is that the method can stratify protein-DNA interactions by binding affinity. Without direct quantitative validation of binding affinity, the claim remains speculative. The method may be classifying based on other physicochemical properties (e.g., droplet drying dynamics, salt crystallization) that correlate with DNA type or size but not necessarily with binding affinity per se.
  - **Resolution test** Provide quantitative binding affinity measurements (e.g., surface plasmon resonance, isothermal titration calorimetry, or fluorescence anisotropy) for the histone-DNA complexes used, and demonstrate a statistically significant correlation between CNN classification accuracy (or confidence scores) and measured binding affinities across multiple DNA types and ratios.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Generalizability
  - **Claim pointer** The manuscript claims that a pre-trained CNN can classify unknown histone-DNA samples from species not included in the training set, with 84.4% and 96.25% accuracy for strong and medium binders, respectively.
  - **Evidence pointer** Figure 6, Results section "Classification of Unknown Histone–DNA Interactions"
  - **Concern** The generalizability claim is based on a single unknown species (Calf DNA). The definition of "strong" and "medium" binders is not clearly operationalized. It is unclear how these categories were defined (e.g., based on the ethidium bromide assay, literature values, or CNN confidence scores). The sample size for the unknown species test is not specified. The statement that "the vast majority (96%) of stain patterns were accurately classified as eukaryotic DNA" is ambiguous, as it conflates classification of DNA type with binding affinity prediction.
  - **Why it matters** Generalizability is a key selling point of the method. A single test case with unclear category definitions and sample sizes is insufficient to establish robust generalizability. The claim that the model can predict binding affinity of unseen species requires more rigorous validation across multiple species and clear, pre-defined affinity categories.
  - **Resolution test** Test the pre-trained model on multiple unknown species (e.g., 3-5 different sources) with defined affinity categories based on independent quantitative measurements. Report sample sizes, confidence intervals, and statistical significance. Clarify the criteria for "strong" and "medium" binding categories.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Technical soundness
  - **Claim pointer** The manuscript states that "the categorization of PLM images was carried out and resulted in an accuracy rate of 100% for each group" (Figure 3B).
  - **Evidence pointer** Figure 3, Results section "Classification of Various DNA"
  - **Concern** While 100% accuracy is reported, the manuscript does not provide details on potential overfitting, class imbalance, or the robustness of the model. The training set size (400 images per class) is relatively small for a deep network like InceptionV3. No cross-validation results, learning curves, or analysis of misclassification patterns are provided. The possibility of the model learning non-specific features (e.g., salt concentration, droplet size variations) rather than DNA-specific features is not addressed.
  - **Why it matters** High accuracy on a small, controlled dataset does not guarantee robustness. Without evidence of generalization within the dataset (e.g., cross-validation) and analysis of potential confounding variables, the 100% accuracy may be misleading.
  - **Resolution test** Provide cross-validation results, learning curves, and an analysis of model sensitivity to variations in experimental conditions (e.g., salt concentration, humidity, droplet volume). Include a discussion of potential confounding factors and how they were controlled.
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Reproducibility
  - **Claim pointer** The experimental section describes the use of a specific buffer (100 mM HEPES, 150 mM KCl, 50 mM ammonium sulfate) and drying conditions (23°C, 40% humidity, 50 min).
  - **Evidence pointer** Experimental Section "Histone-DNA Solutions" and "Droplet Deposition"
  - **Concern** The manuscript does not report the number of independent experimental replicates (e.g., how many times the droplet drying experiments were repeated) or the variability in droplet patterns across replicates. The robustness of the patterns to minor variations in environmental conditions (temperature, humidity) is not assessed. The manuscript also does not specify how many images were collected per droplet or per sample.
  - **Why it matters** Reproducibility is essential for a method intended for practical applications. Without information on experimental variability and replication, it is difficult to assess the reliability of the reported accuracies.
  - **Resolution test** Report the number of independent replicates, the variability in classification accuracy across replicates, and the sensitivity of the method to controlled variations in drying conditions.
- **Minor Comments** 
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Figure 4D
  - **Evidence pointer** Figure 4D
  - **Issue** The figure presents classification accuracies for various ratios, but the exact ratios and the number of images per ratio are not clearly labeled in the text.
  - **Required correction** Provide a clear table or figure legend specifying the ratios, sample sizes, and statistical significance of accuracy differences.
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Methodology
  - **Affected element** Ethidium bromide displacement assay
  - **Evidence pointer** Experimental Section "Ethidium Bromide Displacement Assay"
  - **Issue** The assay is described briefly, but the concentration of EtBr relative to DNA (0.1 mM per 168 bp) seems unusually high and may not be physiologically relevant. The manuscript does not report the fluorescence values or the extent of displacement quantitatively.
  - **Required correction** Provide quantitative fluorescence data (e.g., IC50 values or percentage displacement) and justify the EtBr concentration used.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Statistical analysis
  - **Evidence pointer** Experimental Section "Statistical Analysis"
  - **Issue** The statistical analysis section mentions ANOVA and LSD, but the specific comparisons and results are not reported in the main text.
  - **Required correction** Report the statistical test results (F-values, p-values) for the key comparisons, particularly those related to accuracy differences between DNA types and ratios.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Presentation
  - **Affected element** Figure 1
  - **Evidence pointer** Figure 1
  - **Issue** The SEM and TOF-SIMS images are described but not quantitatively analyzed. The manuscript does not explain how these characterizations support the classification results.
  - **Required correction** Either provide quantitative analysis of the SEM/TOF-SIMS data or clarify their role as qualitative supporting evidence.
  - **Concern ID** R1-m5
  - **Severity** Minor
  - **Axis** Completeness
  - **Affected element** Data availability
  - **Evidence pointer** Data Availability Statement
  - **Issue** The data availability statement says data are available "upon reasonable request," which is vague and not in line with open science practices.
  - **Required correction** Consider depositing the image dataset and code in a public repository to facilitate reproducibility.

## Technical failings that need to be addressed before the case is established
- R1-M1: Lack of direct quantitative binding affinity measurements to support the claim of affinity prediction.
- R1-M2: Insufficient evidence for generalizability (single unknown species, unclear category definitions).
- R1-M3: Inadequate validation of the deep learning model (no cross-validation, potential overfitting, confounding factors).
- R1-M4: Lack of information on experimental replicates and variability.

## Risk / unsupported claims
- The claim that the CNN predicts "binding affinities" is unsupported by direct quantitative measurements; the ethidium bromide assay is indirect and not quantitatively linked to CNN outputs.
- The claim of "comprehensive DNA categorization (100% accuracy)" is based on a single test set without cross-validation or analysis of potential confounders.
- The generalizability claim (84.4% and 96.25% accuracy for unknown species) is based on a single species and lacks clear operational definitions of "strong" and "medium" binders.
- The statement that "the vast majority (96%) of stain patterns were accurately classified as eukaryotic DNA" conflates DNA type classification with binding affinity prediction and is not clearly supported by the data presented.
- The claim that "only 10 images are sufficient to obtain 90+% accuracy" is based on a single analysis (Figure S4) and lacks statistical rigor.

## Assessment against Nature-style criteria
- **Originality** Moderate. The application of deep learning to drying droplet patterns for protein-DNA interaction analysis is novel, though the underlying techniques (droplet drying, CNN classification) are established. The combination is creative but builds on prior work by the same group.
- **Scientific importance** Moderate. The method could offer a rapid, low-cost screening tool, but the lack of quantitative validation limits its immediate impact. The biological insights gained are limited, as the method classifies patterns without explaining the underlying physical or molecular mechanisms.
- **Interdisciplinary readership** Moderate. The work bridges materials science, biophysics, and machine learning, which could appeal to a broad audience. However, the technical depth in each area may limit accessibility.
- **Technical soundness** Weak. The deep learning methodology lacks rigorous validation (cross-validation, confounding analysis). The binding affinity claims are not supported by quantitative measurements. Experimental reproducibility is not adequately documented.
- **Readability for nonspecialists** Acceptable. The manuscript is generally clear, but some sections (e.g., CNN training details, TOF-SIMS analysis) may be challenging for readers without specialized knowledge. The figures are illustrative but not always quantitatively informative.

## Recommendation posture
**Currently not established from the provided evidence.** The core concept is promising, but the claims of binding affinity prediction and generalizability are not sufficiently supported by the data and methodology as presented. The manuscript would require substantial revisions, including direct quantitative binding measurements, more rigorous model validation, and clearer operational definitions of affinity categories, before the case can be considered established.