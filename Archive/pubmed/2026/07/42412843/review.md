## Review setup
- **Input scope** Full manuscript text (main text, methods, results, discussion) as provided
- **Assessment boundary** Scientific content, methodological soundness, claims versus evidence, and presentation quality
- **Shared manuscript claim summary** The authors present NPBIP, a method that integrates a similarity-based component (SimBind) and a deep-learning component (NucProNet) to predict binding preferences of uncharacterized nucleic-acid-binding proteins (NBPs) to any RNA or DNA sequence. They report significant improvements over existing methods and comparable or superior performance relative to experimental k-mer upper bounds, with interpretability analysis recovering canonical motifs.
- **Visible evidence base** Main text, methods, results sections, figure references (Figs 1–6, supplementary figures), tables referenced (Table 1), and supplementary material descriptions
- **Missing materials affecting confidence** Supplementary figures and tables (Figs 1–13 supplementary, Tables 1 supplementary), full hyperparameter details, exact model architecture specifications, and complete benchmark results are referenced but not provided in the submitted material

## Reviewer

### **Overall assessment**
The manuscript addresses a timely and important problem in computational biology: predicting binding preferences of uncharacterized nucleic-acid-binding proteins to arbitrary sequences. The proposed NPBIP method combines a similarity-based approach with a deep-learning model, which is a sensible and potentially powerful strategy. The results are promising, with reported performance exceeding existing methods and approaching experimental upper bounds. However, several technical aspects require clarification and additional validation before the claims can be fully established. The interpretability analysis is a strength, but the overall evidence base is incomplete due to missing supplementary materials.

### **Who would be interested in the results, and why**
Computational biologists working on protein–nucleic-acid interactions, machine learning practitioners developing predictive models for biological sequences, and experimental biologists studying gene regulation who need tools to predict binding preferences of uncharacterized proteins. The method's ability to handle both RNA- and DNA-binding proteins without prior experimental data for the query protein makes it broadly applicable.

### **Major strengths**
1. The problem addressed (NewProNewSeq) is well-defined and practically important, with clear limitations identified in existing methods.
2. The two-component architecture (similarity-based plus deep-learning) is conceptually sound and leverages complementary information sources.
3. Evaluation on large datasets (420 RBP and 464 DBP experiments) provides reasonable statistical power.
4. The interpretability analysis using occlusion and motif recovery adds biological validation beyond raw predictive performance.
5. The comparison against experimental k-mer upper bounds provides a meaningful performance context.

### **Major Concerns**

- **Concern ID** R1-M1
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "NPBIP significantly outperformed each of its components and all competing baselines, achieving a mean Pearson correlation of 0.414±0.20 and 0.581±0.22 over the RNA- and DNA-binding experiments, respectively."
- **Evidence pointer** Section 3.2, Section 3.3, Figures 4A and 4B (main text)
- **Concern** The reported performance metrics are presented as means with standard deviations, but the statistical testing methodology is not fully described. The authors mention Wilcoxon signed-rank tests, but it is unclear how multiple testing across many comparisons was handled. Additionally, the variance across experiments is substantial (SD of 0.20–0.22), and it is not clear whether the reported improvements are consistent across all test proteins or driven by a subset. The comparison to the experimental k-mer upper bound for DNA (where NPBIP reportedly surpasses it) is particularly surprising and requires careful scrutiny, as it suggests the model captures information beyond what is contained in the k-mer model derived from the same experimental data.
- **Why it matters** The core claim of the manuscript is that NPBIP outperforms existing methods and approaches or exceeds experimental upper bounds. If the statistical analysis is not robust or the comparison methodology is flawed, the central conclusions may not hold.
- **Resolution test** Provide a detailed description of the statistical testing procedure, including how multiple comparisons were controlled. Report the distribution of per-protein performance differences (e.g., paired differences with confidence intervals). For the DNA result where NPBIP exceeds the k-mer upper bound, provide a detailed analysis of why this occurs, including potential artifacts in the k-mer model construction or evaluation protocol.

