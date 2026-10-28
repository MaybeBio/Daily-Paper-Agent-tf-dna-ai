## Review setup
- **Input scope** Full manuscript text including abstract, introduction, results, discussion, methods, and supplementary information references.
- **Assessment boundary** Scientific validity, technical soundness, methodological rigor, clarity of claims, and alignment with Nature Communications standards. No assessment of formatting or editorial style beyond readability.
- **Shared manuscript claim summary** The authors present DeepSEED, a two-stage AI-aided framework combining expert knowledge (fixed cis-regulatory element "seeds") with deep learning (a conditional GAN for flanking sequence generation and a DenseNet-LSTM predictor) to design synthetic promoters with improved activity. They demonstrate success in Escherichia coli constitutive, IPTG-inducible, and mammalian doxycycline-inducible promoters, and argue that flanking sequences carry implicit features (k-mer frequencies, DNA shape) critical for promoter function.
- **Visible evidence base** Abstract, full introduction, full results section with figure descriptions, full discussion, full methods section, and references to supplementary figures, data files, and prior work.
- **Missing materials affecting confidence** Actual figures and supplementary data files are not provided. Specific numerical results, statistical details, model architecture hyperparameters, training/validation splits, and full experimental datasets are referenced but not visible. This limits verification of quantitative claims and reproducibility.

## Reviewer
- **Overall assessment** This manuscript addresses a relevant and timely problem in synthetic biology: the systematic optimization of flanking sequences around known promoter elements. The conceptual framing, separating expert-defined seeds from data-driven flanking optimization, is sensible and potentially useful. The application to three distinct promoter types is a strength. However, the provided text alone does not allow full verification of the central claims. Key quantitative results, statistical comparisons, and model evaluation details are referenced but not shown. The biological interpretation of flanking sequence features, while plausible, is supported by correlative analyses that are not fully described. The manuscript is likely of interest to the synthetic biology and computational biology communities, but the strength of the conclusions cannot be fully assessed from the visible material.
- **Who would be interested in the results, and why** Researchers in synthetic biology, promoter engineering, and genetic circuit design would be the primary audience. The framework offers a practical method for improving promoter activity without altering core regulatory elements, which is directly applicable to metabolic engineering, gene therapy, and inducible expression systems. Computational biologists working on sequence-to-function models and generative models for regulatory DNA would also find the approach relevant. The demonstration across prokaryotic and eukaryotic systems broadens the potential impact.
- **Major strengths**
  1. The conceptual separation of expert knowledge (seeds) from data-driven flanking optimization is a clear and practical contribution.
  2. The framework is demonstrated on three distinct promoter types, showing versatility.
  3. The inclusion of interpretability analyses (saliency maps, DNA shape embedding) goes beyond simple performance claims.
  4. The authors address the risk of trivial sequence copying through edit distance and BLAST analyses.
  5. The writing is generally clear and accessible to a broad scientific audience.
- **Major Concerns**
  - **Concern ID** R1-M1
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Evidence sufficiency
  - **Claim pointer** The manuscript claims that DeepSEED "demonstrated success in improving the properties" of all three promoter types, with specific fold-improvements and success rates.
  - **Evidence pointer** Results sections "Design of constitutive promoters in E. coli", "Design of IPTG-inducible promoters in E. coli", "Design of Dox-inducible promoters in mammalian cells"; figures 3, 4, 5; supplementary figures 13-18.
  - **Concern** The central quantitative claims are not verifiable from the provided text. No actual activity values, fold-changes, statistical significance levels, or confidence intervals are given. The descriptions reference figures and supplementary data that are not visible. Without these data, the magnitude and reliability of the reported improvements cannot be assessed. This is a blocking issue for establishing the core case.
  - **Why it matters** The primary contribution of the manuscript is the empirical demonstration that flanking sequence optimization improves promoter performance. If the quantitative evidence is not presented in a verifiable form, the central claim is unsupported.
  - **Resolution test** Provide the actual numerical data for all experimental comparisons, including means, variances, sample sizes, and statistical tests. Ensure all figures and supplementary data are available for review.
  - **Concern ID** R1-M2
  - **Severity** Major
  - **Blocking** Yes
  - **Axis** Technical soundness
  - **Claim pointer** The manuscript claims that the DenseNet-LSTM predictor accurately predicts promoter activity and that the cGAN generates flanking sequences that capture implicit features.
  - **Evidence pointer** Methods sections "DeepSEED generative and predictive networks", "Promoter design approach"; supplementary figures 1, 2.
  - **Concern** The model training, validation, and testing procedures are not described in sufficient detail. Key hyperparameters, dataset splits, and evaluation metrics are missing. The predictor's accuracy is not quantified. The cGAN's training stability and mode collapse are mentioned but not demonstrated. Without these details, the technical soundness of the models cannot be evaluated.
  - **Why it matters** The framework relies entirely on the quality of the generative and predictive models. If the models are not rigorously validated, the reliability of the designed promoters is questionable.
  - **Resolution test** Provide full model architecture details, training procedures, hyperparameter settings, dataset splits, and quantitative performance metrics (e.g., correlation coefficients, AUC, loss curves) for both the predictor and the generator.
  - **Concern ID** R1-M3
  - **Severity** Major
  - **Blocking** No
  - **Axis** Biological interpretation
  - **Claim pointer** The manuscript claims that DeepSEED "captures the implicit features in flanking sequences, such as k-mer frequencies and DNA shape features, which are crucial for determining promoter properties."
  - **Evidence pointer** Results section "DeepSEED captures essential features of natural promoter sequences"; figure 2.
  - **Concern** The causal link between the captured features and promoter activity is not established. The analyses show correlations (k-mer frequency correlations, DNA shape clustering) but do not demonstrate that these features are causally responsible for the improved activity. The saliency map analysis is descriptive. The claim of "crucial" is stronger than the evidence supports.
  - **Why it matters** The manuscript positions flanking sequence features as a key mechanistic insight. If the causal role is not established, the claim is overstated and the generalizability of the approach is less certain.
  - **Resolution test** Perform perturbation experiments (e.g., mutate specific flanking positions predicted to be important and measure activity) or use attribution methods to demonstrate a causal link. Alternatively, temper the claim to "associated with" rather than "crucial for."
  - **Concern ID** R1-M4
  - **Severity** Major
  - **Blocking** No
  - **Axis** Comparison to existing methods
  - **Claim pointer** The manuscript claims that DeepSEED outperforms previous whole-sequence generation methods, with a 6.73-fold average increase in promoter activity.
  - **Evidence pointer** Results section "Design of constitutive promoters in E. coli", figure 3d.
  - **Concern** The comparison to the prior method (Wang et al. 2020) is presented as a single average fold-change. The conditions of the comparison are not fully described. Were the same seeds used? Were the same experimental conditions and normalization applied? Without a controlled comparison, the claimed advantage is not robustly established.
  - **Why it matters** The novelty of DeepSEED relative to prior work is a key selling point. A weak comparison undermines this claim.
  - **Resolution test** Provide a detailed description of the comparison protocol, including all experimental conditions, and show the full distribution of results, not just the average.