- **Concern ID** R1-M2
- **Severity** Major
- **Blocking** Yes
- **Axis** Technical soundness
- **Claim pointer** "NucProNet is a two-tower deep-learning model that receives a protein sequence and a nucleic-acid sequence as input, and outputs a single predicted binding affinity."
- **Evidence pointer** Section 2.4, Supplementary Methods (referenced but not provided)
- **Concern** The deep-learning architecture is described at a high level, but critical details are missing. The authors state that NucProNet uses ESM-2 embeddings, convolutional layers, and a transformer, but the exact architecture, hyperparameters, training procedure, and computational resources are not specified in the main text. The supplementary methods are referenced but not available for review. Without these details, the work cannot be reproduced, and the technical soundness of the model cannot be fully assessed. Additionally, the choice of mean-pooling for protein embeddings is a significant simplification that may lose important positional information.
- **Why it matters** Reproducibility is a fundamental requirement for computational methods. The lack of architectural and training details prevents independent validation and limits the scientific contribution.
- **Resolution test** Provide complete architectural specifications, including layer sizes, number of parameters, training hyperparameters, and computational requirements. Justify the mean-pooling choice for protein embeddings and discuss potential alternatives.

- **Concern ID** R1-M3
- **Severity** Major
- **Blocking** Yes
- **Axis** Scientific importance
- **Claim pointer** "NPBIP is the first method designed to directly solve the NewProNewSeq problem: predicting the binding affinity of uncharacterized NBPs to any given nucleic-acid sequence."
- **Evidence pointer** Section 1 (Introduction), Section 4 (Discussion)
- **Concern** The claim of being "the first" method for this task is strong and requires a thorough literature review to substantiate. While the authors mention several existing methods (JPLE, Affinity Regression, ProbeRating), it is not clear whether a comprehensive search was conducted for methods that might address this problem, even if not explicitly framed as such. Methods that predict binding from protein sequence alone, or that use transfer learning from related proteins, might partially address this task.
- **Why it matters** The novelty claim is central to the manuscript's contribution. If similar methods exist, the novelty is diminished, and the comparison against them would be necessary.
- **Resolution test** Provide a more comprehensive literature review, including methods from related fields (e.g., protein–protein interaction prediction, general protein function prediction) that might be applicable. Clearly state the search strategy and inclusion criteria for the comparison methods.

- **Concern ID** R1-M4
- **Severity** Major
- **Blocking** No
- **Axis** Technical soundness
- **Claim pointer** "Our analysis of replicate experiments, comprising 64 pairs for RNAcompete and 10 for PBM, revealed mean correlations of 0.542±0.29 and 0.818±0.10, respectively."
- **Evidence pointer** Section 4 (Discussion)
- **Concern** The replicate analysis is mentioned only briefly in the Discussion, with no details on how replicates were identified, whether they represent the same protein assayed in different experiments, or how the correlation was computed. The small number of PBM replicate pairs (10) raises questions about the reliability of the estimated upper bound. Additionally, the RNAcompete replicate correlation (0.542) is notably lower than the NPBIP performance (0.414), suggesting that NPBIP is still substantially below the experimental noise floor, which is not clearly communicated.
- **Why it matters** The replicate analysis provides an important context for interpreting NPBIP's performance. If the experimental noise is high, the reported performance may be close to the achievable limit, which is a positive result. However, the current presentation is insufficient to make this assessment.
- **Resolution test** Provide a detailed description of the replicate analysis, including how replicates were defined, the distribution of replicate correlations, and a comparison of NPBIP performance relative to the replicate noise floor for individual proteins.

### **Minor Comments**

- **Concern ID** R1-m1
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Section 2.4 (NucProNet description)
- **Evidence pointer** Section 2.4
- **Issue** The description of the deep-learning architecture assumes familiarity with terms like "dilated Conv1D blocks," "gated pooling," and "gated, low-rank cosine bilinear head." While these are standard in the machine learning community, the target audience of Bioinformatics includes many experimental biologists who may not be familiar with these concepts.
- **Required correction** Provide brief explanations of these architectural components in plain language, or add a supplementary figure illustrating the architecture with annotations.

- **Concern ID** R1-m2
- **Severity** Minor
- **Axis** Technical soundness
- **Affected element** Section 2.1 (Datasets)
- **Evidence pointer** Section 2.1
- **Issue** The authors state that RNAcompete data were downloaded from two sources and combined, totaling 420 experiments over 380 RBPs. It is unclear whether the 176 additional experiments from the Sasse et al. study were generated using the same experimental protocol and normalization as the original Ray et al. data. Differences in experimental conditions could introduce batch effects that affect model training and evaluation.
- **Required correction** Describe the normalization procedures for both data sources and any steps taken to harmonize them. If batch effects are a concern, discuss how they were addressed.

- **Concern ID** R1-m3
- **Severity** Minor
- **Axis** Scientific importance
- **Affected element** Section 3.4 (TF family analysis)
- **Evidence pointer** Section 3.4, Figure 5A
- **Issue** The TF family analysis is informative but only reports mean Pearson correlations per family. It would be useful to know the number of proteins in each family and the variance within families, as small family sizes could lead to unreliable estimates.
- **Required correction** Report the number of proteins per family and the standard deviation or confidence intervals for the mean correlations.

- **Concern ID** R1-m4
- **Severity** Minor
- **Axis** Readability for nonspecialists
- **Affected element** Section 3.2 (RNA-binding prediction results)
- **Evidence pointer** Section 3.2
- **Issue** The comparison between NPBIP and the experimental k-mer upper bound is described as "not statistically different" for RNA, but the practical significance of this finding is not discussed. A difference of 0.046 in mean Pearson correlation (0.414 vs 0.460) may be statistically insignificant but could still represent a meaningful gap in predictive accuracy.
- **Required correction** Discuss the practical implications of the observed differences, including whether the gap between NPBIP and the upper bound is likely to matter for downstream applications.

### **Technical failings that need to be addressed before the case is established**
1. Incomplete description of the deep-learning architecture and training procedure (R1-M2)
2. Insufficient statistical methodology details, particularly regarding multiple testing and the surprising DNA result exceeding the upper bound (R1-M1)
3. Lack of a comprehensive literature review to substantiate the "first method" claim (R1-M3)
4. Inadequate description of the replicate analysis used to establish experimental upper bounds (R1-M4)

### **Assessment against Nature-style criteria**
- **Originality**: The combination of similarity-based and deep-learning approaches for the NewProNewSeq task is a reasonable contribution, but the individual components are not novel. The claim of being "first" requires stronger evidence. Moderate originality.
- **Scientific importance**: The problem is important, and a reliable method for predicting binding preferences of uncharacterized NBPs would be valuable. However, the practical impact depends on the robustness of the reported performance, which is not fully established. Moderate to high importance.
- **Interdisciplinary readership**: The work bridges machine learning and molecular biology, and the interpretability analysis (motif recovery) makes it accessible to a broader biological audience. However, the technical sections may be challenging for nonspecialists. Moderate interdisciplinary appeal.
- **Technical soundness**: The evaluation framework is generally sound, but the missing architectural details, incomplete statistical reporting, and the surprising DNA result relative to the upper bound raise concerns. The technical soundness cannot be fully assessed without the supplementary materials.
- **Readability for nonspecialists**: The manuscript is generally well-written, but the methods section assumes significant machine learning expertise. The results and discussion are accessible. Moderate readability.

### **Recommendation posture**
Supportive if technical concerns are resolved. The core idea is promising, and the reported results are encouraging. However, the missing technical details, incomplete statistical reporting, and the need for a more thorough literature review prevent full endorsement at this stage. The authors should be encouraged to revise and resubmit with the required clarifications and additional analyses.

## Risk / unsupported claims
- The claim that NPBIP is "the first method designed to directly solve the NewProNewSeq problem" is not fully substantiated without a comprehensive literature review.
- The claim that NPBIP achieves performance "statistically superior to an upper bound over DBPs" is surprising and requires careful validation, as it suggests the model captures information beyond the experimental k-mer model.
- The statement that the optimized integration weights were "nearly balanced" and yielded "negligible performance gain" is presented without supporting data or statistical testing.
- The generalizability of NPBIP to other experimental assays (e.g., HTR-SELEX, HT-SELEX) is discussed as a future direction but not tested, so any implied generalizability is unsupported.
- The claim that the interpretability analysis "demonstrates that NPBIP recovers canonical binding motifs" is based on only two examples (RBFOX2 and Gm5454); the aggregate results over all proteins are not reported.