- **Minor Comments**
  - **Concern ID** R1-m1
  - **Severity** Minor
  - **Axis** Clarity
  - **Affected element** Abstract
  - **Evidence pointer** Abstract, last sentence.
  - **Issue** The phrase "captures the implicit features in flanking sequences" is vague. It is unclear whether "captures" means the model learns these features, or the analysis reveals them.
  - **Required correction** Rephrase to be specific, e.g., "DeepSEED-generated sequences reproduce k-mer frequency and DNA shape distributions of natural promoters, and these features correlate with activity."
  - **Concern ID** R1-m2
  - **Severity** Minor
  - **Axis** Reproducibility
  - **Affected element** Methods, "DeepSEED generative and predictive networks"
  - **Evidence pointer** Methods section, paragraph on network architecture.
  - **Issue** The description of the generator and discriminator architectures is incomplete. The number of attention heads, layers, and the exact loss weighting (lambda) are not specified.
  - **Required correction** Provide a full architectural summary, possibly in a table or supplementary figure, with all hyperparameters.
  - **Concern ID** R1-m3
  - **Severity** Minor
  - **Axis** Statistical rigor
  - **Affected element** Results, all experimental sections
  - **Evidence pointer** Figures 3, 4, 5.
  - **Issue** The number of biological replicates is stated as three, but the statistical treatment of these replicates is not described. Are error bars standard deviation or standard error? Were any tests for normality or variance equality performed?
  - **Required correction** State the error bar definition and the statistical tests used in all figure legends.
  - **Concern ID** R1-m4
  - **Severity** Minor
  - **Axis** Generalizability
  - **Affected element** Discussion
  - **Evidence pointer** Discussion, paragraph on limitations.
  - **Issue** The discussion of genomic context is brief. Given that the authors acknowledge this as a limitation, a more detailed consideration of how the approach might be adapted for chromosomal integration would strengthen the manuscript.
  - **Required correction** Expand the discussion on genomic context, possibly referencing relevant literature on chromatin effects on promoter activity.
- **Technical failings that need to be addressed before the case is established**
  1. R1-M1: Missing quantitative data for all experimental claims.
  2. R1-M2: Insufficient model training and validation details.
  3. R1-M3: Overstated causal interpretation of correlative feature analyses.
  4. R1-M4: Incomplete description of the comparison to prior methods.
- **Assessment against Nature-style criteria**
  - **Originality** The idea of using a conditional GAN to generate flanking sequences around fixed regulatory elements is a novel combination of existing techniques. The explicit focus on flanking sequences as a design variable, rather than whole-sequence generation, is a useful conceptual contribution. However, the individual components (GANs for sequence generation, predictors for activity) are not new. The originality is moderate and incremental.
  - **Scientific importance** The problem of promoter design is important for synthetic biology. The potential to improve promoter activity without altering core elements has practical value. However, the importance is somewhat limited by the lack of demonstrated generality beyond the three tested promoter types and the absence of mechanistic insight into why the flanking sequences work.
  - **Interdisciplinary readership** The manuscript bridges machine learning and synthetic biology. The writing is accessible to both communities, with clear explanations of biological concepts for computational readers and model concepts for experimental readers. The potential readership is broad, but the impact may be limited to those specifically working on promoter design.
  - **Technical soundness** The technical soundness cannot be fully assessed due to missing details. The described approach is plausible, but the lack of model validation details and quantitative results is a significant concern. The experimental design appears reasonable, but the statistical treatment is not fully described.
  - **Readability for nonspecialists** The manuscript is well-written and the conceptual framework is easy to follow. The use of figures to illustrate the workflow is helpful. However, the methods section is dense and may be challenging for readers without a computational background. The abstract is clear and accessible.
- **Recommendation posture** Supportive if technical concerns are resolved. The conceptual framework and the breadth of applications are promising. However, the manuscript cannot be accepted in its current form because the central quantitative claims are not verifiable from the provided material. The authors must provide the full dataset, detailed model descriptions, and rigorous statistical analyses. If these are provided and the claims hold, the manuscript would be a valuable contribution to the field.